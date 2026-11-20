---
name: meta-ads-audit
description: Read-only audit of a Meta (Facebook/Instagram) ad account through the official meta-ads MCP server. Produces an account report, prioritized recommendations, an AI context pack, technical tasks and a visual HTML report. Use when the user asks to audit, analyze or report on their Meta / Facebook / Instagram ads.
---

# Meta ads audit

## 0. Safety
- READ-ONLY. Never call any meta-ads tool that creates, updates, deletes, pauses or changes budgets, bids or targeting. If the user explicitly asks for a change, state exactly what would change, in which account and by how much, and get explicit confirmation first.
- Do not print access tokens. Keep raw data in the working folder under `data/`. Never send account data to any other service.
- If the meta-ads server is not authenticated, tell the user to run `/mcp`, select meta-ads and choose Authenticate.

### Tool reference (read-only)
Tool names can change; decide by verb. Only call tools whose name reads like `get`, `list`, `read` or `insights`.
- Allowed (examples): `ads_get_ad_accounts`, `ads_get_ad_entities`, `ads_get_field_context`, `ads_get_creatives`, `ads_get_ad_preview`, `ads_get_errors`, `ads_get_async_result`, `ads_get_datasets`, `ads_get_dataset_details`, `ads_get_dataset_quality`, `ads_get_dataset_stats`, `ads_get_customconversions`, `ads_get_ad_account_pages`, `ads_get_ig_accounts`, `ads_insights_*`, `ads_account_get_activity_logs`, `ads_pixel_event_read`, `ads_pixel_parameter_read`, `ads_catalog_list_*`, `ads_catalog_get_*`.
- Never call: anything containing `create`, `update`, `delete`, `activate`, `duplicate`, `boost`, `upload`, `finalize`, `connect`, `disconnect`, `permission_manager`, or experiment create/update tools.
- The server may return a `next_actions` queue. Follow only actions that are read-only and do not require user confirmation; skip and mention anything else.

## 1. Setup
1. List the ad accounts the MCP can access. If more than one, ask which (show name and currency).
2. Period: last 30 days vs the previous 30 days unless the user says otherwise. Use the account's time zone.
3. Goal: infer from campaign objectives (sales, leads, traffic, engagement, awareness). You may ask one question: "Do you have a target cost per result or ROAS?" Otherwise compare against the account's own average.
4. Write all outputs in the language the user is writing in. Format numbers for that language and use the account currency.

## 2. Data
Discover the available tools and fetch, for both periods. Save every response as JSON under `data/<account>/<date>/`.
- Account: name, currency, time zone, status, spend cap.
- Structure: campaigns, ad sets, ads with status, objective, budget type and amount, bid strategy, optimization goal.
- Insights at campaign, ad set and ad level: spend, impressions, reach, frequency, link clicks, link CTR, CPC, CPM, results, cost per result, purchase value and ROAS when available.
- Breakdowns: age, gender, platform and placement, device.
- Daily time series: spend, results, CTR, CPM.
- Creatives of the top 5 and bottom 5 ads: format, primary text, headline.
- Tracking: dataset/pixel status, event quality and diagnostics when the tools allow.

If something is unavailable, record it as a data gap; never estimate. Do every calculation in code (Python or Node), not in your head, and save intermediate tables as CSV.

## 3. Rules
These thresholds are generic starting points, not industry facts. Always compare with the account's own baseline and label them as heuristics in the report.
1. Creative fatigue: frequency > 3 and link CTR down > 20% vs previous period → refresh creatives.
2. Weak hook: link CTR < 0.8% with meaningful spend → test the first 3 seconds, visual and headline.
3. CPM spike: CPM up > 30% → audience saturation, competition or seasonality.
4. Budget waste: ad sets with cost per result > 1.5× the account median taking > 20% of spend → shift budget.
5. Winners: ads with cost per result < 0.7× the median → scale gradually (max +20% budget every 3 days).
6. Learning issues: ad sets with < 50 optimization events in 7 days → consolidate or optimize for a higher-volume event.
7. Fragmentation: many small-budget ad sets with overlapping audiences → simplify the structure.
8. Segment outliers: an age, gender or placement segment with 2× average cost per result taking > 15% of spend → exclude or test separately.
9. Tracking: conversion objective without purchase/lead events, low event quality, or browser and server events not deduplicated → technical task.
10. Hygiene: missing UTM parameters, inconsistent naming, active items with no delivery → technical task.

Every finding includes its number (for example "Link CTR fell from 1.4% to 0.9%"). No number, no finding.

## 4. Outputs
Write to `reports/<account>-<YYYY-MM-DD>/`.

**01-account-report.md:** summary (max 5 bullets), KPI table for both periods with % change (spend, results, cost per result, ROAS, CTR, CPM, frequency, reach), campaigns by spend, top 5 and bottom 5 ads with one-line reasons, meaningful breakdown outliers, trend notes, data coverage and gaps.

**02-recommendations.md:** max 10, ordered by priority. Each: Priority (High/Medium/Low), Finding (with number), Action (concrete step), Expected impact, Effort (Low/Medium/High).

**03-ai-context.md + 03-ai-context.json:** a self-contained context pack (max ~1500 words) to paste into any AI assistant: business goal, period, KPI table, structure summary, top 5 issues, best creatives' copy, open questions. First line: a usage note ("Give this to an AI assistant and ask for new creative ideas or a budget plan.").

**04-technical-tasks.md:** checklist. Each item: Why (which finding), How (steps), Owner (developer/marketing), Priority. Include templates where relevant: Pixel + Conversions API with a shared `event_id` for deduplication (example payload), correct standard events, domain verification and event prioritization, a UTM template (`utm_source=meta&utm_medium=paid_social&utm_campaign={{campaign.name}}&utm_content={{ad.name}}`), a naming convention, Instagram professional account linked to the Page, catalog for e-commerce. Only include items tied to findings unless the user asks for a full checklist.

**report.html:** copy `templates/report.html` from this skill folder, replace the `__REPORT_DATA__` placeholder with the report JSON (same content as 03-ai-context.json plus campaigns, daily series, breakdowns, recommendations and technical tasks), and save it. Do not change the template's design. Tell the user they can open it in any browser.
- The JSON schema is documented in the comment block at the top of the template. Set `meta.lang` to `"tr"` or `"en"` (the interface has a TR/EN switch; any other language falls back to English labels while your text stays as written).
- Do the replacement in code and escape `</` as `<\/` inside the JSON so the script tag cannot break.

## 5. Finish
Give a short summary in chat: top 3 findings, top 3 actions, and the folder path. Do not paste the full tables into chat.

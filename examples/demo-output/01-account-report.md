# Account report: Lumen & Clay Studio (demo)

> **Fictional demo.** The account, campaigns, ads and numbers below are made up to show what meta-ads-audit produces.

**Period:** Oct 21 – Nov 19, 2026 vs Sep 21 – Oct 20, 2026 · **Currency:** USD · **Time zone:** America/Chicago · **Goal:** Online sales of handmade ceramics (purchase objective)

## Summary
- Spend $46,276 (+2.2%) brought 1,524 purchases at $30.36 each (+15.4%).
- The Lookalike campaign takes 21% of spend at $80.18 per purchase, 2.1× the ad-set median ($38.24).
- Creative fatigue in Lookalike: frequency 3.36 and link CTR down from 1.32% to 0.99%.
- Catalog ($18.23) and Retargeting ($17.09) are the winners; both are under 0.7× the median.
- The dataset received 1,585 browser purchase events and 0 server events: Conversions API is not set up.

## KPIs
| Metric | Previous 30 days | Last 30 days | Change |
|---|---:|---:|---:|
| Spend | $45,299 | $46,276 | +2.2% |
| Purchases | 1,722 | 1,524 | -11.5% |
| Cost per purchase | $26.31 | $30.36 | +15.4% |
| ROAS | 2.25× | 1.99× | -11.6% |
| Link CTR | 1.42% | 1.33% | -6.3% |
| CPM | $11.73 | $13.13 | +11.9% |
| Frequency | 2.36 | 2.60 | +10.2% |
| Reach | 1,639,563 | 1,357,962 | -17.2% |

## Campaigns by spend
| Campaign | Status | Spend | Purchases | Cost per purchase | ROAS | Link CTR | Frequency |
|---|---|---:|---:|---:|---:|---:|---:|
| SALES \| Prospecting \| Broad | active | $19,427 | 508 | $38.24 | 1.55× | 1.26% | 2.00 |
| SALES \| Lookalike audiences | active | $9,942 | 124 | $80.18 | 0.68× | 0.99% | 3.36 |
| SALES \| Advantage+ catalog | active | $8,949 | 491 | $18.23 | 3.36× | 1.55% | 1.70 |
| SALES \| Retargeting \| 30d visitors | active | $6,581 | 385 | $17.09 | 3.67× | 1.79% | 3.10 |
| SALES \| Holiday teaser | paused | $1,377 | 16 | $86.06 | 0.65× | 1.11% | 1.50 |

Ad-set median cost per purchase (spend-weighted): **$38.24**.

## Top 5 ads (lowest cost per purchase, min $500 spend)
| Ad | Campaign | Spend | Purchases | Cost per purchase | Link CTR | Why |
|---|---|---:|---:|---:|---:|---|
| RT_Review_Quote | SALES \| Retargeting \| 30d visitors | $3,623 | 251 | $14.44 | 1.92% | Social proof headline; link CTR 1.92% |
| Catalog_DPA_Lifestyle_Frame | SALES \| Advantage+ catalog | $3,572 | 221 | $16.17 | 1.69% | Lifestyle frame lifts CTR to 1.69% |
| Catalog_DPA_Default | SALES \| Advantage+ catalog | $5,377 | 270 | $19.91 | 1.46% | Dynamic catalog; ROAS 3.09× |
| RT_FreeShipping_Reminder | SALES \| Retargeting \| 30d visitors | $2,957 | 134 | $22.07 | 1.64% | Clear offer to warm visitors; 134 purchases |
| UGC_Mug_Unboxing_v2 | SALES \| Prospecting \| Broad | $8,176 | 269 | $30.39 | 1.48% | Best prospecting creative; link CTR 1.48% |

## Bottom 5 ads
| Ad | Campaign | Spend | Purchases | Cost per purchase | Link CTR | Why |
|---|---|---:|---:|---:|---:|---|
| LAL_Studio_Story_30s | SALES \| Lookalike audiences | $1,979 | 16 | $123.69 | 0.63% | Weak hook: link CTR 0.63% on $1,979 spend |
| LAL_Discount_10 | SALES \| Lookalike audiences | $3,313 | 34 | $97.43 | 0.97% | Lookalike fatigue; frequency 3.40 |
| LAL_Gift_Guide | SALES \| Lookalike audiences | $3,338 | 46 | $72.57 | 1.02% | Lookalike fatigue; 46 purchases in 30 days |
| Carousel_Bestsellers | SALES \| Prospecting \| Broad | $4,859 | 102 | $47.64 | 1.14% | Carousel converts below average ($47.64 per purchase) |
| LAL_Glaze_Closeup | SALES \| Lookalike audiences | $1,312 | 28 | $46.87 | 1.52% | Good CTR (1.52%) but the lookalike audience is fatigued |

## Breakdown outliers
- **Audience Network:** 17% of spend at $68.41 per purchase, 2.3× the account average ($30.36).
- Age 18-24 and 65+ convert below average ($50.03 and $50.30) but take only 8% and 5% of spend; no action needed.
- Desktop converts best ($23.43) on 12% of spend.

## Trend notes
- Cost per purchase: first 7 days $31.16 → last 7 days $29.77.
- CPM +12.0% vs the previous period ($11.73 → $13.13); below the 30% spike threshold, keep watching.
- The holiday teaser ran 9 days and was paused; its spend is included in the totals.

## Data coverage and gaps
- Covered: account, 5 campaigns, 7 ad sets, 12 ads; insights at all levels; age, gender, placement and device breakdowns; daily series; dataset event counts.
- Gap: Event match quality was not available through the tools.
- Gap: Video metrics (3-second views, hold rate) were not fetched; the weak-hook finding uses link CTR only.
- Gap: Reach is deduplicated per ad set; the account total is an estimate supplied by the API.

_Thresholds used in this report (frequency > 3, CTR drop > 20%, 1.5× / 0.7× the median, 2× segment cost) are generic heuristics compared with this account's own baseline, not industry facts._

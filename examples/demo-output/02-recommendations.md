# Recommendations: Lumen & Clay Studio (demo)

> **Fictional demo.** The account, campaigns, ads and numbers below are made up to show what meta-ads-audit produces.

Ordered by priority. Every finding is backed by a number from Oct 21 – Nov 19, 2026 vs Sep 21 – Oct 20, 2026.

## 1. Cut and consolidate the Lookalike campaign
- **Priority:** High
- **Finding:** Cost per purchase $80.18 is 2.1× the ad-set median ($38.24) while the campaign takes 21% of spend. Its three ad sets got 11, 7, 10 purchases in the last 7 days (learning needs about 50).
- **Action:** Merge the three lookalike ad sets into one (LAL 1% purchasers), lower its budget by 30% (about $99/day) and move that money to Retargeting and Catalog.
- **Expected impact:** Lower blended cost per purchase; one ad set gets enough conversions to leave the learning phase.
- **Effort:** Low

## 2. Refresh Lookalike creatives
- **Priority:** High
- **Finding:** Frequency 3.36 (previous 2.56) and link CTR fell from 1.32% to 0.99% (-24.5%).
- **Action:** Launch 3 new concepts built on the best hook (glaze close-up and unboxing) and pause the oldest ads.
- **Expected impact:** CTR back toward the previous period level; lower CPM pressure from the same audience.
- **Effort:** Medium

## 3. Set up Conversions API with deduplication
- **Priority:** High
- **Finding:** 1,585 browser purchase events and 0 server events in the last 30 days.
- **Action:** Send Purchase from the server with the same event_id as the pixel (see technical tasks).
- **Expected impact:** More purchases attributed and better optimization signal, especially on iOS and with ad blockers.
- **Effort:** Medium

## 4. Scale Catalog and Retargeting gradually
- **Priority:** Medium
- **Finding:** Catalog $18.23 (ROAS 3.36×) and Retargeting $17.09 (ROAS 3.67×) are below 0.7× the median $38.24.
- **Action:** Raise budgets by max 20% every 3 days while cost per purchase stays under $26.77.
- **Expected impact:** More purchases at the account's best efficiency without resetting learning.
- **Effort:** Low

## 5. Test excluding Audience Network
- **Priority:** Medium
- **Finding:** Audience Network takes 17% of spend at $68.41 per purchase, 2.3× the account average.
- **Action:** Duplicate the Prospecting ad set without Audience Network and compare for 7 days.
- **Expected impact:** Budget moves to placements that convert closer to the average.
- **Effort:** Low

## 6. Rework the first 3 seconds of the studio story video
- **Priority:** Medium
- **Finding:** LAL_Studio_Story_30s has a link CTR of 0.63% on $1,979 spend (account 1.33%).
- **Action:** Open on the finished product, put the offer in the headline and cut the video to 15 seconds.
- **Expected impact:** Higher CTR from the same spend.
- **Effort:** Low

## 7. Add UTM parameters to every ad
- **Priority:** Low
- **Finding:** 7 of 12 ads have no UTM parameters.
- **Action:** Apply the UTM template from the technical tasks to all ads.
- **Expected impact:** Meta results can be checked against your analytics tool.
- **Effort:** Low

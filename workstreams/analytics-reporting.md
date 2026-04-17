---
summary: Campaign performance reporting, funnel analysis, cohort analysis, and attribution tracking.
status: Active
last_updated: 17.04.2026
---

# Analytics & Reporting

## Current Status

Weekly and weekend campaign numbers are tracked and reported. Funnel drop-off analysis is a recurring task across verticals. Cohort analysis is used to evaluate voucher/deal effectiveness. SQL is used directly for voucher and appointment data.

## Regular Reports

- **Weekday campaign numbers** — prepared by Yana
- **Weekend campaign numbers** — prepared by Yana
- **Healthcare Report** — completed 14.04.2026
- **KSA Campaign Performance Report** — in progress [OPEN]
- **LTV Report** — completed

## Analytics Stack

- **SQL** — appointment and voucher data queries (backend)
- **Adjust** — attribution and deep link tracking
- **CleverTap** — CRM and funnel drop-off data (via BD)
- **Google Analytics** — web and app sessions, conversion rates
- Event tracking: `jl_page_view`, `mobile_page_view`, `mobile_category_clicked`

## Funnel Observations

- Lab Test: Sessions increased Sunday but Funnel CR% decreased — drop-off point TBD (March 2024)
- IV Therapy: Sessions decreased, Funnel CR% also decreased (March 2024)
- App visitors: Sessions up but CR% down (Sep 2024) — trend-driven, not campaign issue
- Web visitors: Sessions up but conversions down (Sep 2024)
- Voucher usage for App Banners, Meta, Google decreased — sign of organic trend decrease (Sep 2024)

## Cohort Analysis Highlights

- HC10 users: 25% booked in month 2 vs 23% for AED 50 Off users
- AED 50 Off: Meta CPA rose from $96.25 to $212.00 — scaled back
- Voucher usage dropped from 198 to 98 with AED 50 Off deal
- Discount-to-GMV decreased 5.68%, PC1 increased 3.13% (HC10 period)

## Open Items

| Item | Owner | Status |
|---|---|---|
| KSA Campaign Performance Report | Yana | Open |
| KSA Conversion Lift Results | Yana | Open |
| Complete Analysis on all KSA campaigns | Yana | Open |
| Pet Healthcare Funnel Drop Off analysis | Yana | Open |
| BD CleverTap Drop Off Data | Yana | Open |

## Backlinks

- [[workstreams/paid-media]] — Campaign data source
- [[workstreams/healthcare-vertical]] — Funnel analysis for HC verticals
- [[workstreams/ksa-expansion]] — KSA reporting
- [[experiments/hc10-vs-aed50-discount]] — Cohort analysis source

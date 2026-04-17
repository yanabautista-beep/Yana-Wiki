---
summary: KPI definitions and benchmarks for Justlife digital marketing.
status: Active
last_updated: 17.04.2026
---

# Metric Definitions

## CPA (Cost Per Acquisition)

**Definition:** Total ad spend divided by number of confirmed bookings/acquisitions, per channel and vertical.

**Current benchmark:** HC Home Cleaning Meta CPA: $96.25 (HC10 deal). Increased to $212.00 under AED 50 Off deal — reverted.

**How it's calculated:** Total spend ÷ confirmed appointments attributed to paid channel.

---

## ROAS (Return on Ad Spend)

**Definition:** Revenue generated from ads divided by total ad spend.

**Current benchmark:** TBD — not explicitly stated in source.

**How it's calculated:** Revenue attributed to paid ÷ total spend.

---

## PC1 (Profit Contribution 1)

**Definition:** First-order profitability metric used at Justlife to evaluate deal economics. Negative PC1 is acceptable when offset by lower CPAs and strong month-2 retention.

**Current benchmark:** HC10 = negative PC1. AED 50 Off = +3.13% PC1 improvement. HC10 chosen despite negative PC1 due to lower CPA.

**How it's calculated:** Internal calculation — refer to finance team.

---

## Month-2 Booking Rate (Cohort Retention)

**Definition:** Percentage of customers acquired in a given month who made a booking in the following month. Used to assess deal quality and LTV trajectory.

**Current benchmark:** HC10 cohort: 25%. AED 50 Off cohort: 23%.

**How it's calculated:** Cohort analysis on appointment data from SQL.

---

## Voucher Usage

**Definition:** Number of bookings completed using a specific voucher code in a given period. Used to measure deal traction and scale potential.

**Current benchmark:** Weekend voucher usage dropped from 198 to 98 with AED 50 Off deal — signal to revert.

**How it's calculated:** SQL query on appointment table, filter by voucher code and status (0, 1, 5).

---

## Discount-to-GMV

**Definition:** Total discount value as a percentage of Gross Merchandise Value. Measures how much discount is being given relative to revenue.

**Current benchmark:** Decreased 5.68% during HC10 period (improvement — less discount relative to GMV).

**How it's calculated:** Total discount ÷ Total GMV × 100.

---

## CTR (Click Through Rate)

**Definition:** Percentage of ad impressions that result in a click.

**Current benchmark:** Not explicitly stated in source — track per campaign.

**How it's calculated:** Clicks ÷ Impressions × 100.

---

## App Conversion Rate

**Definition:** Percentage of app sessions that result in a completed booking.

**Current benchmark:** Decreased Sep 2024 despite increased app budgets — attributed to organic trend, not campaign issue.

**How it's calculated:** Completed bookings ÷ App sessions × 100.

---

## Funnel CR% (Funnel Conversion Rate)

**Definition:** Percentage of users who enter the booking funnel and complete a booking. Tracked per vertical (Lab Tests, IV Therapy, etc.) and per user type (visitor, retained).

**Current benchmark:** Decreased for IV Therapy and Lab Tests (March 2024) — drop-off point analysis ongoing.

**How it's calculated:** Completed bookings ÷ Funnel entries × 100, segmented by vertical and user type.

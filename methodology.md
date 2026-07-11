# Methodology — South Africa E-Commerce Import Trends v1.0 (2026)

## 1. Data source

All figures derive from the **South African Revenue Service (SARS) Trade
Statistics** detailed import data, downloaded from
https://tools.sars.gov.za/tradestatsportal/data_download.aspx:

- Trade type: **Imports** only.
- Granularity: tariff line (8-digit HS code) × country of origin × month.
- Measure: **customs value in South African rand (ZAR)** — the value declared for
  customs purposes. Nominal values; no inflation adjustment.
- Period: January 2021 – December 2025 (full years), plus available 2026 months
  (partial, flagged, and excluded from all growth and index calculations).
- Chapters downloaded: 33, 61, 62, 64, 84, 85, 95 (84 is needed solely for
  heading 8471; the basket then filters to the exact scope below).

UN Comtrade (DESA/UNSD) is **not used in v1.0**; an international-comparison
chart is planned for a future update.

## 2. The e-commerce basket — exact definition

Five consumer-goods categories most associated with online retail:

| Category | HS scope (exact) |
|---|---|
| Apparel & clothing | **Chapters 61 + 62**, all tariff lines |
| Consumer electronics | **Headings 8471, 8517, 8518, 8519, 8521, 8528 only** (see below) |
| Beauty, cosmetics & fragrance | **Headings 3303, 3304, 3305, 3306, 3307 only** (see below) |
| Footwear | **Chapter 64**, all tariff lines |
| Toys, games & sporting goods | **Chapter 95**, all tariff lines |

A tariff line belongs to a category if its HS code starts with one of the listed
chapter (2-digit) or heading (4-digit) prefixes. The basket total is the sum of
the five categories; no line is counted twice (the scopes do not overlap).

### Beauty, cosmetics & fragrance — headings included and why not all of chapter 33

| Heading | Covers |
|---|---|
| 3303 | Perfumes and toilet waters |
| 3304 | Make-up and skincare preparations (incl. sunscreen, manicure/pedicure) |
| 3305 | Haircare preparations |
| 3306 | Oral and dental hygiene preparations |
| 3307 | Shaving preparations, deodorants, bath preparations |

HS Chapter 33 bundles consumer cosmetics with **beverage syrup concentrates** —
SARS itself labels the chapter "Cosmetics, Toiletries and Beverage Syrup". The
excluded headings are 3301 (essential oils — largely industrial inputs) and
3302 (odoriferous mixtures and flavour concentrates for the food and beverage
industry). Heading 3302 alone accounted for roughly half of chapter 33's import
value in 2025 (≈R11bn), dominated by beverage-flavour concentrate — including
large volumes from a regional concentrate-manufacturing hub — none of which is
a consumer beauty product. Restricting the category to consumer headings
3303–3307 removes that distortion; like the electronics definition, this makes
the category **conservative**.

### Consumer electronics — headings included

| Heading | Covers |
|---|---|
| 8471 | Computers, laptops, tablets and other automatic data-processing machines |
| 8517 | Smartphones and other telephones; network/communication apparatus |
| 8518 | Headphones, earphones, microphones, loudspeakers, audio amplifiers |
| 8519 | Sound recording / reproducing apparatus |
| 8521 | Video recording / reproducing apparatus |
| 8528 | Monitors, projectors and television receivers |

Note: **8471 sits in HS Chapter 84**, not 85 — the category therefore spans
Chapters 84 + 85. (The common shorthand "electronics = Chapter 85" would miss
every computer and laptop.)

### Consumer electronics — deliberately excluded

To keep the category defensible, headings with heavily mixed consumer/industrial
or B2B content are excluded, notably: 8504 (power supplies/chargers — largely
industrial transformers), 8523 (storage media — includes commercial software and
smart-card volumes), 8525 (cameras — includes broadcast equipment), 8507
(batteries — dominated by automotive/industrial cells) and 8544 (cables). This
makes the electronics figure **conservative**: it understates rather than
overstates consumer electronics.

## 3. Calculations

All computations are sums and ratios over SARS rows — nothing is estimated,
imputed or modelled.

- **Annual category value** = sum of customs value across the category's tariff
  lines, all origins, all 12 months.
- **Year-on-year growth %** = (value_year ÷ value_previous_year − 1) × 100.
- **CAGR 2021–2025** = ((value_2025 ÷ value_2021)^(1/4) − 1) × 100. This is the
  compound annual rate across the five-year window 2021–2025, i.e. four
  compounding steps.
- **SA E-Commerce Import Basket Index** = (basket value_year ÷ basket value_2021)
  × 100, so 2021 = 100. Full years only.
- **Top source countries** = origins ranked by customs value within a category
  for the latest full year (2025). Non-country origin codes (Unclassified,
  Unknown, Ship/Aircraft, "Gold, Petroleum and Other") are excluded from the
  ranking but retained in category totals so totals reconcile with SARS.
- **Monthly seasonality** = each month's share of that year's category value,
  averaged across 2021–2025. An even spread would be 100/12 = 8.33% per month;
  the peak month is the one with the highest average share.

## 4. Limitations — read before citing

1. **This is not a measure of online sales.** Customs data records goods crossing
   the border, not the sales channel. Wholesale, retail and B2C shipments in
   these categories are indistinguishable. The basket is a transparent proxy:
   "consumer-goods import categories associated with e-commerce".
2. **Customs value ≠ retail value.** Figures are declared customs values,
   excluding duties, VAT, freight mark-ups and retail margins.
3. **Low-value consignment coverage.** Small parcels under de minimis-style
   simplified clearance may be recorded differently from full declarations, so
   direct-to-consumer parcel flows can be under-captured.
4. **Country of origin ≠ country of purchase.** Goods bought on an international
   platform may be recorded against the manufacturing origin.
5. **Nominal rand values.** Growth reflects both volume and price/exchange-rate
   effects; no deflator is applied.
6. **2026 is partial** and excluded from growth rates and the index.
7. **Tariff structure changes** (reclassified lines) can shift small amounts
   between headings across years.

## 5. Reproducibility

The full pipeline (validation, processing, report build) is deterministic Python
(pandas) run over the SARS download; the scripts define the basket in one shared
module so definitions cannot drift. Contact info@jlog.co.za for the pipeline.

---
JetLog (Pty) Ltd, trading as JLog · Unit 12C, 10 Railway Street, Woodstock,
Cape Town · info@jlog.co.za · +27 21 300 6099.
Analysis layer licensed CC BY 4.0; underlying figures © SARS.

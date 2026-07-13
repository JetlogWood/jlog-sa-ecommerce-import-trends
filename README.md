# South Africa E-Commerce Import Trends — open dataset (v1.0, 2026)

**Full report:** https://jlog.co.za/research/sa-ecommerce-import-trends/  
**DOI:** https://doi.org/10.5281/zenodo.21333712  
**Kaggle dataset:** https://www.kaggle.com/datasets/gerritdyman/south-africa-e-commerce-import-trends

## What this is

Aggregated figures on South Africa's imports in the five consumer-goods categories
most associated with online retail — apparel, consumer electronics, beauty and
cosmetics, footwear, and toys, games and sporting goods — derived from official
South African Revenue Service (SARS) Trade Statistics, 2021–2025.

**What this is NOT:** a measure of online sales. Customs data records goods
crossing the border, not the sales channel, so it cannot separate B2C e-commerce
from wholesale imports. This dataset is a transparent proxy: "consumer-goods
import categories associated with e-commerce". Full detail in `methodology.md`.

It is also NOT a copy of the SARS database — only aggregated, derived figures are
published here. For the underlying detailed records, use the SARS Trade Statistics
portal directly.

## Files and columns

All rand values are **customs value in ZAR** (nominal — not inflation-adjusted).
Every file carries a `source` column crediting SARS.

### sa-ecommerce-import-trends-category-annual.csv
One row per category per year.
| Column | Meaning |
|---|---|
| category | machine key: apparel, consumer_electronics, beauty, footwear, toys_games_sport, basket_total |
| category_label | plain-English category name |
| year | calendar year |
| import_value_zar | total customs value of imports, ZAR |
| is_partial_year | True where the year is incomplete (2026) — treat with care |
| yoy_growth_pct | growth vs the previous year, % (blank for 2021 and partial years) |
| source | data source credit |

### sa-ecommerce-import-trends-category-monthly.csv
One row per category per month: `category, category_label, year, month (1–12),
import_value_zar, source`.

### sa-ecommerce-import-trends-basket-index.csv
The SA E-Commerce Import Basket Index: `year, basket_value_zar,
index_2021_100 (2021 = 100), source`.

### sa-ecommerce-import-trends-top-source-countries.csv
Top 5 source countries per category, latest full year: `category, category_label,
year, rank (1–5), country, import_value_zar, share_of_category_pct, source`.
Non-country origin codes in the SARS data (Unclassified, Unknown, Ship/Aircraft,
"Gold, Petroleum and Other") are excluded from rankings but kept in totals.

### sa-ecommerce-import-trends-monthly-seasonality.csv
Average share of a year's import value landing in each calendar month (mean over
2021–2025): `category, category_label, month (1–12), share_of_year_pct,
is_peak_month, source`. An even spread would be 8.33% per month.

### sa-ecommerce-import-trends-category-summary.csv
One row per category: `category, category_label, latest_full_year,
import_value_zar, yoy_growth_pct, cagr_2021_2025_pct, top_source_country,
top_source_share_pct, source`.

## Sources

- **South African Revenue Service (SARS), Trade Statistics** —
  https://tools.sars.gov.za/tradestatsportal/data_download.aspx (primary; all figures)
- United Nations Comtrade is planned for a future international-comparison update
  and is **not used in v1.0**.

## How to cite

> JLog (JetLog (Pty) Ltd). "South Africa E-Commerce Import Trends", version 1.0, 2026.
> Derived from SARS Trade Statistics. Licensed CC BY 4.0.
> https://jlog.co.za/research/sa-ecommerce-import-trends/
> doi:10.5281/zenodo.21333712 · https://doi.org/10.5281/zenodo.21333712

## Licence

JLog's analysis layer (category definitions, derived figures, index, documentation)
is licensed **CC BY 4.0** — see `LICENSE`. Underlying trade figures are
© South African Revenue Service (SARS) and must be attributed to SARS.

## Contact

JetLog (Pty) Ltd, Unit 12C, 10 Railway Street, Woodstock, Cape Town ·
info@jlog.co.za · +27 21 300 6099

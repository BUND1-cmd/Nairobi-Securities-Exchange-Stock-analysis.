# Data dictionary

## 1. Sources
Original Mendeley file names: see the list above. The 2024 file was saved with a .xlsx ending by Windows; the content is CSV.
2020: NSE_data_all_stocks_2020.csv
2021: NSE_data_all_stocks_2021_upto_31dec2021.csv
2022: NSE_data_all_stocks_2022.csv
2023: NSE_data_all_stocks_2023.csv
2024: NSE_data_all_stocks_2024_csv.xlsx (content is CSV)

| File | Period | Source | DOI / URL | Version | Downloaded | Licence | Notes |

|---|---|---|---|---|---|---|---|

| data/raw/NSE_2020.csv | 2 Jan to 31 Dec 2020 | [MENDELEY DATA] | [10.17632/73rb78pmzw.2] | [2] | [16TH NOV 2026] | [CC BY 4.0] | Full year 2 Jan to 31 Dec 2020 (checked). Dataset description says 2020 runs to 30 June only. Adjust column all '-' (unadjusted).|

| data/raw/NSE_2021.csv | 2 jan to 31 dec 2021 | [MENDELEY DATA] | [10.17632/97hkwn5y3x.4] |
[4] | [16TH NOV 2026] | [CC BY 4.0] | Full year 2021. Downloaded version 4; version 5 is the latest on the dataset page. Check which version contains the data you use.|

| data/raw/NSE_2022.csv | 2 Jan to 31 Dec 2022 | [MENDELEY DATA] | [10.17632/jmcdmnyh2s.2] | [2] | [16TH NOV 2026] | [CC BY 4.0] | Full year 2022. Downloaded version 2 (latest; version 1 also listed).|

| data/raw/NSE_2023.csv | 2 Jan to 31 Dec 2023 | [MENDELEY DATA] | [10.17632/ss5pfw8xnk.3] | [3] | [16TH NOV 2026] | [CC BY 4.0] | Full year FROM jan to dec 3 versions available|

| data/raw/NSE_2024.csv | 2 Jan to 31 Dec 2024 | [MENDELEY DATA] | [10.17632/ss5pfw8xnk.3] | [3] | [16TH NOV 2026] | [CC BY 4.0] | Full year FROM jan to dec 3 versions available|

## 2. Columns (raw files)

Standard names are used in the cleaning script. Raw names differ by year: 2020 and 2021 files use the first set, 2022 to 2024 use the second.

| Standard name | Raw name (2020-21 / 2022-24) | Meaning | Unit | Example (2020 file) |
|---|---|---|---|---|
| date | DATE / Date | Trading date of the price record | Text, dd-Mon-yy (2024 has one-digit days, e.g. 2-Jan-24) | 02-Jan-20 |
| code | CODE / Code | NSE ticker symbol | Text | EGAD |
| name | NAME / Name | Company name | Text | Eaagads Ltd |
| low_12m | 12m Low | Lowest traded price in the previous 12 months | KES per share | 8.2 |
| high_12m | 12m High | Highest traded price in the previous 12 months | KES per share | 14 |
| day_low | Day Low | Lowest price traded on the day | KES per share | 10.1 |
| day_high | Day High | Highest price traded on the day | KES per share | 10.1 |
| day_price | Day Price | Price recorded for the day (confirm in the source whether this is the closing price) | KES per share | 10.1 |
| previous | Previous | Price from the previous trading day | KES per share | 10.1 |
| change | Change | Day Price minus Previous; "-" when there was no trade | KES per share | - |
| change_pct | Change% | Percentage change; text with a % sign in the CSV, e.g. -8.24% | Percent | - |
| volume | Volume | Shares traded on the day; "-" when there was no trade; thousand separators inside quotes, e.g. "3,200" | Number of shares | - |
| adjust | Adjust (2020-21) / Adjusted Price (2022-24) | Price adjusted for corporate actions. "-" in every row checked so far, so no adjusted price is supplied | KES per share | - |

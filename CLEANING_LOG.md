## Raw row counts (before cleaning)

| File | Lines in file | Data rows (lines minus header) |
|---|---|---|
| NSE_2020.csv | 17,893 | 17,892 |
| NSE_2021.csv | 17,747 | 17,746 |
| NSE_2022.csv | 16,807 | 16,806 |
| NSE_2023.csv | 17,275 | 17,274 |
| NSE_2024.csv | 18,120 | 18,119 |

## Structure checks (raw files)

- All five files: header of 13 fields, every data row 13 fields when quotes are respected.
- Header names differ between years: 2020 and 2021 use `DATE`, `CODE`, `Adjust`; 2022 to 2024 use `Date`, `Code`, `Adjusted Price`. Renamed in the cleaning script.
- Date format is text `dd-Mon-yy` in all files. 2024 has one-digit days (for example `2-Jan-24`), which the parser must accept.
- 2021 file starts with a UTF-8 byte-order mark; read with `encoding='utf-8-sig'`.
- Numbers with thousands separators appear inside quotes, for example `"3,200"`; read with `thousands=','`.

## Adjusted price column

- 2021 file: 6 rows with a value, all IMH (03 to 10 May 2021). Each adjusted value equals Day Price divided by 2. No corresponding break appears in Day Price. Status: unexplained, pending check against NSE announcements.
- 2022 file: 59 rows with a value, all CGEN (03 Jan to 24 Mar 2022). Same pattern. CGEN is not a bank, so it's outside the study universe.
- 2020, 2023, 2024 files: no values.
- Decision: the adjust column isn't used in return calculations until the IMH rows are verified.

## IMH bonus issue (1:1, 2021)

- Book closure 10 May 2021; shares credited 21 May 2021 (I&M published notice, March 2021).
- Raw Day Price falls from 42.60 (10 May) to 24.85 (11 May), a -17.75 change. This is the ex-bonus break, not a trading loss.
- Adjustment: divide all IMH Day Price, Previous, Day High, Day Low, 12m High and 12m Low rows dated before 11 May 2021 by 2. Multiply Volume by 2 for the same rows.
- The raw Adjust column is populated only for 3 to 10 May 2021 and is not used. The script recomputes the adjustment from the bonus date.
- Adjusted 11 May return: about +16.7%, not -58%.
- Dividend: KES 2.25, ex-date 16 April 2021. Price-only returns do not adjust for it. Decision on price vs total return deferred to Stage 4.

## IMH spike, 21 to 30 August 2024

- 21 Aug 2024: price 20.60 to 34.25 (+66%), volume 4,619,200 (about 200 times the normal level).
- 22 to 27 Aug 2024: four consecutive falls of about -9.9% each, then 28 to 30 Aug back to about 21 to 22.
- Status: unexplained. Looks like a one-off large trade or data error, not a change in value.
- Decision: rows kept in the clean data and flagged with `spike_flag = True` for 21 to 30 Aug 2024. Excluded from return statistics in the main analysis. Tested with and without in the Stage 5 robustness check.
- Check still open: search NSE and I&M announcements for August 2024. If none found, the status stays unexplained.
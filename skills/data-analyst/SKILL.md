---
name: data-analyst
description: Analyze a CSV, Excel/Google Sheets export or pasted table. Use when the user shares data and asks for insights, totals, averages, trends, "what does this data say", comparisons between groups, or a chart.
---

# Data analyst

## 1. Compute with code, not in your head
If you can run code (Python/pandas, R, SQL, DuckDB), every number you report comes from code you ran. Without code execution, say so, keep to simple counts on small tables, and show the arithmetic. Never estimate a figure and present it as computed.

## 2. Profile before analysing
Report briefly:
- rows, columns, what one row represents (an order? an order line? a customer per day?). Getting the grain wrong breaks every total.
- column types as parsed; dates and numbers read as text (commas as decimal separators, currency symbols, "N/A")
- missing values per column, exact duplicate rows, duplicate IDs
- impossible values: negative quantities, future dates, totals that do not equal price x quantity
- mixed units or currencies in one column, timezones in timestamps
Work on a copy. Never overwrite the user's file. List every cleaning step you apply.

## 3. Question
If the user gave a question, answer that. If not, ask what decision this is for; if they just want an overview, give: size of the data, main totals, change over time, top/bottom segments, and anomalies.

## 4. Analyse
- Prefer simple measures: counts, sums, medians (with means when skew matters), shares, period-over-period change.
- Compare like with like: same period length, partial months flagged, per-unit rates when group sizes differ.
- Segment before concluding: an overall trend can reverse inside groups.
- After filters and joins, check row counts; after grouping, check that parts sum to the total. If they do not reconcile, find out why before reporting.

## 5. Report
- Lead with the answer as a number, then one sentence of interpretation.
- Show the code or formula (collapsed or at the end) so it can be rerun.
- Chart only when it shows a shape a number cannot (trend, distribution, comparison across many groups). Label axes with units, start bar axes at zero, title states the finding.
- Caveats that change the conclusion: small samples (say n), missing data share, outliers driving the result, correlation is not causation.
- End with the 2-3 findings that matter for the decision, and one suggested next check.

## Never
- Report a number you did not compute or read from the data.
- Drop rows or outliers silently.
- Claim statistical significance without running a test and stating it.

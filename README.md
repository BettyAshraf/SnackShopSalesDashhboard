# Snack Shop Sales Dashboard

An interactive Power BI dashboard that answers a shop owner's core questions about sales without digging through a spreadsheet. Built as a practice project during my Data Analytics training.

![Snack Shop Sales Dashboard](Screenshot%202026-11-16%20022258.png)

> **Dataset scope:** 7 transaction rows covering 1–4 January 2026. This is a small training dataset, so the findings describe only these records and are not evidence of long-term business performance.

## Business Questions

1. How much revenue came in?
2. How many items were sold?
3. Which product earned the most?
4. Do drinks or snacks perform better?
5. What sold, and in what quantities?

## Dashboard Features

- KPI cards: Total Sales and Total Quantity
- Revenue by product (bar chart)
- Revenue share by category (pie chart)
- Quantity sold by product (bar chart)
- Detail table by date and product
- Category and Product slicers with a **Reset Filters** button
- Consistent red color theme

## Key Results

| KPI | Result |
|---|---:|
| Total Sales Revenue | $5,621 |
| Total Quantity Sold | 297 units |
| Products | 6 |
| Transaction Rows | 7 |
| Date Coverage | 1–4 January 2026 |

- **Juice** was the top product: **$2,461** revenue and **107 units**.
- **Drinks** generated **$3,621 (64.4%)** of revenue; **Snacks** generated **$2,000 (35.6%)**.

Full interpretation: [Business_Insights_and_Recommendations.md](Business_Insights_and_Recommendations.md)

## Data Preparation

Issues found and fixed while building the report:

- The Total Quantity card showed "$297" because of a currency format I had missed; it now shows a plain number.
- Some chart titles did not match what the chart actually showed; I corrected them.
- A duplicate column was hiding in the data; I removed it.
- The source workbook had non-breaking spaces in some headers and text cells, and `Unit Price` was stored as text in some rows; I converted it to a numeric type.

Details and formulas: [Data_Cleaning_and_Calculated_Columns.md](Data_Cleaning_and_Calculated_Columns.md)

`Total Sales = Quantity × Unit Price`

## Tools

- Microsoft Excel: source data review
- Power BI: data model, DAX, and dashboard

## Files

| File | Description |
|---|---|
| `SnackShopDashboard.pbix` | Power BI dashboard |
| `1- Project1_SnackShopSales.xlsx` | Source data |
| `Business_Insights_and_Recommendations.md` | Findings and recommendations |
| `Data_Cleaning_and_Calculated_Columns.md` | Cleaning steps and calculated columns |

## Limitations

- Only 7 rows over 4 days.
- No cost, expense, or inventory fields, so profit and margin cannot be calculated. Revenue is not profit.

## What I'd Add Next

- More transactions to show trends over time
- Cost data for a profit view
- Stock data to separate low demand from stockouts

# Snack Shop Sales Analysis

## Project Overview
This project analyzes a small snack shop sales dataset to summarize sales revenue, units sold, product performance, and category contribution. The results are presented in an interactive sales dashboard.

> **Dataset scope:** The supplied workbook contains 7 transaction rows covering 1–4 January 2026. It is a small training/sample dataset, so the findings describe only these records and should not be treated as evidence of long-term business performance.

## Business Questions
- What is the total sales revenue?
- How many units were sold?
- Which product generated the highest revenue?
- Which product sold the highest quantity?
- Which category contributed more to revenue?

## Dataset
**Source file:** `1- Project1_SnackShopSales.xlsx`  
**Worksheet:** `SnackShopSales`

| Column | Description |
|---|---|
| Date | Transaction date |
| Product | Product name |
| Category | Product category (Drinks or Snacks) |
| Quantity | Number of units sold |
| Unit Price | Selling price per unit |

A calculated `Total Sales` field is used for revenue analysis:

`Total Sales = Quantity × Unit Price`

## Tools
- Microsoft Excel — source data review and preparation
- Power BI — dashboard and visual analysis *(include the PBIX file if the dashboard was built in Power BI)*

## Key Performance Indicators
| KPI | Result |
|---|---:|
| Total Sales Revenue | $5,621 |
| Total Quantity Sold | 297 units |
| Number of Products | 6 |
| Number of Transaction Rows | 7 |
| Date Coverage | 1–4 January 2026 |


## Main Findings
- **Juice** generated the highest revenue: **$2,461**.
- **Juice** also had the highest quantity sold: **107 units**.
- **Drinks** generated **$3,621** (approximately **64.4%**) of total revenue.
- **Snacks** generated **$2,000** (approximately **35.6%**) of total revenue.

See [`Business_Insights_and_Recommendations.md`](Business_Insights_and_Recommendations.md) for the detailed interpretation and recommendations.

## Data Preparation
The source workbook contains non-breaking spaces in some headers and text/numeric cells. These should be normalized before analysis, and the `Unit Price` field should be converted to a numeric data type. The preparation checks and calculated-field formulas are documented in [`Data_Cleaning_and_Calculated_Columns.md`](Data_Cleaning_and_Calculated_Columns.md).

## Repository Structure
```text
Snack-Shop-Sales-Analysis/
├── Dataset/
│   └── SnackShopSales.xlsx
├── Dashboard/
│   └── SnackShopSales.pbix          # Add if your dashboard is a Power BI file
├── Images/
│   └── Dashboard.png
├── README.md
├── Business_Insights_and_Recommendations.md
└── Data_Cleaning_and_Calculated_Columns.md
```

## Important Limitations
- The dataset has only 7 rows and covers 4 days.
- There is no cost, expense, inventory, or profit field. Therefore, profit, profit margin, and product profitability cannot be calculated from the supplied data.
- The dashboard screenshot should be checked to ensure that slicers filter all intended visuals consistently.



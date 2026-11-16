# Data Cleaning & Calculated Columns Documentation

## 1. Source Data
- **File:** `1- Project1_SnackShopSales.xlsx`
- **Worksheet:** `SnackShopSales`
- **Original fields:** `Date`, `Product`, `Category`, `Quantity`, `Unit Price`
- **Source size:** 7 data rows and 5 columns

The documentation below distinguishes issues observed in the supplied workbook from recommended preparation actions. It does not claim that an unprovided Power Query or PBIX file was inspected.

## 2. Data Quality Checks

### Issue 1 — Extra whitespace / non-breaking spaces
The supplied workbook contains non-breaking spaces (`CHAR(160)`) at the end of some column headers and text values. Ordinary `TRIM` does not always remove non-breaking spaces.

**Recommended cleaning:**
- Replace non-breaking spaces with regular spaces.
- Remove leading/trailing spaces.
- Apply consistently to headers and text fields such as `Product` and `Category`.

**Excel example:**
```excel
=TRIM(CLEAN(SUBSTITUTE(A2,CHAR(160)," ")))
```
Use the equivalent source column reference for each text field.

### Issue 2 — Unit Price stored as text in some rows
In the source workbook, some `Unit Price` values include a trailing non-breaking space and are stored as text rather than numeric values.

**Recommended cleaning:**
- Replace `CHAR(160)` with an empty string (or a regular space, then trim).
- Convert the cleaned result to a number.
- Confirm that all unit prices have a numeric data type.

**Excel example:**
```excel
=VALUE(TRIM(SUBSTITUTE(E2,CHAR(160),"")))
```

### Issue 3 — Date data type
The source workbook displays dates as text strings (for example, `1-Jan-2026`) rather than native Excel date values.

**Recommended cleaning:**
- Convert `Date` to a real Date data type.
- Verify that all dates fall within the expected sample period: 1–4 January 2026.

**Excel example (if the text is recognized by the Excel locale):**
```excel
=DATEVALUE(TRIM(SUBSTITUTE(A2,CHAR(160),"")))
```
Then format the result as a date.

### Issue 4 — Numeric validation
Confirm that `Quantity` and cleaned `Unit Price` contain numeric values, no blanks, and no unexpected negative values. The supplied records contain positive quantities and prices.

## 3. Calculated Columns

### A. Total Sales
**Purpose:** Calculate revenue for each product transaction row.

**Business logic:**
```text
Total Sales = Quantity × Unit Price
```

**Excel Table formula:**
```excel
=[@Quantity]*[@[Unit Price]]
```

**Power BI DAX calculated column:**
```DAX
Total Sales = 'SnackShopSales'[Quantity] * 'SnackShopSales'[Unit Price]
```

### B. Month (optional)
**Purpose:** Support month-level grouping if the dataset is expanded to cover multiple months.

**Excel formula (when Date is a valid date):**
```excel
=TEXT([@Date],"mmmm")
```

**Power BI DAX calculated column:**
```DAX
Month = FORMAT('SnackShopSales'[Date], "MMMM")
```

For the current sample, every record belongs to January 2026, so Month adds little analytical value until more dates are added.

## 4. Validation & Reconciliation
After cleaning and calculating `Total Sales`, the supplied records should reconcile to the following totals:

| Product | Quantity | Total Sales |
|---|---:|---:|
| Biscuits | 40 | $520 |
| Chips | 50 | $1,000 |
| Chocolate | 20 | $480 |
| Juice | 107 | $2,461 |
| Soda | 20 | $500 |
| Water | 60 | $660 |
| **Grand Total** | **297** | **$5,621** |

Category reconciliation:

| Category | Quantity | Total Sales |
|---|---:|---:|
| Drinks | 197 | $3,621 |
| Snacks | 100 | $2,000 |
| **Grand Total** | **297** | **$5,621** |

The calculated revenue is based on the provided quantities and unit prices. It is not profit.

## 5. Data Model & Dashboard Checks
Before publishing:
- Confirm `Date` is a Date data type.
- Confirm `Quantity` is a whole number.
- Confirm `Unit Price` and `Total Sales` are numeric/currency fields.
- Confirm `Product` and `Category` are text fields.
- Verify that product/category slicers filter all intended cards, charts, and tables.
- Verify that the displayed totals reconcile to 297 units and $5,621 when no filters are applied.

## 6. Scope & Limitations
The supplied workbook contains only 7 rows, 6 products, 2 categories, and 4 dates. It has no cost, discount, tax, return, or inventory fields. Therefore, this dataset supports basic sales-revenue and quantity analysis, but not profit, margin, stock turnover, or return-rate analysis.

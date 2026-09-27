# Global Superstore — Sales Operations MIS

## Project Overview

This project demonstrates the development of an Excel-based Sales Operations Management Information System (MIS) using the publicly available Global Superstore transactional dataset.

The project focuses on building a structured reporting workflow covering:

- Data profiling
- Data quality validation
- Power Query data preparation
- KPI calculation
- Daily MIS reporting
- Weekly MIS reporting
- Monthly MIS reporting
- Pivot-based business analysis
- Management summary reporting
- Reconciliation and validation

The objective is to demonstrate how raw transactional data can be transformed into a structured and management-ready reporting system using Microsoft Excel and Power Query.

---

## Business Objective

The objective is to create a reliable sales reporting workflow that allows management to monitor:

- Sales performance
- Profitability
- Order volume
- Customer volume
- Shipping performance
- Shipping costs
- Returns
- Market performance
- Regional performance
- Data-quality exceptions

The project emphasizes data accuracy and reconciliation before management reporting.

---

## Dataset

The project uses the publicly available Global Superstore dataset.

The main source tables are:

### Orders

Contains transactional sales information including:

- Order ID
- Order Date
- Ship Date
- Customer
- Segment
- Geography
- Market
- Region
- Product
- Category
- Sales
- Quantity
- Discount
- Profit
- Shipping Cost
- Order Priority

### Returns

Contains return information linked to Order ID.

### People

Contains regional personnel mapping information from the source dataset.

---

## Data Architecture

The project follows a structured workflow:

RAW → STAGING → CLEAN → REPORTING

### RAW

The original source workbook is preserved without modification.

### STAGING

Power Query is used to import and prepare the source tables.

### CLEAN

Data types are standardized and text fields are cleaned while preserving source values that require business review.

### REPORTING

Validated data is used to create KPI calculations, periodic MIS reports, pivot analysis and the management summary.

---

## Power Query Workflow

Power Query was used to create the following staging queries:

- `stg_Orders`
- `stg_Returns`
- `stg_People`

Key preparation steps included:

- Header promotion
- Data-type assignment
- Text trimming
- Text cleaning
- Shipping-days calculation
- Return-market standardization
- Preservation of source values requiring review

The cleaned tables are loaded into Excel as:

- `tbl_Orders`
- `tbl_Returns`
- `tbl_People`

---

## Excel MIS Reporting

The final workbook contains the following reporting layers:

### KPI Calculation Layer

Core KPIs include:

- Total Sales
- Total Profit
- Total Quantity
- Total Orders
- Unique Customers
- Average Order Value
- Profit Margin
- Average Shipping Days
- Total Shipping Cost
- Returned Orders
- Return Rate

### Daily MIS

Daily reporting includes:

- Sales
- Profit
- Quantity
- Orders
- Customers
- Shipping Cost
- Average Shipping Days

### Weekly MIS

Weekly reporting provides the same core operational measures aggregated by week.

### Monthly MIS

Monthly reporting provides the same measures aggregated by month.

### Pivot Analysis

The workbook includes:

- Market Performance analysis
- Region Performance analysis

Both analyses use distinct Order ID counts where order-level counts are required.

### Management Summary

The management summary provides:

- Core KPI values
- Management reporting notes
- Market and regional reporting references
- Operational performance information
- Important data-quality notes

---

## Data Quality

Data-quality validation was performed before reporting.

Checks included:

- Missing Order IDs
- Missing Order Dates
- Missing Sales
- Missing Profit
- Missing Postal Codes
- Duplicate full rows
- Duplicate Row IDs
- Repeated Order ID + Product ID combinations
- Negative quantity
- Zero quantity
- Invalid discounts
- Ship dates before order dates
- Unmatched return Order IDs
- Duplicate return Order IDs
- Region mapping differences

The project deliberately preserves valid source information instead of automatically deleting records simply because they require investigation.

---

## Important Data-Quality Findings

### Postal Code

A substantial proportion of Postal Code values are missing.

These values were preserved rather than artificially filled.

### Repeated Order/Product Combinations

Repeated Order ID + Product ID combinations were identified.

They were not automatically deleted because repeated combinations are not, by themselves, sufficient evidence of duplicate transactions.

### Returns

A duplicate Return Order ID was identified and retained for review.

### Market Naming

The Returns source uses `United States` while the Orders source uses `US`.

A standardized field was created for reconciliation while the original source value was preserved.

### Region Naming

The People table contains `AMEA` while the Orders data contains `EMEA`.

The source values were preserved rather than making an unsupported mapping assumption.

---

## Reconciliation

The reporting workflow includes reconciliation between different reporting layers.

The following measures were reconciled:

- Sales
- Profit
- Quantity
- Orders

Daily, weekly and monthly reporting totals were checked against the KPI calculation layer.

Market and regional pivot totals were also reconciled against the KPI calculation layer.

---

## Tools Used

- Microsoft Excel
- Power Query
- Excel Tables
- Excel formulas
- Pivot Tables
- Data-quality validation
- KPI calculations

---

## Project Structure

```text
GLOBAL-SUPERSTORE-MIS/
│
├── 01_RAW/
├── 02_STAGING/
├── 03_PROCESSED/
├── 04_EXCEL_MIS/
│
└── 05_GITHUB/
    ├── Excel/
    │   └── Global_Superstore_MIS.xlsx
    │
    ├── Documentation/
    │
    └── Screenshots/

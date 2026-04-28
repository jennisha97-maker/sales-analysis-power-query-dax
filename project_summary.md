# Project Summary — Sales Analysis 360° Excel

## Overview
This project demonstrates a complete, production-ready Excel analytics solution built from scratch using Microsoft Excel's full modern stack — Power Query, Data Model (Power Pivot), DAX, Pivot Tables, and interactive Charts.

---

## Problem Statement
Raw sales transaction data existed in CSV format without any structured analysis. The goal was to transform this into an interactive dashboard that answers:
- How is revenue and profit trending over time?
- Which product categories and individual products drive the most value?
- What are the seasonal and day-of-week patterns in sales?
- How do weekday and weekend performance compare?
- Which products are underperforming or unsold?

---

## Approach

### Step 1 — Data Ingestion (Power Query)
- Imported `sales_data.csv` into Power Query Editor
- Cleaned column headers, fixed date formats, removed blank rows
- Added calculated columns: `WeekType`, `Quarter`, `MonthName`
- Created a separate `Date` dimension table using `List.Dates()`
- Merged `Sales` with `Product` lookup on `ProductID`
- Loaded all tables into the Excel Data Model (not worksheet)

### Step 2 — Data Model Design
- Built a Star Schema: `Sales` (fact) linked to `Product` and `Date` (dimensions)
- Defined relationships in Power Pivot Diagram View
- Hid raw key columns from Pivot Table field list for cleaner UX

### Step 3 — DAX Measures
- Created a dedicated `_Measures` table to house all DAX
- Built base measures first (Revenue, Profit, COGS, Qty, Transactions)
- Layered time-intelligence measures on top (YOY, SAMEPERIODLASTYEAR)
- Added ratio and conditional measures (Profit Margin%, Weekday Split, Above Avg Flag)

### Step 4 — Pivot Tables
- Built 7 Pivot Tables from the Data Model (not worksheet ranges)
- Connected all Pivot Tables to shared Year slicer for synchronized filtering
- Applied number formatting: currency, percentages, comma separators

### Step 5 — Dashboard & Charts
- Designed 3 dashboard sheets: `Analysis 1`, `Analysis 2`, `Time Series Dashboard`
- Added KPI summary cards (Revenue, Profit, Margin%, Transactions, Qty)
- Created YOY comparison cards with percentage change indicators
- Built line, bar, donut and column charts linked to Pivot Tables
- Applied dynamic chart titles using cell references

---

## Skills Demonstrated
- Power Query (M language, custom steps, query merging)
- Data Modelling (Star schema, relationships, cardinality)
- DAX (CALCULATE, DIVIDE, FILTER, time intelligence, AVERAGEX)
- Pivot Tables (from Data Model, calculated fields, grouping)
- Excel Charts (linked to Pivot Tables, dynamic titles)
- Dashboard Design (slicers, layout, conditional formatting)

---

## Files
| File | Description |
|------|-------------|
| `sales_analysis.xlsm` | Main workbook — all sheets, model, and macros |
| `Data/sales_data.csv` | Raw transaction dataset |
| `Screenshots/` | Visual documentation of each component |
| `Docs/project_summary.md` | This file |

---

## Author
**Jennisha K** — Data Analyst  
jennisha97@gmail.com | [LinkedIn](https://linkedin.com/in/jennisha-k-66a195191)

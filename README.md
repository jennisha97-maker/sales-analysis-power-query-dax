**📊 Sales Analysis — Power Query | DAX | Data Model | Excel 360°
> A complete end-to-end Sales Performance Analysis built entirely in Microsoft Excel — covering data ingestion, transformation, modelling, calculations, and interactive dashboards.
---
🎯 Objective
Analyze sales transaction data to uncover revenue trends, profit patterns, product performance, and seasonal behaviour — using a fully integrated Excel solution without any external tools.
---
🗂️ Project Structure
```
sales-analysis-power-query-dax/
│
├── 📁 Data/
│   └── sales_data.csv               ← Raw transaction dataset
│
├── 📁 Screenshots/
│   ├── dashboard_overview.png        ← Main dashboard view
│   ├── power_query_steps.png         ← Power Query transformation steps
│   ├── data_model.png                ← Data Model relationship diagram
│   ├── dax_measures.png              ← DAX measures panel
│   └── pivot_charts.png              ← Pivot charts view
│
├── 📁 Docs/
│   └── project_summary.md           ← Detailed write-up
│
├── sales_analysis.xlsm              ← Main Excel workbook (upload separately)
├── .gitignore
└── README.md
```
---
🛠️ Tools & Techniques Used
🔵 Power Query — Data Transformation

Step	What Was Done

Data Import	Loaded raw CSV into Power Query Editor
Column Cleanup	Removed nulls, renamed headers, fixed data types
Date Table	Created a custom Date dimension table (Year, Quarter, Month, Week, Day)
Conditional Columns	Added `WeekType` (Weekday / Weekend) and `Quarter` labels
Merge Queries	Joined sales data with product lookup table
Load to Model	Loaded all queries directly into the Excel Data Model
---
🟠 Data Model — Relationships

Table	Role	Relationship
`Sales`	Fact Table	Many side
`Product`	Dimension	One side → ProductID
`Date`	Dimension	One side → OrderDate
Star schema design with `Sales` as the central fact table
All relationships set as one-to-many, single direction
Data Model powers all Pivot Tables and DAX calculations
---
🟢 DAX Measures
```
Total Revenue       = SUM(Sales[Revenue])
Total Profit        = SUM(Sales[Profit])
Total COGS          = SUM(Sales[CostOfGoodsSold])
Profit Margin %     = DIVIDE([Total Profit], [Total Revenue], 0)
Total Transactions  = COUNTROWS(Sales)
Total Order Qty     = SUM(Sales[OrderQuantity])

YOY Revenue Change  =
    VAR CurrentYear  = CALCULATE([Total Revenue], DATESYTD(Date[OrderDate]))
    VAR PreviousYear = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR(Date[OrderDate]))
    RETURN DIVIDE(CurrentYear - PreviousYear, PreviousYear, 0)

Weekday Profit %    =
    DIVIDE(
        CALCULATE([Total Profit], Sales[WeekType] = "Week day"),
        [Total Profit], 0
    )

Above Avg Revenue Flag =
    IF([Total Revenue] >= AVERAGEX(ALL(Date[Year]), [Total Revenue]), "Above Avg", "Below Avg")
```
---
🔴 Pivot Tables

Pivot Table	Rows	Values
Yearly KPI Summary	Year	Revenue, Profit, COGS, Margin%, Transactions, Qty
Monthly Profit Trend	MonthName	Profit, Transactions
Quarterly Breakdown	Quarter	Profit, Revenue, Share%
Weekday vs Weekend	WeekType	Profit, Profit%
Day-of-Week Analysis	DayName	Profit, Transactions
Category Performance	Category, SubCategory	Revenue, Profit, Qty
Top 10 Products	ProductName	Revenue, Profit, Margin%
---
🟣 Charts & Dashboard

Chart	Type	Sheet

Monthly Revenue & Profit Trend	Line Chart	Time Series Dashboard
Category Revenue Split	Bar Chart	Analysis 1
Weekday vs Weekend Profit	Donut Chart	Analysis 2
Quarterly Profit Share	Column Chart	Analysis 2
KPI Cards	Shape + Formula	Analysis 1
Slicers connected to all Pivot Tables for Year filtering
Dynamic titles using cell references that update with slicer selection
Conditional formatting applied to highlight above/below average values
---
📈 Key Insights

Bikes dominate — Mountain, Touring & Road Bikes contribute ~87% of total revenue
Q4 outperforms Q3 by ~23% in profit — strong seasonal demand Oct–Dec
40.6% profit margin maintained consistently across all product categories
Weekdays drive 57.7% of profit vs 42.3% on weekends
Friday is the strongest sales day; Sunday is the lowest
15 of 25 products unsold — opportunity for product mix optimization
---
💼 Business Impact

Inventory planning can prioritize high-margin Bike SKUs
Q3 promotional campaigns can close the gap with Q4 performance
Weekend-targeted offers can grow the 42.3% weekend profit share
Unsold product review can free up working capital
---
🚀 How to Use

Download `sales_analysis.xlsm` from this repo
Enable macros when prompted
Use the Year slicer on the dashboard to filter all views
Explore individual sheets: `Analysis 1`, `Analysis 2`, `Time Series Dashboard`
The Data Model and all DAX measures are accessible via Power Pivot → Manage
---
👩‍💻 About
Jennisha K  
Data Analyst | SQL · Power BI · Tableau · Excel · Python  
📧 jennisha97@gmail.com  
🔗 linkedin.com/in/jennisha-k-66a195191
---
📄 License
MIT License — free to use with attribution.**

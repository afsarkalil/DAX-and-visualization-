# DAX-and-visualization-
using DAX formula and visualizat# 📊 E-Commerce Sales Analysis | Power BI + DAX

An interactive Power BI dashboard that analyzes sales trends, profitability, and target achievement for an e-commerce business, built using **DAX calculated columns, measures, and time intelligence**.

---

## 🎯 Project Overview

Using the E-Commerce Sales dataset and the data model built in the previous assignment (Power Query transformations + table relationships), this project focuses on:

- Writing **DAX** for calculated columns and business measures
- Building **time-intelligence** calculations (Year-to-Date sales)
- Designing an **interactive dashboard** that tells a clear story about sales performance

**Business questions answered**
- Are we meeting sales targets in each category?
- Which sub-categories are the most (and least) profitable?
- How do monthly sales trend over time?
- Which cities and states drive the most sales and orders?

---

## 🗂️ Dataset

| Table | Key Columns |
|---|---|
| **List of Orders** | Order ID, Order Date, Customer Name, City, State, Category, Amount, Profit |
| **Order Details** | Order ID, Category, Sub-Category, Quantity, Amount, Profit |
| **Sales Target** | Category, Month of Order Date, Target |

**Data model:** `List of Orders` (1) → (many) `Order Details` on **Order ID**; `Sales Target` linked through **Category** (and month).

> 📷 *Add a screenshot of your model view here:* `![Data Model](images/data_model.png)`

---

## 🧮 DAX Calculations

### Calculated Columns (Order Details)

```DAX
-- Combine Category and Sub-Category
Category Type = 'Order Details'[Category] & " - " & 'Order Details'[Sub-Category]

-- Revenue per order line
Revenue = 'Order Details'[Amount] * 'Order Details'[Quantity]

-- Classify against the overall average Amount
Sales Category =
IF (
    'Order Details'[Amount] >= AVERAGE ( 'Order Details'[Amount] ),
    "Above Average",
    "Below Average"
)
```

### Measures

```DAX
-- 1. Total number of orders
Order Count = DISTINCTCOUNT ( 'Order Details'[Order ID] )

-- 2. Average profit for orders placed in Delhi
Average Profit in Delhi =
CALCULATE (
    AVERAGE ( 'Order Details'[Profit] ),
    'List of Orders'[City] = "Delhi"
)

-- 3. Year-to-Date sales
YTD Sales =
TOTALYTD (
    SUM ( 'Order Details'[Amount] ),
    'Date'[Date]
)
```

> ⚠️ **Replace the formulas above with the exact ones from your `.pbix`** (table/column names and the date table may differ).

---

## 📈 Visualizations

| # | Visual | Chart Type | Purpose |
|---|---|---|---|
| 1 | Sales Target Achievement by Category | Clustered column | Actual sales vs. target per category |
| 2 | Max Profit Margin by Sub-Category | Donut | Highest profit margin per sub-category |
| 3 | Monthly Sales Trend | Line chart | Sales movement over time |
| 4 | Profit vs. Quantity by Sub-Category | Scatter | Relationship between volume and profit |
| 5 | Total Sales vs. Target | Cards + multi-row card | Quick KPI comparison; minimum target per segment |
| 6 | Sales Performance Matrix | Matrix | Actual vs. target by category and month |
| 7 | Geographic Sales Analysis | Map | Total sales by city |
| 8 | Sales Distribution by Sub-Category | Treemap | Share of sales per sub-category |
| 9 | Order Count by State | Funnel | Distribution of orders across states |

> 📷 *Add your screenshots:*
> `![Dashboard](images/dashboard.png)`

---

## 💡 Key Insights

*(Fill these in from your own dashboard — recruiters love this section.)*

- **Targets:** Which categories exceeded / missed their targets?
- **Profitability:** Which sub-categories have the best margin? Any high-sales, low-profit items?
- **Trend:** Peak and low months for sales.
- **Geography:** Top states/cities by sales and order count.
- **Delhi:** How does average profit in Delhi compare to overall?

---

## 🛠️ Tools & Skills

- **Power BI Desktop** – data modeling, report design
- **DAX** – calculated columns, `CALCULATE`, `DISTINCTCOUNT`, `TOTALYTD`
- **Power Query** – data cleaning and transformation (previous assignment)
- Data storytelling, dashboard formatting, business analysis

---

## 📁 Repository Structure

```
├── power_bi_ass_2.pbix      # Power BI report
├── README.md
├── images/                  # Screenshots (model, DAX, visuals, dashboard)
└── Power_BI_Assignment_2.pdf  # DAX screenshots + visual explanations
```

---

## ▶️ How to Open

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows).
2. Download `power_bi_ass_2.pbix` from this repo.
3. Open it in Power BI Desktop and explore the report pages and slicers.

---

## 👤 Author

**Your Name**
[LinkedIn](https://linkedin.com/in/your-profile) • [GitHub](https://github.com/your-username) • your.email@example.comion 

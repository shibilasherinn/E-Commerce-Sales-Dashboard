# E-Commerce Sales Dashboard — Power BI

A 4-page interactive Power BI dashboard analyzing 5 years of multi-category Indian e-commerce sales data (FY 2021–2026), built with DAX measures, Power Query, and a custom dark premium theme.

---

## Dashboard Preview

### Overview
![Overview](Overview%20E-Commerce.png)

### Sales Analysis
![Sales Analysis](Sales%20Analysis%20E-Commerce.png)

### Customers
![Customers](Customers%20E-Commerce.png)

### Products
![Products](Products%20E-Commerce.png)

---

## Project Summary

| Detail | Info |
|---|---|
| Tool | Power BI Desktop |
| Data | Synthetic (Python-generated) |
| Time Period | June 2021 – June 2026 |
| Total Orders | 11,000+ |
| Customers | 2,600 |
| Products | 266 (8 categories) |
| Pages | 4 |
| Theme | Custom Dark & Premium |

---

## Dashboard Pages

### 1. Overview
- KPI cards: Revenue, Total Orders, AOV, Profit
- Revenue trend line chart (monthly, 5-year)
- Revenue by category (horizontal bar)
- Top 5 products by revenue (table)

### 2. Sales Analysis
- Revenue by region (bar chart)
- Revenue by payment mode (donut chart)
- Revenue vs discount band (line & column chart)
- Order status breakdown (donut chart)

### 3. Customers
- Revenue by customer segment (donut chart)
- Revenue by age group & gender (clustered column)
- New vs repeat customers over time (line chart)
- Top 5 customers by spend (table)

### 4. Products
- Category & sub-category performance (treemap)
- Top 10 brands by revenue (bar chart)
- Return rate by category (column chart)
- Profit margin by category (column chart)

---

## Data Model

Star schema with 4 tables:

```
Orders (fact)
├── Customers (dimension) — via CustomerID
├── Products (dimension) — via ProductID
└── DateTable (dimension) — via OrderDate
```

---

## DAX Measures

```
Revenue = SUMX(Orders, Orders[Quantity] * Orders[UnitPrice] * (1 - Orders[DiscountPct]/100))

Total Orders = DISTINCTCOUNT(Orders[OrderID])

AOV = DIVIDE([Revenue], [Total Orders])

Profit = SUMX(Orders, Orders[Quantity] * (Orders[UnitPrice]*(1-Orders[DiscountPct]/100) - RELATED(Products[CostPrice])))

Profit Margin % = DIVIDE([Profit], [Revenue])

Return Rate = DIVIDE(CALCULATE([Total Orders], Orders[OrderStatus]="Returned"), [Total Orders])

Cancelled Orders = CALCULATE([Total Orders], Orders[OrderStatus]="Cancelled")

Total Customers = DISTINCTCOUNT(Orders[CustomerID])
```

---

## Files in This Repository

| File | Description |
|---|---|
| `Orders.csv` | 11,000+ order transactions (fact table) |
| `Products.csv` | 266 products across 8 categories |
| `Customers.csv` | 2,600 customers across 12 Indian states |
| `DarkPremiumTheme.json` | Custom Power BI theme file |
| `*.pbix` | Power BI report file |
| `*.png` | Dashboard page screenshots |

---

## Tools & Technologies

- **Power BI Desktop** — Report building, DAX, Power Query
- **DAX** — Dynamic measures for KPIs, ratios, and time intelligence
- **Power Query (M)** — Data transformation and star schema modeling
- **Python** — Synthetic dataset generation (Faker library)
- **Custom Theme JSON** — Dark & premium visual styling

---

## Key Insights from the Data

- Electronics dominates revenue at ₹102M (66% of total)
- UPI is the most preferred payment mode (32%)
- Diwali season (Oct–Nov) shows consistent 2.5x revenue spike each year
- South region leads in sales (₹52M), followed by North (₹49M)
- Books category has the highest profit margin (21%)
- Return rate is consistent across categories (~10%)

---

## How to Use

1. Clone or download this repository
2. Open Power BI Desktop
3. Load the three CSV files (Orders, Products, Customers)
4. Build the Date table using the DAX formula in the report
5. Apply `DarkPremiumTheme.json` via View → Themes → Browse for themes
6. Or open the `.pbix` file directly if included

---

## Author

**Shibila Sherin M**
Data Science | Data Analysis | Power BI | Python |Statistics | Machine Learning | NLP | Deep Learning | SQL

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/shibila-sherin-m-99881b3a1)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat&logo=github)](https://github.com/shibilasherinn/E-Commerce-Sales-Dashboard)

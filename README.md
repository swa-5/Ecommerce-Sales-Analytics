# E-Commerce Sales Analytics

An end-to-end data analytics project analyzing e-commerce sales performance using **Python, Pandas, MySQL, SQL, and Power BI**.

The project covers the complete analytics workflow — from raw data cleaning and exploratory analysis to SQL-based business analysis and an interactive Power BI dashboard.

---

## 📌 Project Overview

This project analyzes **500 e-commerce orders** to understand:

* Sales and profit performance
* Product and category performance
* Regional sales trends
* Monthly revenue trends
* Customer profitability
* Payment method performance
* Discount and profit-margin patterns

The dataset is **synthetically generated for portfolio and learning purposes**.

---

## 🛠️ Tools & Technologies

| Tool         | Purpose                                  |
| ------------ | ---------------------------------------- |
| Python       | Data cleaning and exploratory analysis   |
| Pandas       | Data manipulation and analysis           |
| NumPy        | Data generation and numerical operations |
| Matplotlib   | Data visualization                       |
| MySQL        | Data storage and querying                |
| SQL          | Business analysis                        |
| Power BI     | Interactive dashboard                    |
| Git & GitHub | Version control and portfolio            |

---

## 📂 Project Structure

```text
Ecommerce-Sales-Analytics/
│
├── data/
│   └── ecommerce_sales.csv
│
├── python/
│   └── untitled.ipynb
│
├── sql/
│   └── analysis_queries.sql
│
├── power bi/
│   └── Ecommerce_Sales_Analytics.pbix
│
├── .gitignore
└── README.md
```

---

## 📊 Dataset

The dataset contains **500 orders** and 12 columns:

* `Order_ID`
* `Order_Date`
* `Customer_ID`
* `Product`
* `Category`
* `Region`
* `Quantity`
* `Unit_Price`
* `Discount_Percent`
* `Revenue`
* `Profit`
* `Payment_Mode`

### Categories

* Electronics
* Accessories
* Wearables

### Regions

* North
* South
* East
* West
* Central

### Payment Modes

* UPI
* Credit Card
* Debit Card
* Cash on Delivery

---

## 🔄 Analytics Workflow

```text
Raw Dataset
     ↓
Python + Pandas
     ↓
Data Cleaning
     ↓
Exploratory Data Analysis
     ↓
MySQL Database
     ↓
SQL Business Analysis
     ↓
Power BI Dashboard
     ↓
Business Insights
```

---

## 🐍 Python Analysis

Python was used for:

* Data loading
* Data-type validation
* Missing-value analysis
* Duplicate detection
* Descriptive statistics
* Revenue analysis
* Profit analysis
* Product analysis
* Category analysis
* Regional analysis
* Monthly trend analysis
* Customer analysis
* Profit-margin analysis
* Outlier/distribution checks

### Data Quality Results

* Rows: **500**
* Columns: **12**
* Missing values: **0**
* Duplicate rows: **0**

---

## 🗄️ SQL Analysis

The cleaned dataset was imported into MySQL and analyzed using SQL.

Key SQL techniques used:

* `SELECT`
* `SUM()`
* `COUNT()`
* `GROUP BY`
* `ORDER BY`
* `ROUND()`
* `LIMIT`
* `DATE_FORMAT()`
* Common Table Expressions (`CTE`)
* Window functions
* `ROW_NUMBER()`
* `RANK()`

### Business Questions Answered

1. What are the total revenue and profit?
2. Which products generate the most revenue?
3. Which categories perform best?
4. Which regions generate the highest revenue?
5. How does revenue change month by month?
6. Which products generate the most profit?
7. Who are the most profitable customers?
8. Which payment methods perform best?
9. How do discounts relate to profit margins?
10. Which region has the highest profit margin?
11. What are the top products in each region?

---

## 📈 Key Performance Indicators

| KPI                   |       Value |
| --------------------- | ----------: |
| Total Revenue         | ₹16,424,865 |
| Total Profit          |  ₹2,783,621 |
| Total Orders          |         500 |
| Total Units Sold      |       1,250 |
| Average Order Value   |  ₹32,849.73 |
| Overall Profit Margin |      16.95% |

---

## 💡 Key Business Insights

### Product Performance

**Laptop** generated the highest revenue and profit among all products.

**Smartphone** was the second-highest revenue-generating product.

### Category Performance

**Electronics** dominated overall sales, generating approximately ₹14.73M in revenue.

### Regional Performance

**North** generated the highest revenue at approximately ₹3.83M.

**South** achieved the highest profit margin at approximately **17.86%**.

### Monthly Performance

**January** recorded the highest monthly revenue.

**April** recorded the lowest monthly revenue.

### Payment Methods

**Cash on Delivery** generated the highest total revenue and absolute profit.

**Credit Card** achieved the highest profit margin among payment methods.

**Debit Card** had the highest average order value.

### Customer Performance

A small group of customers contributed significantly to total revenue and profit, with **CUST126** being the highest-profit customer in this dataset.

> Note: These observations describe this synthetic dataset and should not be interpreted as real-world causal relationships.

---

## 📊 Power BI Dashboard

The Power BI dashboard provides an interactive view of the e-commerce business.

### Dashboard Components

* KPI cards
* Monthly Revenue Trend
* Revenue by Product
* Revenue by Category
* Revenue by Region
* Profit by Product
* Profit Margin by Category
* Profit Margin by Region
* Revenue by Payment Mode
* Profit Margin by Discount
* Top Customers by Profit

### Interactive Filters

Users can filter the dashboard by:

* Region
* Category
* Order Date

---

## 🎯 Skills Demonstrated

This project demonstrates practical experience with:

* Data cleaning
* Exploratory Data Analysis
* Python/Pandas
* SQL
* MySQL
* Aggregation and grouping
* CTEs
* Window functions
* Business KPI analysis
* Data visualization
* Power BI dashboards
* Git/GitHub
* Business storytelling

---

## 🚀 Future Improvements

Possible improvements include:

* Customer segmentation
* Cohort analysis
* Product-level profitability optimization
* More realistic customer behavior
* Forecasting future sales
* Advanced Power BI DAX measures
* Automated data pipelines
* Cloud data warehouse integration
* Deployment of an automated analytics pipeline

---

## 👨‍💻 Author

**Swatantra Pandey**

IGNOU MCA Graduate | Aspiring Data Analyst | Future Data Scientist

---

## ⭐ Project Purpose

This project was created as a portfolio project to demonstrate an end-to-end data analytics workflow using commonly used industry tools.

If you find the project useful, consider giving the repository a ⭐.

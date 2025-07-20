# Sales Insight Data Analytics-dashboard
## Table of Contents

- [Case Study](#case-study)
- [Dataset Description](#dataset-description)
- [ER Diagram](#er-diagram)
- [Data Cleaning](#data-cleaning)
- [Data Analysis](#data-analysis)
- [Dashboard](#dashboard)

## Case Study
To analyze sales trends across regions, customer types, and product categories over four years, and to identify strategic opportunities for growth and optimization.

## Dataset Description

Our dataset consists of the following observations which include:

###  Transactions

- **product_code** – Unique identifier for the product sold in the transaction  
- **customer_code** – Unique identifier for the customer who placed the order  
- **market_code** – Unique identifier of the market (city/region) where the order was placed  
- **order_date** – Date on which the transaction occurred  
- **sales_qty** – Number of units sold in the transaction  
- **sales** – Sale price per unit (can be before discount or tax)  
- **amount** – Total transaction amount (quantity × unit price, adjusted if needed)  

---

###  Products

- **product_code** – Unique identifier for the product (used to join with transactions)  
- **product_type** – Type/category of product (e.g., Electronics, Apparel, Grocery, etc.)  

---

###  Markets

- **market_code** – Unique code for each market/city  
- **markets_name** – Name of the market (e.g., Delhi NCR, Mumbai, Chennai)  
- **zone** – Region-classification (e.g., North, South, East, West)  

---

###  Date

- **date** – Actual date of the transaction  
- **cy_date** – Custom-formatted date (optional: e.g., MM-YYYY or fiscal calendar)  
- **year** – Year (e.g., 2017, 2018...)  
- **month_name** – Month name (e.g., Jan, Feb, Mar...)  

---

###  Customer

- **customer_code** – Unique ID for each customer  
- **customer_name** – Name or label of the customer (e.g., "Nixon", "Electrical Ltd")  
- **customer_type** – Type of customer  

## ER Diagram
<img width="1917" height="973" alt="sales 20_07_2025 17_47_26" src="https://github.com/user-attachments/assets/bc1202d8-ac4b-49f5-96e8-311d9cd12350" />
## Data Cleaning


This project involves cleaning, analyzing, and visualizing sales transaction data using **SQL** for querying and **DAX** for Power BI reporting. The dataset includes transactions, products, markets, customers, and time-related tables from 2017 to 2020.

## 📋 Table of Contents

- [SQL Queries for Analysis](#sql-queries-for-analysis)
  - [1. Total Revenue per Year](#1-total-revenue-per-year)
  - [2. Top 5 Markets by Revenue](#2-top-5-markets-by-revenue)
  - [3. Top 5 Products by Quantity Sold](#3-top-5-products-by-quantity-sold)
- [DAX Measures for Power BI](#dax-measures-for-power-bi)
  - [• Total Revenue](#•-total-revenue)
  - [• Total Quantity Sold](#•-total-quantity-sold)

---

## SQL Queries for Analysis

### 1. Total Revenue per Year
      SELECT d.year, SUM(st.amount) AS total_revenue
      FROM sales_transactions st
      JOIN date d ON st.order_date = d.date
      GROUP BY d.year
      ORDER BY d.year;
### 2. Top 5 Markets by Revenue
     SELECT m.markets_name, SUM(st.amount) AS revenue
     FROM sales_transactions st
     JOIN markets m ON st.market_code = m.market_code
     GROUP BY m.markets_name
     ORDER BY revenue DESC
     LIMIT 5;
### 3.Top 5 Products by Quantity Sold
    SELECT p.product_type, SUM(st.sales_qty) AS total_qty
    FROM sales_transactions st
    JOIN products p ON st.product_code = p.product_code   
    GROUP BY p.product_type
    ORDER BY total_qty DESC
    LIMIT 5;
DAX Measures for Power BI
### 1.Total Revenue
            Total Revenue = SUM(sales_transactions[amount])
### 2.Total Quantity Sold
            Total Sales Qty = SUM(sales_transactions[sales_qty])






## Data Analysis
### 1.  Revenue Growth Year-over-Year
Insight:

Revenue has grown steadily from ₹90M in 2017 to ₹130M in 2020, with a peak of ₹145M in 2019.
Interpretation:
The business is scaling well, but the slight dip in 2020 might be due to market conditions (e.g., COVID-19 impact).
### 2. Top Performing Markets
Insight:

Delhi NCR is the most profitable market contributing ~52% of total revenue, followed by Mumbai and Ahmedabad.
Interpretation:
These Tier-1 markets are revenue drivers. Consider expansion or retention strategies here.
### 3.  Best-Selling Products
Insight:

Product types like Consumer Electronics and Grocery Essentials top the sales list both in quantity and revenue.
Interpretation:
These categories could benefit from targeted promotions and stocking priorities.
### 4. Monthly Seasonality in Sales
Insight:

Revenue tends to spike in July and December, indicating seasonal or festival-related boosts.
Interpretation:
These periods can be leveraged with promotions, combo offers, or bundled pricing.
### 5. 🧭 Zone-Wise Distribution
Insight:

Northern and Western zones contribute over 75% of revenue.
Interpretation:
The South and East zones are underperforming — explore local campaigns, logistics, or product adjustments.
## Dashboard

<img width="1913" height="963" alt="sales dashboard" src="https://github.com/user-attachments/assets/3ec86e45-1683-4905-95b6-1e4460f39fb0" />

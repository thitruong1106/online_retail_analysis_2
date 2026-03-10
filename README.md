# UK Online Retail Behaviour & Performance Analysis (2009–2011)
This project builds on a previous analysis of the same dataset but focuses on **return behaviour, customer revenue concentration, and product performance**, providing a deeper investigation into operational patterns within the business.

![SQL](https://img.shields.io/badge/SQL-MySQL-blue)
![Project Type](https://img.shields.io/badge/Analysis-Retail_Data-green)

### Dataset

Dataset used: Online Retail II UCI

Source: https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci/data

---

## Executive Summary

This project analyzes transaction data from a UK-based online retailer (2009–2011) to understand:

- Revenue patterns across the year
- Customer revenue concentration
- Product performance
- Return behaviour and anomalies

The analysis was conducted using **MySQL**, with structured queries to ensure the work is reproducible and transparent.

---

## Objective

The purpose of this analysis was to understand how the business generates revenue and what risks may exist in the current sales structure.

The goal was to identify:

- seasonal revenue patterns
- the products driving the business
- the customers responsible for the largest share of revenue
- whether product returns indicate operational issues or customer dissatisfaction

---

## Cleaning The Data

To ensure the analysis reflected **real customer purchases only**, the following records were removed:

- Cancelled invoices (Invoice starting with `"C"`)
- Manual adjustments and accounting entries
- Fees such as Amazon charges and bank charges
- Negative price values
- Non-product stock codes such as postage and adjustments

Revenue was calculated as: Quantity * Price


This ensures that all revenue represents actual product sales.

---

## Key Findings

### 1. The Business Is Strongly Holiday Driven

Across the two-year dataset, the revenue pattern is very clear.

Revenue climbs steadily starting in **September**, builds through **October**, and peaks in **November**.

Revenue reached approximately:

- **£1.47M in November 2010**
- **£1.50M in November 2011**

Once January arrives, revenue drops sharply.

This suggests the business is heavily driven by **holiday shopping behaviour**, which is consistent with a retailer selling giftware, decorations, and home accessories.

While this pattern is expected, it introduces operational challenges:

- Cash flow volatility between peak and off-season months
- Inventory planning risk
- Operational pressure during peak demand periods

---

### 2. The January Return Spike Was Not Customer Dissatisfaction

At first glance, return rates appear alarming.

Returns increased from roughly:

- **11% in December 2010**
- to **20% in January 2011**
- and approximately **32% in December 2011**

Initially, this suggested customers were returning unwanted Christmas gifts.

However, further investigation revealed a different explanation.

One product, **StockCode 23166 (Medium Ceramic Top Storage Jar)**, accounted for **74,215 returned units in January 2011**.

When examining the invoices responsible for these returns, they were **not distributed across many customers**. Instead, they appeared within **very few invoices containing extremely large quantities**.

This behaviour does not match consumer returns and instead indicates an **operational reversal**, such as:

- inventory corrections
- wholesale order cancellations
- accounting adjustments

The spike in January returns therefore reflects **operational activity rather than customer dissatisfaction**.

---

### 3. A Small Group of Customers Drives Most Revenue

Customer revenue follows a clear Pareto pattern.

- **Top 10% of customers generate ~64% of total revenue**
- **Top 1% generate ~32%**
- **Top 0.1% (approximately 6 customers) generate ~12%**

This means a very small group of customers contributes a disproportionate share of revenue.

The implication is that the business is **highly dependent on high-value customers**.

If even one of these customers stops purchasing, the revenue impact could be significant.

Understanding who these customers are and maintaining strong relationships with them is therefore critical.

---

### 4. Product Performance Is Driven by Gift-Oriented Items

The products generating the most revenue align closely with the retailer's product category.

Top revenue products include:

- Regency Cake Stand 3 Tier
- White Hanging Heart T-Light Holder
- Jumbo Bag Red Retrospot
- Party Bunting

Top products by units sold include:

- World War 2 Gliders Assorted Design
- Assorted Colour Bird Ornament
- White Hanging Heart T-Light Holder
- Jumbo Bag Red Retrospot

These products are typical **gift items or decorative household products**, which explains their strong performance during the holiday season.

Maintaining stock availability for these items before Q4 is essential, as stock shortages during peak demand would result in lost revenue.

---

### 5. Seasonal Products Carry Higher Return Risk

When products were initially ranked by return rate, several products appeared to have **return rates exceeding 100%**.

This was caused by two factors:

- operational reversals appearing in the data
- products with very small sales volumes where one return distorts the percentage

After applying a **minimum sales threshold of 50 units**, the products with the highest return rates were primarily **seasonal decorative products**, such as:

- cherry lights
- festive candles
- holiday decorations

Seasonal products have a short selling window, and returns may occur after the peak season when demand drops.

This suggests that higher return rates for seasonal items may simply be a normal part of the business model rather than a sign of product issues.

---

## Business Implications

What does this mean for the business?

### 1. Revenue Concentration Risk

A small group of customers generates a large portion of total revenue. Protecting these relationships is essential for revenue stability.

### 2. Strong Q4 Dependence

The business relies heavily on holiday season demand. While this is expected for a gift retailer, it creates seasonal volatility.

### 3. Operational Adjustments Can Distort Metrics

Large operational reversals can significantly affect return rate metrics. Without investigation, these could easily be misinterpreted as customer dissatisfaction.

### 4. Seasonal Products Require Careful Inventory Planning

Seasonal items drive revenue but also carry higher return rates and shorter sales windows.

---

## Skills Demonstrated

- SQL data cleaning and validation
- Investigating anomalies in transactional data
- Revenue trend analysis
- Customer revenue concentration analysis (Pareto analysis)
- Product performance analysis
- Return behaviour investigation
- Writing reproducible SQL analysis workflows
- Translating SQL results into business insights

---

## Tools Used

- MySQL
- SQL (CTEs, Aggregation, Window Functions)
- MySQL Workbench
- GitHub (project documentation)

---

## Reproducibility

To run this project:

1. Download the dataset from the UCI repository or Kaggle
2. Import the dataset into MySQL
3. Execute the SQL scripts in the `sql/` folder in order
4. Review insights in the `insights/` folder

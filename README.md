# 💳 Credit Card Analytics Dashboard  
### Power BI + SQL Project

An interactive **Credit Card Transaction and Customer Analytics Dashboard** built using **Power BI and MySQL** to analyze customer behavior, spending patterns, and revenue trends.

This project demonstrates an **end-to-end data analysis workflow** from:
SQL Database → Data Cleaning → Data Modeling → Dashboard → Business Insights

---

## 📊 Dashboard Overview

This project includes two dashboards:

### 1️⃣ Credit Card Transaction Report
Features:
- Total Revenue
- Total Interest Earned
- Transaction Amount
- Transaction Count
- Revenue by Card Category
- Revenue by Expenditure Type
- Revenue by Education Level
- Revenue by Customer Job
- Transaction Mode Analysis

---

### 2️⃣ Credit Card Customer Report
Features:
- Revenue by Age Group
- Weekly Revenue Trend
- Income Group Analysis
- Dependent Count
- Marital Status
- Education Level
- Top Performing States

---

## 🎯 Project Objective

The goal of this project is to:
- Analyze credit card transactions
- Identify high-value customer segments
- Understand spending behavior
- Track revenue and interest trends
- Generate actionable business insights

---

## 🛠 Tools & Technologies Used

- Power BI
- MySQL
- Power Query
- DAX
- Excel / CSV Dataset

---

## 🔄 Project Workflow (Step-by-Step)

### Step 1: Data Collection
- Downloaded dataset in CSV format
- Verified column structure and data quality

Dataset includes:
- Customer demographics
- Transaction amount
- Card category
- Education level
- Income group
- Transaction mode
- Weekly revenue

---

### Step 2: SQL Database Creation

Imported dataset into MySQL using:

```sql
LOAD DATA LOCAL INFILE 'credit_card.csv'
INTO TABLE credit_card
FIELDS TERMINATED BY ','
IGNORE 1 ROWS;

## Step 2: SQL Analysis

Performed:
- Data validation  
- Record count verification  
- Basic SQL queries for analysis  

### Example Queries

```sql
SELECT COUNT(*) FROM credit_card;

SELECT card_category, SUM(revenue)
FROM credit_card
GROUP BY card_category;





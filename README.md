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

~~~sql
LOAD DATA LOCAL INFILE 'credit_card.csv'
INTO TABLE credit_card
FIELDS TERMINATED BY ','
IGNORE 1 ROWS;
~~~

## Step 2: SQL Analysis

Performed:
- Data validation  
- Record count verification  
- Basic SQL queries for analysis  

### Queries

~~~sql
SELECT COUNT(*) FROM credit_card;

SELECT card_category, SUM(revenue)
FROM credit_card
GROUP BY card_category;
~~~

## Step 3: Connecting SQL to Power BI

**Steps:**

- Open Power BI Desktop  
- Click Get Data  
- Select MySQL Database  
- Enter server and database name  
- Load tables into Power BI  

---

## Step 4: Data Cleaning (Power Query)

**Performed:**

- Changed data types  
- Removed null values  
- Renamed columns  
- Verified duplicates  

---

## Step 5: Data Modeling

Created relationships between tables and ensured:

- One-to-many relationships  
- Proper filtering direction  

## Step 6: Creating DAX Measures

### Age Group
~~~DAX
AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown"
)
~~~ 

### Income_Group
~~~DAX
IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown"
)
~~~

### Weeknum2
~~~Dax
week_num2 = WEEKNUM('public cc_detail'[week_start_date]
~~~

### Revenue
~~~Dax
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
~~~

### Current_Week_Reveneue
~~~Dax
Current_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))) 
~~~

###  Previous_week_Reveneue
~~~Dax
Previous_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))
~~~
---

## Step 7: Dashboard Design

**Created:**

- KPI Cards
- Bar Charts
- Line Charts
- Tables
- Slicers (Quarter, Gender, Card Type, Income Group)

**Focused on:**
- Clean layout
- Consistent colors
- Interactive filters

## 📈 Key Insights

- Blue card customers generate the highest revenue
- Business professionals are top contributors
- Middle-aged customers spend the most
- Swipe transactions dominate over online payments
- Bills and entertainment are top spending categories
- High-income customers contribute the highest revenue

## 🚀 Business Recommendations
- Promote premium card upgrades
- Increase digital transaction incentives
- Target high-value customer segments
- Improve customer satisfaction initiatives

## 📚 Learning Outcomes
#### Through this project, I learned:

- SQL data handling and queries
- Connecting SQL to Power BI
- Data cleaning using Power Query
- Writing DAX measures
- Dashboard storytelling
- Business insight generation

## 📷 Dashboard Screenshots

### Credit Card Customer Dashboard
[View Customer Dashboard (PDF)](https://github.com/Yogi7557/Credit_Card_Transaction_-_Customer_PowerBI_Dashboard/blob/main/Credit_Card_Customer_PowerBI_DashBoard.pdf)

### Credit Card Transaction Dashboard
[View Transaction Dashboard (PDF)](https://github.com/Yogi7557/Credit_Card_Transaction_-_Customer_PowerBI_Dashboard/blob/main/Credit_Card_Transaction_PowerBI_Dashboard.pdf)

---

## 👨‍💻 Author

**Yoginder Kumar**
**Aspiring Data Analyst**

### Skills:

- Power BI
- SQL
- Python
- Excel

## ⭐ Support

**If you like this project, give it a ⭐ on GitHub!**






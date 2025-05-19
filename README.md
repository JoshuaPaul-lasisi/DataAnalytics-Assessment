# DataAnalytics Assessment

This repository contains optimized MySQL scripts that solve a set of real-world data analyst assessment questions. Each solution is designed to extract actionable insights from customer and transaction data using efficient SQL queries with clear documentation and best practices.

---

## Problem Overview

The assessment focuses on customer segmentation, behavioral analytics, and business intelligence reporting based on savings and investment plans. Key business questions include:

1. **Identifying high-value customers with diverse financial product engagement**
2. **Categorizing customers by transaction frequency**
3. **Flagging inactive accounts for potential re-engagement**
4. **Estimating Customer Lifetime Value (CLV)**

---

## Solution Summary

### **1. High-Value Customers with Multiple Products**

Identifies users who have both **savings** and **investment** plans and ranks them by total confirmed deposits.

* Filters only active (non-deleted) and funded plans
* Ensures customers have at least one savings and one investment product
* Uses aggregation and joins across multiple tables

### **2. Transaction Frequency Analysis**

Segments customers into **High**, **Medium**, or **Low** frequency users based on their average monthly transaction volume.

* Handles new users with zero-month tenure
* Uses `TIMESTAMPDIFF()` for tenure calculations
* Prevents division by zero with `CASE` logic

### **3. Account Inactivity Alert**

Flags both savings and investment accounts with **no transactions in the past 365 days** or **no transactions at all**.

* Uses `DATEDIFF()` and `MAX(created_on)` for activity checks
* Filters out deleted and archived plans

### **4. Customer Lifetime Value (CLV) Estimation**

Estimates CLV using this formula:

> CLV = (Transactions per month) × 12 × (Avg. Transaction Value × 0.1%)

* Converts transaction values from kobo to Naira
* Excludes customers with zero tenure
* Uses rounding and null-safe calculations

---

## Technical Highlights

* **Environment**: MySQL
* **Schema**: `adashi_staging`
* **Functions Used**: `TIMESTAMPDIFF()`, `DATEDIFF()`, `NOW()`, `CASE`, `NULLIF()`
* **Error Handling**: Division-by-zero safeguards, `NULL` checks
* **Readability**: Inline comments and consistent formatting for clarity
* **Performance**: Optimized joins and use of `GROUP BY` to support scalability

---

## File Structure

All queries are consolidated in one SQL file with section headers:

```
DataAnalytics-Assessment/
│
├── Assessment_Q1.sql # High-Value Customers with Multiple Products
├── Assessment_Q2.sql # Transaction Frequency Analysis
├── Assessment_Q3.sql # Account Inactivity Alert
├── Assessment_Q4.sql # Customer Lifetime Value Estimation
│
└── README.md # Project documentation
```

Each query is reusable, production-ready, and tested in a sandboxed staging environment.

---

## Author Note

This assessment demonstrates practical skills in writing performant, readable SQL for customer analytics and retention-focused use cases. Every query is built with care to reflect real business needs and handle edge cases gracefully.

If you'd like to collaborate, hire, or learn more about the thought process behind these queries, feel free to connect!
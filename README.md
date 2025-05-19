# DataAnalytics-Assessment

## Overview

This repository contains solutions to the SQL proficiency assessment that evaluates SQL querying, data transformation, and problem-solving skills using a transactional database.

---

## Repository Structure
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

---

## Solutions Overview

### Question 1: High-Value Customers with Multiple Products

**Objective:**  
Identify customers who have both at least one funded savings plan and one funded investment plan.

**Approach:**  

- Joined customer data with plan and savings tables  
- Filtered for funded savings and investment plans (`is_regular_savings = 1`, `is_a_fund = 1`)  
- Counted product types and summed deposits  
- Ordered by total deposits in descending order

**Key Insights:**  

- Identifies cross-selling opportunities by highlighting multi-product users  
- Helps the business focus on high-value, multi-engaged customers  

---

### Question 2: Transaction Frequency Analysis

**Objective:**  
Categorize customers by average monthly transaction frequency into High, Medium, or Low frequency tiers.

**Approach:**  

- Aggregated total transactions by customer  
- Computed average transactions per month  
- Applied frequency tier classification:
  - High (≥10/month)
  - Medium (3–9/month)
  - Low (≤2/month)  
- Counted number of customers in each group  

**Key Insights:**  

- Enables customer segmentation for targeted engagement  
- Distinguishes active users from dormant or occasional transactors  

---

### Question 3: Account Inactivity Alert

**Objective:**  
Detect active accounts (savings or investment) with no inflow transactions in the past 365 days.

**Approach:**  

- Identified most recent transaction per account  
- Calculated days since last transaction using the current date  
- Filtered for active accounts with inactivity over a year

**Key Insights:**  

- Supports reactivation campaigns and customer follow-ups  
- Flags potentially abandoned accounts for review  

---

### Question 4: Customer Lifetime Value Estimation

**Objective:**  
Estimate customer lifetime value (CLV) using a simplified model based on tenure and transaction behavior.

**Approach:**  

- Calculated account tenure in months since signup  
- Counted total transactions per customer  
- Estimated CLV using the formula:  
  `CLV = (total_transactions / tenure_months) * 12 * avg_profit_per_transaction`  
  with `avg_profit_per_transaction = 0.001 * average transaction value`  
- Ordered customers by estimated CLV descending  

**Key Insights:**  

- Provides a data-driven way to prioritize customer retention  
- Helps identify the most valuable long-term customers  

---

## Challenges Faced

1. **Schema Interpretation** – Interpreted relationships and logic from the table and column names with minimal documentation.
2. **Currency Handling** – Ensured all amount fields stored in kobo were correctly converted to naira.
3. **Edge Cases** – Managed null values, zero-tenure divisions, and sparse transaction records.
4. **Performance Considerations** – Wrote queries with efficient joins and minimal nesting to scale well on large datasets.

---

## Technical Considerations

- SQL queries follow consistent formatting and indentation  
- Inline comments explain non-obvious logic or transformations  
- Null values, currency conversion, and zero-divisions are handled gracefully  
- Queries assume compatibility with standard MySQL syntax  

---

## Assumptions

- `is_regular_savings = 1` flags a valid savings plan  
- `is_a_fund = 1` flags an investment plan  
- `confirmed_amount` refers to deposit inflows  
- All amount fields are stored in kobo (divide by 100 for naira)  
- `is_deleted = 0` marks active (non-deleted) accounts  

---

## How to Use

1. Clone this repository  
2. Load the provided database and schema into MySQL  
3. Run each `.sql` script individually  
4. Verify outputs against expected results  

For questions, feedback, or collaboration, feel free to reach out.
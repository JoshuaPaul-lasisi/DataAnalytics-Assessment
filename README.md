# DataAnalytics-Assessment

## Overview

This repository contains solutions to the SQL proficiency assessment that evaluates SQL querying, data transformation, and problem-solving skills using a transactional database.

---

## Assessment Questions & Approach

### Q1: High-Value Customers with Multiple Products

**Goal:** Identify users with at least one savings and one investment plan with confirmed funding.
**Approach:** Use inner joins with filtering on `is_regular_savings` and `is_a_fund`, then aggregate counts and total deposits.

### Q2: Transaction Frequency Analysis

**Goal:** Categorize users based on monthly average transaction count.
**Approach:** Calculate transaction counts and customer tenure in months; classify into frequency categories using a `CASE` statement.

### Q3: Account Inactivity Alert

**Goal:** Flag active accounts with no transactions in over a year.
**Approach:** Use `MAX(created_at)` per account to get last transaction, then compute inactivity with `DATEDIFF`.

### Q4: Customer Lifetime Value Estimation

**Goal:** Estimate CLV based on transaction volume and account tenure.
**Approach:** Derive tenure from `date_joined`, compute transaction count and average value, then apply the given CLV formula.

---

## Challenges Faced

- **Date Handling:** Some queries required careful calculation of durations in months, which involved converting days to months using approximations.
- **Handling Division by Zero:** Needed to guard against divide-by-zero when tenure or transaction count was zero using `NULLIF`.
- **Precision & Currency:** All monetary values were in kobo, requiring division by 100 and careful rounding for clarity.
- **Data Assumptions:** Assumed `created_at` field exists in all tables for tracking time of transaction.

---

## Final Notes

- Queries are formatted for readability and performance.
- Output assumptions are based on expected fields and business context.
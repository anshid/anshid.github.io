---
layout: page
title: Personal Finance Data Automation
permalink: /projects/da-personal-finance/
---

## 1. Problem Statement
Maintaining subjective, unstructured personal financial data leads to poor analytical tracking and untraceable economic leaks. This project established a fully automated data pipeline that standardizes semi-structured user inputs from Google Forms into a deterministic, queryable Google Sheets dashboard, offering real-time insights into expenses, asset distributions, and temporal trends.

## 2. Data Ingestion Architecture
- **Collection Edge**: A conditional Google Form. Logic was implemented to branch the user interface conditionally—if "Expense" is selected, the form provides distinct categories versus if "Income" or "Savings" is selected.
- **Data Persistence**: Raw form entries dynamically append directly to a central repository.
- **Transformation Layer**: Raw inputs (often containing disparate or unassigned categories based on the conditional form logic) are normalized into a primary "Transactions" reference sheet engineered via nested ArrayFormulas to clean boolean fields and aggregate category columns.

## 3. Analytical Dashboard Features
Real-time filtering logic was established directly in the spreadsheet to create a pseudo-frontend dashboard:
- **Temporal Splicing**: Dynamic views switching between Today, Week-to-Date, Month-to-Date, or Custom Epoch ranges using dependent queries.
- **KPI Metrics**: Automatically resolving total expenses, income, net differential, throughput count, average daily burn rate, and max single expenditure.
- **Visual Implementations**:
  - Horizontal/Pie distributions for categorical expense volume.
  - Time-series graphing for daily and historical monthly trendlines.
  - Tabulated Top-N expense logs mapping specific large transactions.

## 4. Engineering Solutions & Issue Resolution
- **Circular Dependencies**: Designing overlapping date filters initially caused looping execution paths. This was resolved by creating independent query controllers passing variables into an isolated reporting engine.
- **Sparse Data Architectures**: Resolved `#N/A` and query failure issues triggered by null periods (e.g. weeks with zero logged savings or income) by heavily utilizing `IFERROR()` and zero-fill imputation logic.
- **Column Normalization**: Extracted three separately logged conditional categorical columns (from the form behavior) and utilized robust sorting arrays to compress them into a solitary feature category column for charting.

## 5. Future Improvements
- Migration from a raw Google Sheets Frontend tool to Google Data Studio (Looker) to handle advanced geospatial or highly nested chart rendering.
- Inject a forecasting algorithm using moving averages to predict endpoint monthly spend.

# RetailCo Decision Memo — Day 02

## Business Question
How should RetailCo organize sales data for reliable reporting and business decisions?

## Recommendation
Use a star schema with Transactions as the central fact table and Customers, Products, Stores, and Date as dimension tables. Connect Returns to Transactions using the appropriate transaction key after validating the source data.

## Rationale
- A clear fact-table grain helps prevent double counting.
- Shared dimensions support consistent comparisons across products, stores, customers, and time.
- A dedicated Date table enables year, quarter, and month analysis.
- Centralized DAX measures provide consistent KPI calculations.
- Return records require careful handling to avoid inaccurate return counts.

## Risks and Validation
The official RetailCo CSV files and their column names must be confirmed before finalizing the model. Validate key uniqueness, relationship cardinality, missing dates, unmatched IDs, and return-record grain. Reconcile sales and profit totals with the source data.

## Expected Business Value
A validated model will help RetailCo compare sales, profit, product performance, store performance, and returns consistently.

## Explicit Decision
Decision: Adopt the proposed star schema as the target design, subject to validation of the official RetailCo data, transaction grain, and relationship cardinalities before publishing the Power BI model.

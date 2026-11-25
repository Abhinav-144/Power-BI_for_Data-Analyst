# Dashboard Guide

## 1. Executive Overview
Purpose: provide a summary of the credit risk and fraud datasets.

Documented KPI cards:
- Total Loan Applications
- Default Rate
- Total Loan Amount
- Total Transactions
- Fraud Rate
- Fraud Transaction Amount

Documented visual themes:
- Loan status distribution
- Default rate by loan grade
- Transaction classification
- Fraud amount by transaction amount band

Credit and fraud slicers should remain separate.

## 2. Credit Risk Analysis
Purpose: explore observed loan default patterns.

Documented KPI cards:
- Total applications
- Defaulted loans
- Default rate
- Average loan amount

Documented breakdowns:
- Default rate by applicant age band
- Default rate by loan grade
- Default rate by loan purpose
- Default rate by employment length category
- Default rate by home ownership
- Average loan amount by grade

A detail table supports record-level review.

## 3. Loan Portfolio & Credit Profile
Purpose: describe the loan portfolio and applicant financial characteristics.

Documented KPIs:
- Total loan amount
- Average loan amount
- Average interest rate
- Average applicant income
- Average loan-to-income ratio

Documented visual themes:
- Loan amount distribution
- Interest rate distribution
- Loan-to-income ratio by grade
- Applicant income versus loan amount
- Loan amount by purpose
- Loan grade distribution

A what-if parameter provides an illustrative loan-amount increase scenario.

## 4. Fraud Intelligence
Purpose: explore observed fraud classifications and transaction patterns.

Documented KPIs:
- Total transactions
- Fraudulent transactions
- Fraud rate
- Fraud transaction amount
- Average fraud transaction amount

Documented visual themes:
- Transaction classification
- Fraud count by amount band
- Fraud amount by amount band
- Fraud rate by amount band
- Fraud by elapsed-hour interval

Elapsed time must not be interpreted as a calendar date or clock time.

## 5. Risk Investigation
Purpose: provide filterable detail views for credit and fraud records.

Use relevant slicers and carefully selected columns to narrow the displayed records. Do not imply that a credit record and a fraud record belong to the same customer.

## 6. Drill-through Pages
### Credit Drillthrough
Configured around `Loan_Grade`, with optional credit attributes such as `Loan_Purpose` and `Loan_Status_Category`.

### Fraud Drillthrough
Configured around `Fraud_Category`, with optional `Transaction_Amount_Band` and `Elapsed_Hours`.

For drill-through to work, the source visual must contain the same field from the same table as the target page’s drill-through field.

## 7. Report-page Tooltips
The project includes dedicated tooltip pages:
- Credit Risk Tooltip
- Fraud Tooltip

Apply the correct tooltip page to relevant visuals using the visual's Format settings.

# Banking Risk, Fraud & Credit Intelligence Platform

## Project Overview
An advanced Power BI portfolio project that analyzes two banking-risk domains:
1. **Credit risk** — loan applications, applicant profiles, loan characteristics, and observed default outcomes.
2. **Transaction fraud** — transaction amounts, fraud classifications, and patterns across elapsed transaction time.

The project uses two independent public datasets. They are intentionally modeled as separate fact tables because they do not share genuine customer, account, card, or transaction identifiers.

## Business Objectives
- Understand the composition of the loan application portfolio.
- Examine observed default rates across applicant and loan characteristics.
- Analyze loan amounts, interest rates, applicant income, and loan-to-income ratios.
- Measure the frequency and value of fraudulent transactions in the fraud dataset.
- Explore fraud patterns by transaction amount band and elapsed time.
- Present summary and investigation views for different analytical audiences.

## Tools
- Power BI Desktop
- Power Query
- DAX
- Power BI Service (personal publishing to My workspace, where available)
- GitHub for project versioning and portfolio presentation

## Report Pages
| Page | Purpose |
|---|---|
| Executive Overview | High-level KPIs from both independent datasets |
| Credit Risk Analysis | Loan application and default analysis |
| Loan Portfolio & Credit Profile | Loan amount, interest rate, income, and portfolio characteristics |
| Fraud Intelligence | Fraud classification, transaction amounts, and elapsed-time analysis |
| Risk Investigation | Filterable record-level views |
| Credit Drillthrough | Focused investigation by selected credit-risk attributes |
| Fraud Drillthrough | Focused investigation by fraud classification and transaction attributes |

## Key Modeling Decision
The model contains two independent tables:
- `Fact_Credit_Risk`
- `Fact_Fraud_Transactions`

No relationship is created between them. The datasets do not contain a reliable shared key, so joining them would create unsupported customer- or transaction-level associations.

## Repository Structure
```text
Banking_Risk_Fraud_Credit_Intelligence/
├── PowerBI/
│   └── Banking_Risk_Fraud_Credit_Intelligence.pbix
├── Screenshots/
├── Documentation/
│   ├── Project_Objective.md
│   ├── Data_Sources.md
│   ├── Data_Cleaning_and_Power_Query.md
│   ├── Data_Model_Overview.md
│   ├── DAX_Measures.md
│   ├── Dashboard_Guide.md
│   ├── Business_Insights.md
│   ├── Recommendations.md
│   ├── Limitations_and_Assumptions.md
│   ├── RLS_and_Security.md
│   └── Deployment_and_Performance.md
└── README.md
```

## How to Use
1. Download the `.pbix` file from the `PowerBI` folder.
2. Open it in Power BI Desktop.
3. If prompted, review data-source paths and refresh the data using your local dataset files.
4. Navigate through the report pages and use slicers, drill-through, and report-page tooltips.

## Important Interpretation Notes
- The credit dataset represents loan records/applications; it does not provide a true repayment schedule or installment history.
- The fraud dataset's `Time` field is elapsed seconds from the dataset's starting point, not a calendar date or clock time.
- The fraud dataset does not provide real customer, card, merchant, or geographic identifiers.
- `Transaction_ID` is a generated row index used for technical identification within this model; it is not a source-system transaction ID.
- The datasets are independent and should not be interpreted as a unified customer-level banking view.
- This is a retrospective analytical portfolio project, not a live fraud detection or default prediction system.

## Screenshots
Add exported screenshots of each report page to the `Screenshots` folder and embed selected images here when ready.

## Author
Add your name, portfolio URL, and LinkedIn URL here.

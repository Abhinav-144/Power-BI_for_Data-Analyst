# Limitations and Assumptions

## Dataset Limitations

### Credit Risk Dataset
- The dataset is a flat loan-record dataset.
- It does not contain a genuine repayment schedule or installment-level payment history.
- It does not support true repayment tracking, delinquency aging, or balance outstanding calculations.
- It does not provide a reliable common customer key for linking to the fraud dataset.
- The project treats `Loan_Status = 1` as default and `Loan_Status = 0` as non-default; validate this mapping if the source is replaced.

### Fraud Dataset
- The dataset contains anonymized features `V1`–`V28`.
- It does not provide real customer, card, merchant, or geographic identifiers.
- The `Time` field is elapsed seconds from the dataset start, not a calendar timestamp or clock time.
- `Transaction_ID` is a generated index, not a source-system identifier.
- The dataset is highly imbalanced between legitimate and fraudulent classes.

## Modeling Limitations
- The credit and fraud tables are independent.
- No relationship is created between them.
- No customer-level or account-level combined analysis is supported.
- A generated row index must not be treated as a natural business key.

## Analytical Limitations
- The report is descriptive and diagnostic.
- It does not predict future defaults or fraud.
- It does not perform real-time transaction monitoring or alerting.
- What-if loan amount analysis is an illustrative scenario, not a forecast.
- Observed associations do not establish causation.

## Security and Sharing
- RLS restricts rows for supported report consumers; it does not make public embedding safe.
- Publish to web is public. Do not use it for confidential or sensitive data, and do not expect it to enforce RLS.
- Power BI licensing and tenant settings affect sharing and deployment options.

## Assumptions to Validate
- Source field names and data types match the documentation.
- Category band boundaries match the final Power Query logic.
- Measure formatting and currency conventions are consistent.
- Report visuals and page names match the final PBIX.

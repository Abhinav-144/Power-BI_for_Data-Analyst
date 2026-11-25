# Data Model Overview

## Model Structure
The report uses two independent fact tables:

1. `Fact_Credit_Risk`
2. `Fact_Fraud_Transactions`

There are no relationships between these tables.

## Why the Tables Are Independent
The credit dataset and fraud dataset do not provide a genuine shared customer, account, card, or transaction key. Creating a relationship or joining records would imply a connection that the source data does not support.

## Table Responsibilities
### Fact_Credit_Risk
Contains loan/application attributes, applicant profile attributes, and the observed loan status.

### Fact_Fraud_Transactions
Contains transaction amount, elapsed transaction time, anonymized features, and fraud classification.

## Filter Design
Use credit-related slicers with credit visuals and fraud-related slicers with fraud visuals. Do not expect a slicer from one dataset to filter the other dataset.

## Model Validation Checklist
- Confirm both tables load successfully.
- Confirm there are no accidental relationships between the two fact tables.
- Confirm measures reference the correct table.
- Confirm slicers use fields from the appropriate table.
- Confirm drill-through fields come from the same source table as the corresponding source visual.

# Data Sources

## 1. Credit Risk Dataset
**Dataset:** Credit Risk Dataset  
**Publisher/creator:** laotse  
**Platform:** Kaggle  
**Dataset page:** https://www.kaggle.com/datasets/laotse/credit-risk-dataset

### Fields used
| Original field | Model field |
|---|---|
| `person_age` | `Applicant_Age` |
| `person_income` | `Applicant_Income` |
| `person_home_ownership` | `Home_Ownership` |
| `person_emp_length` | `Employment_Length` |
| `loan_intent` | `Loan_Purpose` |
| `loan_grade` | `Loan_Grade` |
| `loan_amnt` | `Loan_Amount` |
| `loan_int_rate` | `Interest_Rate` |
| `loan_status` | `Loan_Status` |
| `loan_percent_income` | `Loan_Income_Ratio` |
| `cb_person_default_on_file` | `Previous_Default` |
| `cb_person_cred_hist_length` | `Credit_History_Length` |

### Interpretation
Each row is treated as a loan application/loan record. `Loan_Status = 1` is treated as default and `Loan_Status = 0` as non-default, consistent with the project’s configured measures. Validate this mapping against the downloaded source file if replacing or updating the dataset.

## 2. Credit Card Fraud Dataset
**Dataset:** Credit Card Fraud Detection  
**Publisher/creator:** Machine Learning Group — ULB  
**Platform:** Kaggle  
**Dataset page:** https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

### Fields used
- `Time` renamed to `Transaction_Time`
- `Amount` renamed to `Transaction_Amount`
- `Class` renamed to `Fraud_Label`
- `V1` through `V28` retained as anonymized numerical features where needed

### Interpretation
`Fraud_Label = 1` represents a fraudulent transaction and `Fraud_Label = 0` represents a legitimate transaction. The source `Time` field is elapsed seconds from the beginning of the dataset, not a calendar timestamp.

## Data Handling
The datasets are loaded and analyzed independently. No customer, account, card, merchant, date, or geography relationship is inferred between them.

## Refresh Notes
The PBIX may require updated local file paths when opened on another computer. Keep the original source files in a clearly named data folder and update Power Query source paths before refreshing.

# DAX Measures

The following measures are part of the project’s documented measure set. Confirm table and column names match the final PBIX before pasting.

## Credit Risk Measures

```DAX
Total Loan Applications =
COUNTROWS('Fact_Credit_Risk')
```

```DAX
Defaulted Loans =
CALCULATE(
    [Total Loan Applications],
    'Fact_Credit_Risk'[Loan_Status] = 1
)
```

```DAX
Non-Defaulted Loans =
CALCULATE(
    [Total Loan Applications],
    'Fact_Credit_Risk'[Loan_Status] = 0
)
```

```DAX
Default Rate =
DIVIDE(
    [Defaulted Loans],
    [Total Loan Applications]
)
```

```DAX
Total Loan Amount =
SUM('Fact_Credit_Risk'[Loan_Amount])
```

```DAX
Average Loan Amount =
AVERAGE('Fact_Credit_Risk'[Loan_Amount])
```

```DAX
Average Applicant Income =
AVERAGE('Fact_Credit_Risk'[Applicant_Income])
```

```DAX
Average Interest Rate =
AVERAGE('Fact_Credit_Risk'[Interest_Rate])
```

```DAX
Average Loan Income Ratio =
AVERAGE('Fact_Credit_Risk'[Loan_Income_Ratio])
```

```DAX
Default Rate Rank =
RANKX(
    ALL('Fact_Credit_Risk'[Loan_Grade]),
    [Default Rate],
    ,
    DESC,
    DENSE
)
```

```DAX
Loan Applications % of Total =
DIVIDE(
    [Total Loan Applications],
    CALCULATE(
        [Total Loan Applications],
        ALL('Fact_Credit_Risk')
    )
)
```

```DAX
Loan Amount % of Total =
DIVIDE(
    [Total Loan Amount],
    CALCULATE(
        [Total Loan Amount],
        ALL('Fact_Credit_Risk')
    )
)
```

```DAX
High Risk Loan Applications =
CALCULATE(
    [Total Loan Applications],
    'Fact_Credit_Risk'[Loan_Grade] IN {"D", "E", "F", "G"}
)
```

```DAX
High Risk Loan Application % =
DIVIDE(
    [High Risk Loan Applications],
    [Total Loan Applications]
)
```

## Fraud Measures

```DAX
Total Transactions =
COUNTROWS('Fact_Fraud_Transactions')
```

```DAX
Fraudulent Transactions =
CALCULATE(
    [Total Transactions],
    'Fact_Fraud_Transactions'[Fraud_Label] = 1
)
```

```DAX
Legitimate Transactions =
CALCULATE(
    [Total Transactions],
    'Fact_Fraud_Transactions'[Fraud_Label] = 0
)
```

```DAX
Fraud Rate =
DIVIDE(
    [Fraudulent Transactions],
    [Total Transactions]
)
```

```DAX
Total Transaction Amount =
SUM('Fact_Fraud_Transactions'[Transaction_Amount])
```

```DAX
Fraud Transaction Amount =
CALCULATE(
    [Total Transaction Amount],
    'Fact_Fraud_Transactions'[Fraud_Label] = 1
)
```

```DAX
Legitimate Transaction Amount =
CALCULATE(
    [Total Transaction Amount],
    'Fact_Fraud_Transactions'[Fraud_Label] = 0
)
```

```DAX
Average Fraud Transaction Amount =
CALCULATE(
    AVERAGE('Fact_Fraud_Transactions'[Transaction_Amount]),
    'Fact_Fraud_Transactions'[Fraud_Label] = 1
)
```

```DAX
Fraud Amount Share =
DIVIDE(
    [Fraud Transaction Amount],
    [Total Transaction Amount]
)
```

## What-if Scenario Measures

The project includes a numeric parameter named `Loan Amount Increase %` with a configured range of 0–50, increment 5, and default 10.

```DAX
Scenario Loan Amount =
[Total Loan Amount] *
(
    1 +
    DIVIDE(
        SELECTEDVALUE(
            'Loan Amount Increase %'[Loan Amount Increase %],
            10
        ),
        100
    )
)
```

```DAX
Scenario Loan Amount Difference =
[Scenario Loan Amount] - [Total Loan Amount]
```

```DAX
Scenario Loan Income Ratio =
DIVIDE(
    [Scenario Loan Amount],
    SUM('Fact_Credit_Risk'[Applicant_Income])
)
```

## Formatting Guidance
- Counts: whole number, `#,##0`.
- Default Rate and Fraud Rate: percentage, 2 decimal places.
- Loan and transaction amounts: currency, using the selected report currency consistently.
- `Interest_Rate` is stored as percentage points (for example, 11.5 means 11.5). Do not apply percentage formatting directly unless the stored values are converted to decimal form.
- `Loan_Income_Ratio` is decimal (for example, 0.25 means 25%); percentage formatting is appropriate.

## Interpretation
The what-if measures are illustrative arithmetic scenarios. They do not update source data, forecast defaults, or predict future portfolio performance.

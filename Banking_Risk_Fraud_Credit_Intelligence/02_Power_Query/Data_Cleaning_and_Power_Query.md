# Data Cleaning and Power Query Transformations

## Credit Risk Table
The credit dataset is loaded into Power Query and renamed to `Fact_Credit_Risk`.

### Column Renaming
See `Data_Sources.md` for the original-to-model field mapping.

### Data Types
Review and assign appropriate data types:
- Applicant age, employment length, credit history length, loan amount, and status: numeric types as appropriate.
- Applicant income, interest rate, and loan-to-income ratio: numeric types.
- Purpose, grade, ownership, and previous-default indicator: text/categorical types.

### Derived Categories
The project includes these derived fields:
- `Employment_Length_Category`: Unknown, Less than 1 Year, 1–5 Years, 6–10 Years, 10+ Years.
- `Interest_Rate_Category`: Unknown, Very Low, Low, Moderate, High, Very High.
- `Age_Band`: 18-25, 26-35, 36-45, 46-55, 56+.
- `Loan_Amount_Band`: Below 5K, 5K-10K, 10K-15K, 15K-20K, 20K+.
- `Loan_Status_Category`: Default, Non-Default, Unknown.

Check the actual Power Query conditional boundaries in the PBIX before changing category definitions.

## Fraud Transactions Table
The fraud dataset is loaded into Power Query and renamed to `Fact_Fraud_Transactions`.

### Column Renaming
- `Time` → `Transaction_Time`
- `Amount` → `Transaction_Amount`
- `Class` → `Fraud_Label`

### Derived Fields
- `Fraud_Category`: Fraudulent for label 1, Legitimate for label 0, otherwise Unknown.
- `Transaction_Amount_Band`: Below 25, 25-99.99, 100-499.99, 500-999.99, 1000+.
- `Elapsed_Hours`: integer hour interval derived from elapsed seconds (`Transaction_Time` divided by 3600).
- `Transaction_ID`: generated index for technical row identification.

## Quality Checks
Before loading:
1. Confirm numeric columns have valid numeric types.
2. Check for nulls and errors in key analytical fields.
3. Confirm category labels are populated as expected.
4. Check row counts against the downloaded source files.
5. Confirm the fraud label contains the expected classification values.
6. Ensure the generated index is unique within the loaded table.

## Important
The generated `Transaction_ID` is not an original source identifier. `Elapsed_Hours` is not a clock hour. Do not describe either as a real-world transaction ID or time-of-day field.

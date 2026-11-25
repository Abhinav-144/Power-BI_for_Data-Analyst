# Data Cleaning Steps

## Purpose
Document the Power Query cleaning process used for the `Employee` table in the HR Workforce & Attrition Analytics report.

> Update this document if your actual Power Query Applied Steps differ from the steps below. It is a project record, not an automatic export of Power Query history.

## Recommended / performed checks to verify

1. **Import the CSV**
   - Load the HR attrition CSV into Power BI Desktop using **Home → Get data → Text/CSV**.
   - Open **Transform data** to enter Power Query Editor.
   - Query name used in the project: `Employee`.

2. **Review column names and data types**
   - Numeric fields such as `Age`, `EmployeeNumber`, `MonthlyIncome`, and `YearsAtCompany` should be numeric.
   - Categorical fields such as `Department`, `JobRole`, `Gender`, `OverTime`, and `Attrition` should be text.
   - Confirm that ratings are numeric whole numbers.

3. **Check data quality**
   - Use **View → Column quality**, **Column distribution**, and **Column profile**.
   - Review errors, nulls, unexpected categories, and duplicates.
   - Verify `EmployeeNumber` is unique before treating it as an employee identifier.

4. **Remove constant columns**
   - The commonly distributed dataset contains `EmployeeCount`, `Over18`, and `StandardHours`, which have constant values.
   - Remove these only after confirming they are constant in the loaded data.

5. **Rename columns for readability (if applied)**
   - `EmployeeNumber` → `Employee ID`
   - `MonthlyIncome` → `Monthly Income`
   - `PercentSalaryHike` → `Salary Hike %`
   - `YearsAtCompany` → `Years at Company`
   - `YearsInCurrentRole` → `Years in Current Role`
   - `YearsSinceLastPromotion` → `Years Since Last Promotion`
   - `YearsWithCurrManager` → `Years With Current Manager`
   - Keep the names used by your actual model consistent with DAX measures.

6. **Create Age Group**
   - 18–25
   - 26–30
   - 31–35
   - 36–40
   - 41–50
   - 51+
   - Ensure the conditions are mutually exclusive and outputs are text.

7. **Create Tenure Group**
   - 0–2 Years
   - 3–5 Years
   - 6–10 Years
   - 11–15 Years
   - 16+ Years
   - Base the grouping on `YearsAtCompany` / `Years at Company`, not a date field.

8. **Create sort columns (if used)**
   - Age Group Sort: 1 through 6 in the same order listed above.
   - Tenure Group Sort: 1 through 5 in the same order listed above.
   - In Power BI, select the group column and use **Column tools → Sort by column**.
   - Confirm each group has a single matching sort value before applying.

9. **Apply changes**
   - Select **Close & Apply**.
   - Verify that the model and visuals still work after transformations.

## Final validation
- Compare row count with the source file.
- Check employee ID uniqueness.
- Confirm that group columns contain text labels, not dates or errors.
- Confirm category sort order in the charts.
- Do not add a Hire Date unless the source contains a genuine hire date.

# Power Query Transformations

## Query
Main query: `Employee`

## Transformation summary
The project uses Power Query to prepare employee-level data for reporting. Confirm each item against the query's **Applied Steps** before treating it as completed.

| Transformation | Purpose |
|---|---|
| Import CSV | Bring the source dataset into Power BI |
| Set data types | Ensure numeric, text, and rating fields use appropriate types |
| Profile columns | Identify missing values, errors, unexpected categories, and duplicates |
| Remove constant fields | Remove fields such as `EmployeeCount`, `Over18`, or `StandardHours` only after confirming they are constant |
| Rename columns | Make field names easier to understand and use consistently in visuals and DAX |
| Create Age Group | Group ages into six readable categories |
| Create Tenure Group | Group years at company into five tenure bands |
| Create sort columns | Keep age and tenure categories in logical order |
| Close & Apply | Load the transformed table into the Power BI model |

## Age Group logic
Use ordered conditions so each age falls into exactly one group:
- Age <= 25: `18-25`
- Age <= 30: `26-30`
- Age <= 35: `31-35`
- Age <= 40: `36-40`
- Age <= 50: `41-50`
- Else: `51+`

This assumes the dataset's minimum age is at least 18. If that is not true for your source, adjust the first label and condition.

## Tenure Group logic
- Years at Company <= 2: `0-2 Years`
- Years at Company <= 5: `3-5 Years`
- Years at Company <= 10: `6-10 Years`
- Years at Company <= 15: `11-15 Years`
- Else: `16+ Years`

## Sort order
Age Group Sort:
1. 18-25
2. 26-30
3. 31-35
4. 36-40
5. 41-50
6. 51+

Tenure Group Sort:
1. 0-2 Years
2. 3-5 Years
3. 6-10 Years
4. 11-15 Years
5. 16+ Years

## Important
Power Query Applied Steps are the source of truth for what was actually performed. Update this file if your final model uses different field names or grouping rules.

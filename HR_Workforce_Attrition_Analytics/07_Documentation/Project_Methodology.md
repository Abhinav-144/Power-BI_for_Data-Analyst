# Project Methodology

## 1. Dataset selection
Selected an HR employee attrition dataset with demographic, job, compensation, satisfaction, performance, and attrition fields. Confirm the exact source and license in `01_Raw_Data/Dataset_Source.txt`.

## 2. Data preparation
Loaded the CSV into Power Query. Reviewed data types, column quality, duplicates, and constant fields. Created Age Group and Tenure Group categories and sort columns where needed. Consult `02_Power_Query` for the documented process; verify it against the final Applied Steps.

## 3. Data model
Used the `Employee` table as the main employee-level table. A single-table model is sufficient for the current report if all fields and measures are sourced from it. See `03_Data_Model/Data_Model_Overview.md`.

## 4. DAX and calculations
Created measures for employee counts, exits, active employees, attrition rate, average age, income, tenure, and satisfaction/performance ratings. Verify measure definitions in the PBIX and document the exact final formulas in `04_DAX_Measures`.

## 5. Visualization
Built report pages for:
1. HR Executive Overview
2. Workforce Analysis
3. Attrition Analysis
4. Employee Satisfaction & Performance
5. Employee Details
6. Business Insights

## 6. Interactivity
Added slicers and configured employee-level drill-through to the Employee Details page. Test the report with slicers cleared and with individual employee selections.

## 7. Insight development
Compared attrition rates and counts across departments, job roles, age groups, overtime status, and job satisfaction levels. Reviewed work-life balance and department-level satisfaction measures.

## 8. Validation
Check overall totals, percentages, sort order, slicer interactions, drill-through behavior, and text readability. The displayed results are descriptive associations and do not prove causation.

## 9. Publication
Capture screenshots, write the README, review dataset attribution and license, and upload only files permitted for redistribution.

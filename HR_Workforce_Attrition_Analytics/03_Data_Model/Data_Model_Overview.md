# Data Model Overview

## Model purpose
The report analyses an employee-level HR attrition dataset. The current report is built around the `Employee` table.

## Current model approach
For this dataset, a single employee table can support the five analytical report pages without requiring relationships to other tables, provided all required fields are present in that table.

```text
                 Employee
                    |
                    +-- Demographics
                    +-- Department / Job Role / Job Level
                    +-- Income and career tenure
                    +-- Satisfaction and performance
                    +-- Overtime and business travel
                    +-- Attrition
                    +-- Age Group / Tenure Group
```

## Employee identifier
Use `Employee ID` (or the original `EmployeeNumber`) as the employee-level identifier. Verify uniqueness in Power Query before relying on it as a unique key.

## Main fields used
- Identity: Employee ID, Age, Gender, Marital Status
- Organization: Department, Job Role, Job Level
- Compensation: Monthly Income, Salary Hike %
- Employment: Years at Company, Years in Current Role, Years Since Last Promotion
- Work: OverTime, Business Travel
- Experience: Job Satisfaction, Environment Satisfaction, Work-Life Balance, Performance Rating
- Outcome: Attrition
- Derived groups: Age Group, Tenure Group

## Relationships
No relationships are required for a single-table model. If you add a separate date or dimension table later, document the relationship cardinality, filter direction, and reason for the relationship here.

## Measure definitions
See the measures created in Power BI and document them in `04_DAX_Measures`. The report's totals and rates should be validated against the actual model before publication.

## Data limitations
- The commonly distributed dataset is a snapshot-style employee dataset, not a dated employee movement history.
- Do not create time-based hire or attrition trends unless the necessary date fields exist.
- Observed associations should not be described as proof of causation.

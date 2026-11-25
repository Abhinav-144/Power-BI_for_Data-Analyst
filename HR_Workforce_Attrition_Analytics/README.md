# HR Workforce & Attrition Analytics

An interactive HR analytics report built with Microsoft Power BI Desktop using an IBM HR Analytics Employee Attrition & Performance-style dataset.

## Project overview
The report explores workforce composition, compensation, tenure, employee attrition, satisfaction, and performance. It includes five analytical pages and a Business Insights page.

## Report pages
1. **HR Executive Overview** — workforce KPIs and high-level distribution.
2. **Workforce Analysis** — job roles, job levels, income, and tenure.
3. **Attrition Analysis** — attrition rates by department, job role, age group, overtime, and tenure where included.
4. **Employee Satisfaction & Performance** — satisfaction ratings, work-life balance, and performance.
5. **Employee Details** — employee-level table and drill-through.
6. **Business Insights** — findings and recommendations based on the report.

## Tools and techniques
- Power BI Desktop
- Power Query for data preparation
- DAX measures for employee counts, exits, attrition rate, and averages
- Interactive slicers, visual interactions, and drill-through
- Data-driven business insight documentation

## Dataset
The commonly distributed dataset is named `WA_Fn-UseC_-HR-Employee-Attrition.csv` and is commonly available through the Kaggle dataset page:
https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset

Confirm that this is the exact source used and review its current license before redistributing the CSV. Do not describe this dataset as actual IBM employee records. The standard version does not contain a genuine Hire Date.

## Key results shown in the report
The current screenshots show:
- Total employees: 1,470
- Exited employees: 237
- Overall attrition rate: 16.12%
- Sales department attrition: 20.63%
- Sales Representative attrition: 39.76%
- Overtime Yes attrition: 30.53%; Overtime No: 10.44%

Recheck all figures against the final PBIX before publication. These are descriptive patterns and do not prove causation.

## Repository structure
```text
01_Raw_Data/       Dataset and source attribution
02_Power_Query/    Cleaning and transformation documentation
03_Data_Model/     Model overview, dictionary, relationship diagram
04_DAX_Measures/   DAX measure files
05_Dashboards/     PBIX, screenshots, optional PDF
06_Insights/       Business findings and recommendations
07_Documentation/  Objective, methodology, demonstrated skills
```

## How to view
Open `05_Dashboards/HR_Workforce_Attrition_Analytics.pbix` in Power BI Desktop. If the PBIX file is not included in this repository, add your local file before publishing or provide an appropriate report link.

## Limitations
- Results depend on the exact dataset version and final measure definitions.
- This is an employee snapshot-style dataset, not necessarily a time-series history.
- Associations between attributes and attrition do not establish causation.
- No genuine hire date should be inferred if it is absent from the source.

## License
See the dataset's source terms. Add a repository license only for material you have the right to license; do not apply an open-source license to third-party data without permission.

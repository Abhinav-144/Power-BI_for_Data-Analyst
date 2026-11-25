# Deployment and Performance

## Local Project
- Save the final Power BI Desktop report as a `.pbix` file.
- Keep source data files in a documented folder.
- When moving the project to another computer, update Power Query source paths as required.
- Verify the report after refresh.

## Power BI Service
With Power BI Free, publishing to **My workspace** is generally suitable for personal use, subject to account and tenant availability. Sharing and public embedding have separate licensing and tenant requirements.

Do not assume that a Free account can generate a Publish to web embed code. Check the current options available in the account. Publish to web makes content publicly accessible and must not be used for confidential data.

## Performance Analyzer
Use **View → Performance Analyzer** in Power BI Desktop:
1. Start recording.
2. Refresh visuals.
3. Interact with slicers.
4. Expand visual timings.
5. Identify visuals with relatively high DAX query or visual display time.
6. Optimize and repeat the test.

Record actual results below.

| Report page | Initial observation | Change made | Retest observation |
|---|---|---|---|
| Executive Overview | [Record] | [Record] | [Record] |
| Credit Risk Analysis | [Record] | [Record] | [Record] |
| Loan Portfolio & Credit Profile | [Record] | [Record] | [Record] |
| Fraud Intelligence | [Record] | [Record] | [Record] |
| Risk Investigation | [Record] | [Record] | [Record] |

## Optimization Checklist
- Remove unused columns only after confirming they are not needed for analysis.
- Avoid unnecessary high-cardinality fields in visuals.
- Keep detailed tables focused on relevant columns.
- Avoid excessive visuals on a single page.
- Prefer measures for aggregations such as totals, averages, and percentages.
- Keep the two fact tables independent.
- Re-test after making changes.

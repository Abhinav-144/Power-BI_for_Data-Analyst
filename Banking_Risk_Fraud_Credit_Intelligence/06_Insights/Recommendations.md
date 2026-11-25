# Business Recommendations

The recommendations below are analytical prompts. Retain, edit, or remove them based on the actual patterns confirmed in `Business_Insights.md`.

## Credit Risk
1. **Review higher-default segments:** If the report identifies loan grades or applicant segments with higher observed default rates, investigate underwriting criteria and segment characteristics.
2. **Assess affordability indicators:** Review loan-to-income ratio patterns alongside applicant income and loan amount. Treat these as descriptive indicators, not proof of repayment capacity.
3. **Monitor portfolio composition:** Review loan purpose, grade, and amount distribution to understand where the application portfolio is concentrated.
4. **Validate data and policy context:** Compare findings with additional repayment, delinquency, and borrower-history data before changing credit policy.

## Fraud Analytics
1. **Prioritize observed high-risk patterns:** If certain amount bands or elapsed-time intervals show higher fraud concentration, use them as candidates for further investigation.
2. **Account for class imbalance:** Fraudulent records are a small minority in this dataset. Review counts and rates together and avoid relying on accuracy alone in any future predictive model.
3. **Investigate with richer source data:** Real fraud operations require reliable transaction timestamps, customer/account identifiers, merchant context, and investigation outcomes.
4. **Avoid live-alert claims:** This Power BI report is retrospective and does not monitor transactions in real time.

## Reporting and Governance
- Keep credit and fraud analyses separate unless a future source provides a validated common key.
- Refresh source data using controlled, documented processes.
- Review RLS assignments before sharing reports with other users.
- Do not expose confidential or personally identifiable data through public embedding.

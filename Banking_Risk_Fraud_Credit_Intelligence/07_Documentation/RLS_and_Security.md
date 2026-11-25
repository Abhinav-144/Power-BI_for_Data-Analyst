# Row-Level Security and Report Security

## Configured Roles
The project design includes these roles:

| Role | Credit table filter | Fraud table filter | Intended view |
|---|---|---|---|
| `Credit_Risk_Analyst` | `TRUE()` | `FALSE()` | Credit risk records only |
| `Fraud_Analyst` | `FALSE()` | `TRUE()` | Fraud transaction records only |
| `Executive` | `TRUE()` | `TRUE()` | Both datasets |

These are table-level row filters configured in Power BI Desktop. Confirm the exact role definitions in the PBIX before deployment.

## Testing in Desktop
1. Open **Modeling → Manage roles** to review role filters.
2. Use **Modeling → View as**.
3. Test each role.
4. Confirm the appropriate table's visuals are filtered or blank as intended.

## Power BI Service
After publishing, role membership is managed on the semantic model's Security page, subject to the capabilities and licensing of the account and workspace.

## Important Security Notes
- RLS is not a substitute for workspace permissions.
- Workspace Admin, Member, and Contributor roles generally have edit-level access and are not appropriate for testing consumer-level RLS restrictions. Test with a Viewer or an appropriate test account.
- Publish to web is public and does not enforce RLS. Never use it to expose confidential information.
- Do not place credentials, access tokens, or personal data in the PBIX, screenshots, README, or public repository.

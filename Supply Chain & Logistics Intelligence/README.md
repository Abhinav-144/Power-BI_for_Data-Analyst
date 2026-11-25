# Supply Chain & Logistics Intelligence — Power BI Project

## Project Overview

**Supply Chain & Logistics Intelligence** is an interactive Power BI analytics project built using the **DataCo Smart Supply Chain dataset**. The project explores order activity, sales performance, shipping operations, delivery risk, product categories, and geographic performance.

The objective is to transform raw supply-chain records into a dimensional data model and interactive reports that help users examine operational performance and identify areas that may require further investigation.

## Business Objectives

- Monitor order volume and sales performance.
- Examine delivery-risk patterns and shipping delays.
- Compare performance across regions, markets, and shipping modes.
- Identify product categories and products contributing to sales.
- Support interactive analysis through slicers, drill-through, report-page tooltips, and What-if parameters.
- Improve report reliability through data-quality checks and performance analysis.

## Dataset

The project uses the DataCo Smart Supply Chain dataset. The working source files discussed during development are:

- `DataCoSupplyChainDataset.csv`
- `DescriptionDataCo.csv` / `DescriptionDataCoSupplyChain.csv` (field-description file; use the exact filename present in your downloaded dataset)

The dataset was obtained from Kaggle. The exact Kaggle page URL was not recorded in the project notes, so it is intentionally not guessed here. Add the original dataset page URL before publishing this repository.

## Tools & Technologies

- Microsoft Power BI Desktop
- Power Query Editor
- DAX (Data Analysis Expressions)
- Dimensional data modeling
- CSV data source

## Report Pages

| Report page | Purpose |
|---|---|
| Logistics Executive Overview | High-level order, delivery-risk, shipping-delay, and regional overview |
| Delivery Performance Analysis | Detailed analysis of shipping delays, delivery-risk indicators, shipping modes, and order-level details |
| Product & Supply Chain Analysis | Product/category sales, top products, market distribution, and product details |
| Product Drill-through | Product-focused detail page opened from a product data point |
| Product Performance Tooltip | Tooltip page that provides contextual product performance information |
| Delivery What-if Analysis | Scenario analysis using a user-selected delivery-delay threshold |
| Forecasting & Trend Analysis | A working trend-analysis page; the built-in forecast was skipped and should not be described as a completed forecast |

A Data Quality & Validation page was also planned during the workflow. Include it in the final page list only if it exists in the delivered PBIX.

## Data Model

The model follows a dimensional structure with one central fact table and supporting dimensions:

- `Fact Order Items`
- `Dim Date`
- `Dim Product`
- `Dim Geography`
- `Dim Shipping`
- `Dim Customer`

The intended relationship pattern is one-to-many from each dimension to `Fact Order Items`, with single-direction filtering from dimensions to the fact table.

See [Data_Model_Overview.md](Data_Model_Overview.md).

## Key Analysis Areas

- Total orders and order-item volume
- Total sales value
- Average actual and scheduled shipping days
- Average shipping delay
- Late-delivery risk rate
- On-time / late risk-flag distribution
- Sales by product category and product
- Orders by market and region
- Order items exceeding a user-selected delay threshold

## Advanced Power BI Features

- DAX measures and calculated columns
- Product drill-through
- Report-page tooltip
- What-if parameter for delivery-delay threshold analysis
- Dynamic report title and KPI narrative
- Performance Analyzer review
- Data-quality and relationship validation activities

**Forecasting note:** The user chose to skip the built-in forecast. The page may show historical monthly trends, but no completed forecast should be claimed.

## Important Metric Definitions

- **Late Delivery Risk Rate** is based on the dataset's `Late Delivery Risk` flag. It is a risk-indicator rate and must not automatically be described as a confirmed actual late-delivery rate.
- **Average Shipping Delay** is calculated as average actual shipping days minus average scheduled shipping days.
- **Delivery Delay Days** and **Delivery Timing Status** are derived fields used in the report. Confirm their exact Power Query expressions and business definitions in the PBIX before publishing.
- Sales currency formatting should match the dataset/report convention. The report screenshot displayed `₹`; verify the source currency and formatting choice before interpreting values as INR.

## Repository Structure

```text
Supply_Chain_Logistics_Intelligence/
│
├── README.md
├── Project_Documentation.md
├── Data_Source.txt
├── Power_Query_Transformations.md
├── Data_Model_Overview.md
├── DAX_Measures_Documentation.md
├── Dashboard_Overview.md
├── Business_Insights.md
├── Data_Quality_Validation.md
└── Performance_Optimization.md
```

## How to Use

1. Open the `.pbix` file in Power BI Desktop.
2. Refresh the data if the source CSV files are available at the configured paths.
3. Review the report pages using the page tabs.
4. Use Year, Market, Region, Shipping Mode, and Product Category slicers where available.
5. Right-click a product data point to access the Product Drill-through page.
6. Hover over supported visuals to view the Product Performance Tooltip.
7. Change the threshold in Delivery What-if Analysis to explore order items exceeding the selected delay threshold.

## Limitations & Responsible Interpretation

- Dataset values are historical records and do not guarantee future performance.
- The built-in forecast was skipped.
- Risk flags and actual delivery outcomes are different concepts.
- Missing dates or delivery-duration values should not be silently treated as zero.
- Validate the final PBIX and all measures against the source data before using the results for operational decisions.

## Author

Add your name, portfolio link, LinkedIn profile, and GitHub repository URL here.

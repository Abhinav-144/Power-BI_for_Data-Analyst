# Project Documentation — Supply Chain & Logistics Intelligence

## 1. Executive Summary

This project uses Microsoft Power BI to analyze the DataCo Smart Supply Chain dataset. It transforms order-level and order-item data into a dimensional model and interactive report pages focused on logistics operations, delivery performance, product sales, and geographic distribution.

## 2. Problem Statement

Supply-chain data can contain multiple related operational dimensions: customers, products, orders, shipping methods, dates, and geography. An analytical report is useful when these records can be explored consistently across dimensions and translated into operational questions.

This project provides an interactive view of those areas. It is an analytical portfolio project, not a production logistics control system.

## 3. Objectives

- Consolidate source data into a reusable Power BI model.
- Build fact and dimension tables.
- Create DAX measures for orders, sales, shipping duration, and delivery-risk indicators.
- Build interactive report pages.
- Enable product drill-through and report-page tooltips.
- Add a What-if parameter for delay-threshold scenario analysis.
- Review data quality and report performance.

## 4. Data Source

Dataset: DataCo Smart Supply Chain dataset.
Source platform: Kaggle.
Files discussed: `DataCoSupplyChainDataset.csv` and a field-description CSV.

The exact Kaggle URL was not retained in the project notes. Add the exact source URL and attribution before public release.

## 5. Data Preparation

Power Query was used to:
- Import and inspect the CSV source.
- Preserve a raw query.
- Create a cleaned order-item fact query.
- Standardize data types and prepare date fields.
- Create a consistent geography key in the fact and geography dimension.
- Prepare delivery-delay and delivery-timing fields.
- Create dimension queries for date, product, geography, shipping, and customer analysis.

Refer to `Power_Query_Transformations.md` for transformation details.

## 6. Data Model

The model contains:
- Fact Order Items
- Dim Date
- Dim Product
- Dim Geography
- Dim Shipping
- Dim Customer

The intended relationship pattern is active one-to-many relationships from dimensions to the fact table, with single-direction filtering.

Refer to `Data_Model_Overview.md`.

## 7. DAX & Metrics

Key measures include:
- Total Orders
- Total Order Items
- Total Sales Value
- Average Actual Shipping Days
- Average Scheduled Shipping Days
- Average Shipping Delay
- Late Orders
- On-Time Orders
- Late Delivery Rate
- On-Time Delivery Rate
- Delayed Order Items
- Product Category Count
- What-if threshold measures
- Dynamic report title and delivery-performance narrative

Refer to `DAX_Measures_Documentation.md` for formulas.

## 8. Report Pages

1. Logistics Executive Overview
2. Delivery Performance Analysis
3. Product & Supply Chain Analysis
4. Product Drill-through
5. Product Performance Tooltip
6. Delivery What-if Analysis
7. Forecasting & Trend Analysis (historical trend analysis; forecast skipped)

A separate Data Quality page should be listed only if it exists in the final PBIX.

## 9. Advanced Features

- Drill-through analysis for product details
- Report-page tooltip
- What-if parameter for delay-threshold analysis
- Dynamic title and KPI narrative
- Performance Analyzer review
- Data-quality and relationship validation

## 10. Validation

Before delivery, verify:
- Dimension key uniqueness
- Fact-to-dimension matching
- Date parsing and date-table relationship
- Missing and blank values
- Sales and order totals against the source
- Delivery-delay calculation definition
- Risk-flag interpretation
- Slicer interactions and drill-through behavior

## 11. Limitations

- The built-in forecast was skipped.
- Historical trend charts are not forecasts.
- The late-delivery-risk flag should not be presented as confirmed lateness without validation.
- The exact source URL and full Power Query M scripts must be added from the user's actual source/PBIX.
- Currency must be confirmed before financial results are interpreted.

## 12. Conclusion

The project demonstrates an end-to-end Power BI workflow: source-data preparation, dimensional modeling, DAX calculations, interactive reporting, scenario analysis, and validation. It provides a foundation for exploring supply-chain and logistics performance through a structured analytical report.

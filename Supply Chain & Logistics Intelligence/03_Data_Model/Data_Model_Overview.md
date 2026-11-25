# Data Model Overview

## Model Design

The Supply Chain & Logistics Intelligence report uses a dimensional model centered on the order-item fact table.

```text
                  Dim Date
                     |
Dim Customer --- Fact Order Items --- Dim Product
                     |
                Dim Geography
                     |
                 Dim Shipping
```

This is a conceptual view. In Power BI Model view, each dimension should connect directly to the fact table rather than dimensions connecting to one another.

## Tables

### Fact Order Items

Grain: one row per order item, subject to validation against the source identifiers.

Fields discussed include:
- Order ID
- Order Item ID
- Customer Id
- Product key / Product Card ID
- Shipping Mode
- Order Date Only
- Actual Shipping Days
- Scheduled Shipping Days
- Delivery Delay Days
- Delivery Timing Status
- Late Delivery Risk
- Sales
- Geography Key

A duplicate check of the combination Order ID + Order Item ID was reported as having no duplicates during development. Recheck after the final refresh.

### Dim Date

Date dimension with:
- Date
- Year
- Quarter
- Month
- Month Number
- Year Month
- Year Month Sort
- Month Start (calculated column)

`Year Month` should be sorted by `Year Month Sort`. `Month Start` is a date column used for chronological monthly trend analysis.

### Dim Product

Product lookup dimension with:
- Product Card ID
- Product Name
- Category Name

### Dim Geography

Geographic lookup dimension with:
- Geography Key
- Market
- Region
- Order Country
- Order State

### Dim Shipping

Shipping lookup dimension with:
- Shipping Mode

### Dim Customer

Customer lookup dimension with:
- Customer Id

## Relationships

Intended active relationships:

| One-side dimension | Dimension key | Many-side fact key |
|---|---|---|
| Dim Customer | Customer Id | Fact Order Items[Customer Id] |
| Dim Product | Product Card ID | Fact Order Items[Product Card ID] |
| Dim Geography | Geography Key | Fact Order Items[Geography Key] |
| Dim Shipping | Shipping Mode | Fact Order Items[Shipping Mode] |
| Dim Date | Date | Fact Order Items[Order Date Only] |

Relationship configuration:
- Cardinality: One-to-many (1:*)
- Cross-filter direction: Single
- Direction: dimension filters fact
- Active: Yes

Confirm the exact product key column name in the final PBIX; the fact-side field name may differ from `Product Card ID` depending on the transformation.

## Modeling Considerations

- Dimension keys must be unique.
- Both sides of a relationship must have compatible data types.
- Avoid unnecessary bidirectional filtering.
- Investigate blank dimension members and unmatched fact keys.
- Mark `Dim Date` as the date table using its `Date` column if appropriate.
- Use dimension fields for slicers and chart axes where possible.

# Dashboard Pages & Visual Design

## 1. Logistics Executive Overview

Purpose: provide a high-level view of order activity, delivery risk, shipping delay, and geographic performance.

KPI cards:
- Total Orders
- On-Time Delivery Rate (risk-flag-derived unless validated)
- Late Orders (risk-flag-derived)
- Average Shipping Delay

Visuals:
- Monthly order trend: `Dim Date[Year Month]` vs `[Total Orders]`
- Orders by region: `Dim Geography[Region]` vs `[Total Orders]`
- Late-delivery risk rate by shipping mode: `Dim Shipping[Shipping Mode]` vs `[Late Delivery Rate]`

Slicers:
- Year
- Market
- Region
- Shipping Mode

## 2. Delivery Performance Analysis

Purpose: examine delivery duration and risk patterns across geography and shipping modes, with order-level detail.

KPI cards:
- Late Delivery Risk Rate
- Average Shipping Delay
- Average Actual Shipping Days
- Delayed Order Items

Visuals:
- Average shipping delay by region
- Monthly average shipping delay trend
- Average shipping delay by shipping mode
- Order detail table containing relevant order date, shipping mode, scheduled/actual days, delivery timing status, and risk flag

Slicers:
- Year
- Market
- Region
- Shipping Mode

Conditional formatting:
A color measure was proposed for `Delivery Timing Status`:

```dax
Delivery Status Color =
SWITCH(
    SELECTEDVALUE('Fact Order Items'[Delivery Timing Status]),
    "Delayed", "#F44336",
    "On Time", "#4CAF50",
    "#D9D9D9"
)
```

Apply using table conditional formatting → Background color → Format style: Field value → `Delivery Status Color`. Confirm status labels match the actual data.

## 3. Product & Supply Chain Analysis

Purpose: understand sales contribution by category, product, and market.

KPI cards:
- Total Orders
- Total Sales Value
- Total Order Items
- Product Category Count

Visuals:
- Sales by product category
- Top 10 products by sales value
- Orders by market
- Product detail table with product, category, total orders, and total sales value

Slicers:
- Year
- Market
- Region
- Product Category

## 4. Product Drill-through

Purpose: provide product-level detail from a product data point in the main product analysis page.

Suggested content:
- Total Sales Value
- Total Orders
- Total Order Items
- Average Shipping Delay
- Monthly sales trend
- Sales by market
- Product detail table

Drill-through field: `Dim Product[Product Name]` was discussed. If names are not unique, use the product key and ensure the source visual passes the same field context.

## 5. Product Performance Tooltip

Purpose: show contextual product metrics on hover.

Suggested content:
- Total Sales Value
- Total Orders
- Total Order Items
- Average Shipping Delay
- Sales by market

A category-level visual passes category context; an individual-product visual passes product context.

## 6. Delivery What-if Analysis

Purpose: let users select a delay threshold and examine order items exceeding it.

Parameter:
- Name: `Delay Threshold Days`
- Minimum: 0
- Maximum: 30
- Increment: 1
- Default: 3

Visuals:
- Threshold slicer
- Order Items Above Threshold card
- Percentage Above Threshold card
- Order Items Above Threshold by Region bar chart

## 7. Forecasting & Trend Analysis

A page was created for monthly sales trend analysis. The user explicitly chose to skip the built-in forecast. Do not claim a forecast was completed. Historical trend analysis can remain if the visuals are working and validated.

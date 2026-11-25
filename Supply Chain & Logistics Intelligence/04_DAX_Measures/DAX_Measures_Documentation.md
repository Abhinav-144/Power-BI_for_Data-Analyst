# DAX Measures & Calculated Columns

This document records the DAX definitions discussed during the project. Confirm exact names and formulas in the final PBIX before publishing.

## Core measures

### Total Orders

```dax
Total Orders =
DISTINCTCOUNT('Fact Order Items'[Order ID])
```

Counts distinct orders rather than order-item rows.

### Total Order Items

```dax
Total Order Items =
COUNTROWS('Fact Order Items')
```

Counts rows in the order-item fact table. This assumes the fact table grain is one row per order item.

### Total Sales Value

```dax
Total Sales Value =
SUM('Fact Order Items'[Sales])
```

Aggregates the Sales field. Confirm currency and source meaning before financial interpretation.

### Average Actual Shipping Days

```dax
Average Actual Shipping Days =
AVERAGE('Fact Order Items'[Actual Shipping Days])
```

### Average Scheduled Shipping Days

```dax
Average Scheduled Shipping Days =
AVERAGE('Fact Order Items'[Scheduled Shipping Days])
```

### Average Shipping Delay

```dax
Average Shipping Delay =
[Average Actual Shipping Days] - [Average Scheduled Shipping Days]
```

This is the difference between the average actual and average scheduled shipping durations. It is not necessarily identical to the average of a row-level delay column.

### Late Orders

```dax
Late Orders =
CALCULATE(
    [Total Orders],
    'Fact Order Items'[Late Delivery Risk] = 1
)
```

Counts distinct orders with the risk flag equal to 1. This is a risk-flag count, not necessarily a verified count of actually late deliveries.

### On-Time Orders

```dax
On-Time Orders =
CALCULATE(
    [Total Orders],
    'Fact Order Items'[Late Delivery Risk] = 0
)
```

Counts distinct orders with the risk flag equal to 0. Interpret according to the dataset's flag definition.

### Late Delivery Rate

```dax
Late Delivery Rate =
DIVIDE([Late Orders], [Total Orders], 0)
```

### On-Time Delivery Rate

```dax
On-Time Delivery Rate =
DIVIDE([On-Time Orders], [Total Orders], 0)
```

These rates are based on the risk flag. Label visuals accordingly unless the flag has been validated as an actual delivery outcome.

### Delayed Order Items

```dax
Delayed Order Items =
CALCULATE(
    [Total Order Items],
    'Fact Order Items'[Delivery Timing Status] = "Delayed"
)
```

Ensure the text value exactly matches the values in the column.

### Product Category Count

```dax
Product Category Count =
DISTINCTCOUNT('Dim Product'[Category Name])
```

## Date table

The following date table pattern was used:

```dax
Dim Date =
VAR MinDate =
    MINX(
        FILTER(
            'Fact Order Items',
            NOT ISBLANK('Fact Order Items'[Order Date Only])
        ),
        'Fact Order Items'[Order Date Only]
    )
VAR MaxDate =
    MAXX(
        FILTER(
            'Fact Order Items',
            NOT ISBLANK('Fact Order Items'[Order Date Only])
        ),
        'Fact Order Items'[Order Date Only]
    )
RETURN
ADDCOLUMNS(
    CALENDAR(MinDate, MaxDate),
    "Year", YEAR([Date]),
    "Quarter", "Q" & FORMAT([Date], "Q"),
    "Month", FORMAT([Date], "MMM"),
    "Month Number", MONTH([Date]),
    "Year Month", FORMAT([Date], "YYYY-MM"),
    "Year Month Sort", YEAR([Date]) * 100 + MONTH([Date])
)
```

### Month Start calculated column

Create using **New column**, not **New measure**:

```dax
Month Start =
DATE(
    YEAR('Dim Date'[Date]),
    MONTH('Dim Date'[Date]),
    1
)
```

## What-if analysis

The What-if parameter table was named `Delay Threshold Days`, with a numeric range discussed as 0–30, increment 1, default 3.

If Power BI did not create the value measure automatically:

```dax
Selected Delay Threshold =
SELECTEDVALUE(
    'Delay Threshold Days'[Delay Threshold Days],
    3
)
```

### Order Items Exceeding Threshold

```dax
Order Items Exceeding Threshold =
VAR ThresholdDays = [Selected Delay Threshold]
RETURN
CALCULATE(
    [Total Order Items],
    FILTER(
        'Fact Order Items',
        NOT ISBLANK('Fact Order Items'[Delivery Delay Days])
            && 'Fact Order Items'[Delivery Delay Days] > ThresholdDays
    )
)
```

### Order Items Exceeding Threshold %

```dax
Order Items Exceeding Threshold % =
DIVIDE(
    [Order Items Exceeding Threshold],
    CALCULATE(
        [Total Order Items],
        FILTER(
            'Fact Order Items',
            NOT ISBLANK('Fact Order Items'[Delivery Delay Days])
        )
    ),
    0
)
```

The comparison is strictly greater than the selected threshold. Blank delay values are excluded.

## Dynamic title

```dax
Dynamic Report Title =
VAR SelectedYear =
    SELECTEDVALUE('Dim Date'[Year])
VAR SelectedMarket =
    SELECTEDVALUE('Dim Geography'[Market])
RETURN
    "Supply Chain Performance"
    & IF(
        NOT ISBLANK(SelectedYear),
        " | Year: " & FORMAT(SelectedYear, "0"),
        ""
    )
    & IF(
        NOT ISBLANK(SelectedMarket),
        " | Market: " & SelectedMarket,
        ""
    )
```

## Delivery performance narrative

```dax
Delivery Performance Narrative =
VAR LateRate = [Late Delivery Rate]
RETURN
    SWITCH(
        TRUE(),
        ISBLANK(LateRate),
            "Delivery performance data is unavailable.",
        LateRate >= 0.30,
            "High delivery risk: review late-delivery patterns and shipping operations.",
        LateRate >= 0.15,
            "Moderate delivery risk: investigate regions and shipping modes with elevated risk.",
        "Lower delivery risk based on the current selection. Continue monitoring delivery performance."
    )
```

The 15% and 30% thresholds are illustrative business rules, not source-provided standards. The narrative is based on the late-delivery-risk flag.

## Formatting guidance

- Counts: whole number
- Rates: percentage
- Shipping days: 2 decimal places
- Sales: format using the verified source/report currency

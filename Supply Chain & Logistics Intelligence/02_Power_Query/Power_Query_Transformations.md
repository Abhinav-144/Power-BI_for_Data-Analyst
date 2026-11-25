# Power Query Transformations

## Purpose

Power Query was used to import, inspect, clean, type, and prepare the DataCo Smart Supply Chain CSV data for the Power BI model.

## Query Organization

The workflow discussed during development used:

- `Raw_DataCo` — preserved raw/imported source query.
- `Fact Order Items` — transformed order-item fact query.
- `Dim Date`
- `Dim Product`
- `Dim Geography`
- `Dim Shipping`
- `Dim Customer`

The dimension queries should be derived from the cleaned source and reduced to the required attributes and unique dimension keys.

## Transformation Areas

### 1. Source import and raw preservation

1. Import `DataCoSupplyChainDataset.csv` using **Get Data → Text/CSV**.
2. Inspect delimiter, headers, and column quality.
3. Preserve a raw source query (discussed name: `Raw_DataCo`).
4. Reference the raw query to create the cleaned fact and dimension queries.
5. Avoid applying irreversible cleaning steps to the only copy of the source query.

### 2. Column names and data types

- Standardize column names where needed.
- Assign appropriate data types to identifiers, dates, numeric measures, and text attributes.
- Keep identifier columns consistent across fact and dimension tables.
- Validate date parsing using the correct locale if source date strings are locale-dependent.

### 3. Order date conversion

The project created `Order Date Only` from the source order date for the date relationship.

If the source value is text in US date/time format, a conversion pattern used in the workflow was:

```powerquery
Date.From(
    DateTime.FromText(
        Text.Trim(Text.From([Order Date])),
        [Culture = "en-US"]
    )
)
```

If the source column is already Date/DateTime:

```powerquery
Date.From([Order Date])
```

Use the expression that matches the actual source type. Set the resulting column to the **Date** data type.

### 4. Geography key

A common geography key was created in both the fact query and `Dim Geography`, using the same ordered components:

- Market
- Region / Order Region
- Order Country
- Order State

The key must use identical concatenation, trimming, null handling, and separators in both queries. Do not use independently written expressions that could produce mismatched keys.

### 5. Delivery analysis columns

The workflow created:

- `Delivery Delay Days`
- `Delivery Timing Status`

These were used for delay analysis and the What-if scenario. Confirm the exact source columns and Power Query formulas in the final PBIX. Do not infer that the dataset's late-delivery-risk flag is the same as actual delay.

### 6. Dimension preparation

The dimension tables should contain the fields needed for filtering and reporting, with unique keys:

- `Dim Customer`: unique `Customer Id`
- `Dim Product`: unique `Product Card ID`, with product/category attributes
- `Dim Geography`: unique `Geography Key`, with market/region/country/state attributes
- `Dim Shipping`: unique `Shipping Mode`
- `Dim Date`: one row per date (created in DAX in the workflow)

### 7. Validation during transformation

Check:
- Nulls in identifiers and dates
- Conversion errors
- Duplicate dimension keys
- Fact rows with missing or unmatched dimension keys
- Consistency of geography-key construction
- Numeric type of `Delivery Delay Days`
- Whether source values are missing versus genuinely zero

## Important Notes

The project notes do not contain a complete exported Power Query M script for every query. This document records the transformation logic and column/table names discussed during development. For exact reproducibility, export or copy the final **Advanced Editor** M code from the PBIX and add it to a `Power_Query_M_Code` folder.

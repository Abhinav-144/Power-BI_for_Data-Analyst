# Data Quality & Validation

## Validation Objectives

Ensure that report calculations and relationships are reliable before publishing or sharing the PBIX.

## Checks to Perform

### 1. Missing values
Inspect:
- Fact Order Items[Order ID]
- Fact Order Items[Order Date Only]
- Fact Order Items[Delivery Delay Days]
- Fact Order Items[Geography Key]
- Dimension keys

Do not automatically replace missing delivery delays with zero. A missing value may mean unavailable information.

### 2. Duplicate dimension keys
Confirm uniqueness for:
- Dim Customer[Customer Id]
- Dim Product[Product Card ID]
- Dim Geography[Geography Key]
- Dim Shipping[Shipping Mode]
- Dim Date[Date]

Investigate duplicate keys before removing records.

### 3. Fact grain
The combination Order ID + Order Item ID was checked during development and no duplicates were reported at that time. Re-run the check after the final data refresh.

### 4. Relationship integrity
Confirm:
- Active relationships
- One-to-many cardinality
- Single-direction filtering from dimensions to fact
- Matching data types
- No unexpected many-to-many relationships
- No unexplained blank dimension members

### 5. Delivery metric validation
Compare the derived `Delivery Delay Days` with the source actual and scheduled shipping-duration fields. Confirm the exact definition of `Delivery Timing Status`.

Keep the risk flag separate from the actual delivery outcome.

### 6. Reconciliation
Compare:
- Fact row count to source row count
- Distinct Order ID count to a source-based calculation
- Sales sum to a source-based calculation
- Dimension distinct-key counts to fact distinct-key counts

Use consistent filters and account for nulls when reconciling.

## DAX diagnostic measures

```dax
Total Fact Rows =
COUNTROWS('Fact Order Items')
```

```dax
Rows Missing Order ID =
CALCULATE(
    COUNTROWS('Fact Order Items'),
    ISBLANK('Fact Order Items'[Order ID])
)
```

```dax
Rows Missing Order Date =
CALCULATE(
    COUNTROWS('Fact Order Items'),
    ISBLANK('Fact Order Items'[Order Date Only])
)
```

```dax
Rows Missing Delivery Delay =
CALCULATE(
    COUNTROWS('Fact Order Items'),
    ISBLANK('Fact Order Items'[Delivery Delay Days])
)
```

## Sign-off checklist

- [ ] Source row count reconciled
- [ ] Fact grain confirmed
- [ ] Dimension keys unique
- [ ] Relationships verified
- [ ] Missing values reviewed
- [ ] Date range and date relationship verified
- [ ] Sales totals reconciled
- [ ] Delivery delay definition verified
- [ ] Risk flag definition documented
- [ ] Visuals and slicers tested

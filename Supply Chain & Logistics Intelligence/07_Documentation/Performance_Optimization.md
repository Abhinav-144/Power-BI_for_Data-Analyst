# Performance Optimization

## Purpose

Improve report responsiveness and maintainability without changing business definitions.

## Performance Analyzer Workflow

1. Open **View → Performance Analyzer** in Power BI Desktop.
2. Select **Start recording**.
3. Select **Refresh visuals**.
4. Interact with key slicers.
5. Expand visual timings and identify slow visuals.
6. Export the analysis if a record is needed.
7. Optimize the actual bottleneck and repeat the same test.

## Model Review

- Remove unused columns only after checking all dependencies.
- Prefer a star-schema relationship pattern.
- Keep dimension-to-fact relationships single-direction where possible.
- Use correct data types.
- Avoid unnecessary calculated columns when a Power Query transformation is more suitable.
- Keep dimension keys unique.

## Visual Review

- Avoid showing thousands of detail rows by default.
- Use Top N filters for long product lists.
- Remove redundant visuals.
- Limit unnecessary interactions.
- Use concise titles and labels.

## DAX Review

- Prefer simple, reusable measures.
- Avoid repeating complex expressions unnecessarily.
- Use variables where they improve clarity.
- Optimize only after identifying a measurable performance issue.

## Validation

Compare before/after results using the same page, filters, and slicer selections. Ensure that optimization has not changed the meaning or result of the report.

# Business Insights & Analytical Questions

## Purpose

This document outlines the business questions the report is designed to answer. These are analytical interpretation areas, not verified numerical findings. Add quantified findings only after checking the final PBIX and applying the relevant filters.

## 1. Executive Overview

Questions:
- How does order volume change over time?
- Which regions contribute the most orders?
- How does the late-delivery-risk indicator vary by shipping mode?
- Are there periods with unusual order-volume changes?

Potential business use:
- Monitor operational workload.
- Identify regions that may require closer operational review.
- Compare shipping-mode risk indicators.

## 2. Delivery Performance

Questions:
- Which regions have the highest average shipping delay?
- Which shipping modes show higher average shipping duration differences?
- How does average shipping delay change month to month?
- Which order records have unusually high actual shipping days compared with scheduled days?

Potential business use:
- Prioritize investigation of regions or shipping modes with elevated delays.
- Review scheduling assumptions.
- Investigate order-level exceptions.

Interpretation caution:
The `Late Delivery Risk` flag represents a risk indicator. It should not be treated as confirmed actual lateness unless the source definition and delivery outcomes have been validated.

## 3. Product & Supply Chain

Questions:
- Which product categories contribute the greatest sales value?
- Which products rank among the top 10 by sales?
- How are orders distributed across markets?
- Do product sales patterns vary across markets and regions?

Potential business use:
- Support product/category performance reviews.
- Identify products with high sales contribution.
- Compare geographic demand patterns.

## 4. What-if Threshold Analysis

Questions:
- How many order items exceed a selected delay threshold?
- What proportion of order items with known delay values exceed the threshold?
- Which regions have the highest number of order items exceeding the threshold?

Potential business use:
- Explore alternative operational alert thresholds.
- Compare regions using a consistent threshold.
- Support investigation prioritization.

This is scenario analysis over historical records, not a prediction of future delivery performance.

## 5. Recommended Insight Writing Format

For each final finding, document:
1. **Observation:** what the visual or measure shows.
2. **Evidence:** exact value, period, and filter context.
3. **Interpretation:** what the pattern may mean.
4. **Action:** a practical next step.
5. **Caveat:** data limitations or metric-definition constraints.

## Quantified Findings

No verified final ranking, percentage, sales total, or regional result is asserted in this document. Populate this section from the final validated report rather than inventing figures.

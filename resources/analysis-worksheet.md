# ABC-XYZ Analysis Worksheet

Use one consistent period frequency, currency, and value basis throughout the dataset.

## 1. Data Checks

- Confirm one row per SKU per period.
- Confirm the period range is complete.
- Distinguish missing observations from true zero demand.
- Check duplicate rows, returns, negative quantities, and exceptional orders.
- Confirm unit values are comparable and use one currency.
- Record the demand unit and period frequency.

## 2. Annual Consumption Value

For each SKU:

Annual consumption value = sum of (period quantity × unit value).

Sort descending by annual consumption value. Calculate each SKU's share of total value and cumulative share.

Starting ABC convention:
- A: cumulative value through approximately 80%.
- B: the next approximately 15%.
- C: the remaining value.

State the exact breakpoint rule used, especially where a SKU crosses a threshold. Do not force a portfolio into a textbook distribution if the data does not support it.

## 3. Demand Variability

For each SKU, calculate mean and standard deviation of period demand:

CV = standard deviation / mean period demand.

Starting XYZ convention:
- X: CV below 0.5.
- Y: CV from 0.5 to below 1.0.
- Z: CV at or above 1.0.

Use the same standard-deviation convention across SKUs. Inspect the actual distribution rather than assuming the thresholds are universally correct.

### Intermittent and zero-mean demand

A SKU with repeated zero-demand periods is intermittent and should normally be treated as Z even where arithmetic CV is misleading. If mean demand is zero, CV is undefined. Do not divide by zero or silently assign X; flag the item as no observed demand or intermittent according to the business rule.

## 4. Build the 9-Box

For every occupied cell, report:
- Number of SKUs.
- Share of total SKUs.
- Total annual consumption value.
- Share of total annual consumption value.

Value shares across all occupied cells must sum to 100%, subject to rounding.

## 5. Translate Cells into Decisions

Use the 9-box policy matrix as a starting point. Adjust for supplier lead time, service targets, substitutability, criticality, minimum order quantities, shelf life, and cash constraints.

## 6. Validate and Communicate

- Recalculate totals independently.
- Spot-check at least two SKUs against raw period data.
- Check that high-value SKUs are not ranked by quantity alone.
- Identify process-driven variability such as batching or promotions.
- State data gaps, thresholds, assumptions, and review cadence.
- Recommend a quarterly refresh where the operating cycle supports it.

## Suggested Output Pack

1. Data quality summary.
2. ABC and XYZ threshold definitions.
3. 3 × 3 matrix with SKU counts and value shares.
4. Policy table for occupied cells.
5. Planner-attention reallocation recommendation.
6. Rationalization candidates with reasons and caveats.

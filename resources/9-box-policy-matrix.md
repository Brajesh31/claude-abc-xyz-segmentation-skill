# ABC-XYZ 9-Box Planning Policy Matrix

These are starting policies, not automatic inventory rules. Confirm service requirements, item criticality, supplier lead time, minimum order quantities, shelf life, substitution options, and stockout cost before implementation.

| Cell | Typical profile | Starting planning policy | Review focus |
|---|---|---|---|
| A-X | High value, predictable | Close forecast review; frequent replenishment review; avoid unnecessary buffer | Forecast bias, service level, supplier reliability |
| A-Y | High value, moderately variable | Forecast plus deliberate buffer; investigate variability drivers | Promotions, lead-time variation, planned events |
| A-Z | High value, highly variable or intermittent | Avoid false forecast precision; consider strategic buffer, supplier agreements, lead-time reduction, or make-to-order | Stockout exposure, obsolescence, sourcing flexibility |
| B-X | Medium value, predictable | Standardized min-max or reorder-point process | Review frequency and automation |
| B-Y | Medium value, moderately variable | Periodic forecast review and moderate buffer based on service target | Variability trend and supplier performance |
| B-Z | Medium value, highly variable | Buffer selectively or extend promise dates; investigate controllable variation | Batching, promotions, supplier constraints |
| C-X | Lower value, predictable | Simple replenishment automation; reduce manual planner effort | Exceptions and minimum order quantities |
| C-Y | Lower value, moderately variable | Simple periodic review; avoid over-engineering | Holding cost and service impact |
| C-Z | Lower value, highly variable or intermittent | Rationalization shortlist, on-demand sourcing, or consolidation where appropriate | Shelf age, holding cost, strategic exceptions |

## Attention Reallocation

A useful recommendation explicitly states which cells should receive more planner time and which can move to automated or exception-based control. Do not infer planner hours from classifications alone. Use SKU count, workload, service failures, supplier complexity, and value exposure to estimate the change.

## Review Triggers

Reassess a SKU when its value, variability, lead time, supply risk, strategic status, or customer impact changes materially. A quarterly review is a reasonable starting cadence for many portfolios, but use the organization's planning cycle.

# ABC-XYZ Segmentation Skill

A focused skill for segmenting inventory portfolios by annual consumption value and demand variability. The combined 9-box view connects item classification to replenishment policy, inventory buffers, forecasting effort, and assortment decisions.

ABC answers where inventory value is concentrated. XYZ answers how predictable demand is. The combined view is useful only when each occupied cell leads to a practical planning response.

## What This Skill Helps With

- Validate SKU-level demand history and unit values.
- Calculate annual consumption value.
- Rank SKUs and assign ABC classes.
- Calculate demand variability using coefficient of variation.
- Assign XYZ classes while treating intermittent demand carefully.
- Build a 3 × 3 ABC-XYZ matrix.
- Report SKU counts and value share by segment.
- Translate segments into replenishment and planner-attention policies.
- Identify candidates for rationalization.
- Validate totals and spot-check classifications.

## When to Use It

Use this skill for inventory segmentation, SKU rationalization, forecasting prioritization, replenishment policy design, and allocation of planner capacity.

Do not present an ABC value classification when unit prices or costs are missing. In that situation, make clear that the result is a quantity or volume ranking, not a financial-value ranking.

## Installation

~~~bash
git clone https://github.com/Brajesh31/claude-abc-xyz-segmentation-skill.git ~/.claude/skills/abc-xyz-segmentation
~~~

## Usage

Invoke:

~~~text
/abc-xyz-segmentation
~~~

Provide a dataset with SKU, period, quantity, and unit value. Also state the period frequency, currency, business context, and constraints such as supplier lead time, service-level targets, or minimum order quantities.

## Required Data

| Field | Meaning | Requirement |
|---|---|---|
| sku | Stable item identifier | Required |
| period | Month, week, or other consistent period | Required |
| qty | Demand quantity in that period | Required |
| unit_price or unit_cost | Value used for ABC ranking | Required for value-based ABC |
| currency | Currency for unit values | Strongly recommended |

Use a consistent time basis and value basis across items. Separate returns, corrections, and one-off exceptional demand where they would distort interpretation.

## Classification Workflow

### ABC classification

Calculate annual consumption value per SKU:

Annual consumption value = sum of period quantity multiplied by unit value.

Sort SKUs from highest to lowest value and calculate each item's share of total value and cumulative share. The commonly used starting convention is A through the first 80% of cumulative value, B through the next 15%, and C for the remainder. Report the actual breakpoints and item concentration rather than assuming a fixed 80/15/5 distribution.

### XYZ classification

Calculate the coefficient of variation:

CV = standard deviation of period demand divided by mean period demand.

Starting conventions are X below 0.5, Y from 0.5 to below 1.0, and Z at or above 1.0. Review the actual distribution before applying these cutoffs. SKUs with intermittent or structurally zero periods should be treated as Z even when a mechanical CV calculation would understate the risk.

### Combined matrix

Cross the ABC and XYZ classifications to create nine possible segments. Report both the SKU count and the share of total consumption value represented by each occupied cell.

## Operational Interpretation

A-X items generally justify close forecasting and frequent review. A-Z items may need strategic buffers, supplier lead-time work, or make-to-order approaches rather than false precision in forecasts. C-Z items are candidates for assortment review, but discontinuation decisions must consider criticality, substitution, and customer impact.

The complete starting policy set is in [the 9-box policy matrix](resources/9-box-policy-matrix.md).

## Included Resources

- [Example SKU demand dataset](resources/sample-demand-data.csv)
- [Analysis worksheet and calculation guide](resources/analysis-worksheet.md)
- [9-box planning policy matrix](resources/9-box-policy-matrix.md)

## Validation Checklist

- Period definitions and units are consistent.
- Missing periods are not silently treated as zero unless that is correct.
- Unit values are comparable and use one currency.
- Annual value shares sum to 100%, subject to rounding.
- ABC thresholds and exact breakpoints are disclosed.
- XYZ thresholds and standard-deviation convention are disclosed.
- Intermittent and zero-mean demand are handled explicitly.
- At least two SKU classifications are checked against raw data.
- Recommendations account for supplier constraints and service requirements.

## Limitations

ABC-XYZ is a prioritization framework, not a complete replenishment optimizer. It does not automatically account for supplier capacity, lead-time distributions, minimum order quantities, substitution, shelf life, obsolescence, service-level targets, or cash constraints. Add those factors before converting a segment label into an operational rule.

## Repository Structure

~~~text
claude-abc-xyz-segmentation-skill/
├── SKILL.md
├── README.md
├── LICENSE
└── resources/
    ├── analysis-worksheet.md
    ├── sample-demand-data.csv
    └── 9-box-policy-matrix.md
~~~

## License

See LICENSE. The applicable upstream MIT notice is retained, with a separate notice for new supplementary repository documentation.

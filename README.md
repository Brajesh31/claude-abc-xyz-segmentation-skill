# claude-abc-xyz-segmentation-skill

A Claude Code skill for segmenting inventory by value and demand variability using ABC-XYZ analysis.

## Overview

ABC analysis classifies items by their contribution to total consumption value. XYZ analysis classifies demand patterns by variability. Combining both dimensions creates a 9-box view that helps allocate forecasting effort, inventory buffers, and planner attention.

The key output is not only a label. Each segment should have a practical planning policy.

## Main Capabilities

- Calculate annual consumption value.
- Rank SKUs by value contribution.
- Assign ABC classes.
- Calculate demand variability.
- Assign XYZ classes.
- Build the combined 9-box matrix.
- Report SKU counts and value share by segment.
- Recommend inventory and planning policies.
- Identify candidates for SKU rationalization.
- Validate calculations and assumptions.

## Required Data

A typical analysis needs:

- SKU identifier.
- Period-level demand history.
- Unit price or unit cost.
- At least 12 periods of history where possible.

Without unit value, ABC becomes a volume ranking rather than a financial value analysis. State this limitation clearly.

## Classification Method

### ABC

Rank items by annual consumption value and calculate cumulative value share. Common thresholds can be used as a starting point, but report the actual distribution rather than assuming every portfolio follows a fixed pattern.

### XYZ

Calculate demand variability, commonly using coefficient of variation:

`CV = standard deviation / mean demand`

Typical starting thresholds are X below 0.5, Y from 0.5 to below 1.0, and Z at or above 1.0. Review the actual distribution and identify intermittent demand separately.

## Installation

```bash
git clone https://github.com/Brajesh31/claude-abc-xyz-segmentation-skill.git ~/.claude/skills/abc-xyz-segmentation
```

## Usage

Invoke the skill for inventory segmentation:

```text
/abc-xyz-segmentation
```

Provide the demand history, SKU values, period definition, currency, and any business-specific thresholds.

## Planning Policy Examples

| Segment | Typical planning approach |
|---|---|
| A-X | Frequent review, accurate forecast, lean buffer |
| A-Y | Forecast plus buffer and variability investigation |
| A-Z | Strategic buffer, lead-time action, or make-to-order |
| B-X / C-X | Simplified replenishment and low planner effort |
| B-Z | Review variability drivers and buffer needs |
| C-Z | Rationalization or on-demand sourcing review |

These are starting policies. Adjust them to service levels, lead times, supplier risk, and business criticality.

## Recommended Workflow

1. Validate the demand history and SKU values.
2. Calculate annual consumption value.
3. Rank SKUs and calculate cumulative share.
4. Assign ABC classes.
5. Calculate demand variability.
6. Assign XYZ classes.
7. Build the 9-box matrix.
8. Report SKU counts and value share per cell.
9. Assign planning policies.
10. Validate totals and spot-check individual SKUs.

## Validation Checklist

- Demand periods are consistent.
- Missing values are handled explicitly.
- Unit values are current and comparable.
- ABC value share totals 100%.
- XYZ thresholds are documented.
- Intermittent demand is treated appropriately.
- Two or more SKU classifications are spot-checked.
- Policy recommendations reflect business constraints.

## Repository Contents

- `SKILL.md`: Main ABC-XYZ segmentation workflow.
- `README.md`: Method, policies, and validation guidance.

## Practical Principle

ABC alone is only half the analysis. The value-variability combination should determine where planning effort and inventory investment go.

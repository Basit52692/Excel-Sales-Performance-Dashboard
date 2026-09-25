# Retail sales and profitability review

## Objective

Build a repeatable Excel view of sales and profit, with enough calculation detail to explain what drives the results. The audience is a sales or category manager reviewing historical performance.

The review uses 10,000 supplied practice records from 2019–2022. Amounts use the source's unspecified currency. The dataset is not represented as verified company data.

## 1. Growth improved in 2022

| Metric | 2021 | 2022 | Change |
|---|---:|---:|---:|
| Sales | 2,453,286.96 | 2,535,711.07 | +3.36% |
| Profit | 417,145.82 | 438,023.59 | +5.00% |
| Profit margin | 17.00% | 17.27% | +0.27 percentage points |

Profit grew faster than sales. That is consistent with an improvement in aggregate margin, but the totals do not explain whether prices, costs, discounts or product mix caused it. The next step would be to compare those factors within consistent product groups.

## 2. Discount groups have different margins

| Discount | Orders | Sales | Profit | Weighted margin |
|---|---:|---:|---:|---:|
| 0% | 2,443 | 2,411,743.79 | 490,676.07 | 20.35% |
| 10% | 2,526 | 2,599,984.54 | 469,685.71 | 18.06% |
| 20% | 2,481 | 2,466,939.97 | 393,280.59 | 15.94% |
| 30% | 2,550 | 2,555,047.65 | 357,537.97 | 13.99% |

Scope: all records, 2019–2022. Margin is total group profit divided by total group sales.

The 30% discount group's margin is 6.35 percentage points below the zero-discount group, calculated before rounding. This does not establish the causal effect of discounting. The groups may differ in product mix, customer mix, costs or promotional purpose.

**Recommended action:** compare margins within product, region and period before changing promotion rules. A pricing experiment would also need demand and conversion data. Do not estimate savings by assuming the current high-discount order volume would remain unchanged at full price.

## 3. Product contribution is more useful than sales alone

Binder has the highest product-name sales at 1,179,000.64, while Conference Table has the highest profit at 203,828.28. Storage Box has the lowest margin at 16.38%, compared with 17.05% overall.

**Recommended action:** review Storage Box's cost and discount mix. A lower margin can be acceptable if the product contributes useful volume or supports other sales, but this dataset cannot test those explanations.

The data contains nine product names but 10,000 unique Product IDs. These are product-name groups, not verified SKUs. All nine are included in the dashboard, with their ranking recalculated after filtering.

## 4. Negative profit needs proportionate attention

There are 79 negative-profit orders, or 0.79% of the 10,000 orders. Their combined loss is 391.88 in source units. Those rows are retained and highlighted for review.

**Recommended action:** inspect whether the small losses reflect rounding, discounts or source-generation rules. They do not justify claiming a major cost-saving opportunity.

## Analytical decisions

- Use the raw source values rather than the previous dashboard's cached totals.
- Parse dates as day/month/year, so `09/12/2019` is 9 December, not 12 September.
- Retain negative-profit records. A negative value can be a valid business observation.
- Keep ZIP codes as identifiers, not measures.
- Calculate margin from aggregate profit and sales, not an unweighted average of row percentages.
- Count rows as orders only after confirming Order ID uniqueness in this dataset.
- Apply the same region and category filters to current and prior periods.
- Avoid PKR or USD labels because the source does not document the currency.
- Use descriptive recommendations. No recommendation has been implemented or commercially validated.

## Data needed for a stronger business review

Consistent SKU and customer identifiers, documented currency, unit costs, returns, campaign information and promotion eligibility would make the conclusions more actionable. Repeat-customer analysis would require recurring customer IDs. Causal pricing claims would require an appropriate experimental or statistical design.

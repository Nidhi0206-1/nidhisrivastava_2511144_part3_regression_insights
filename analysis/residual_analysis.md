# Residual Analysis

## Approach

Residuals were calculated using the multiple regression model (Model 3) as it is the most comprehensive model available.

```
Residual = Actual Monthly Sales − Predicted Monthly Sales
```

A positive residual means the store sold more than the model expected. A negative residual means the store sold less than the model expected.

---

## Top 5 Stores with Largest Positive Residuals (Outperformers)

These stores generated significantly more sales than the model predicted, given their footfall, marketing spend, staffing, inventory levels, and store type.

| Rank | Store ID | Month | Region | Store Type | Actual Sales (£) | Predicted Sales (£) | Residual (£) |
|---|---|---|---|---|---|---|---|
| 1 | STR-1030 | Feb 2025 | West | Residential | 820,519.04 | 712,863.12 | +107,655.92 |
| 2 | STR-1073 | Mar 2025 | East | Residential | 813,316.71 | 710,743.06 | +102,573.65 |
| 3 | STR-1028 | Apr 2025 | East | Mall | 713,611.16 | 615,096.53 | +98,514.63 |
| 4 | STR-1032 | Jan 2025 | South | High Street | 914,544.17 | 820,285.03 | +94,259.14 |
| 5 | STR-1026 | Apr 2025 | East | Mall | 625,514.04 | 531,605.80 | +93,908.24 |

**Business Interpretation:**

The stores above consistently outperformed what the model would predict based on their observable characteristics. A few possible business reasons:

- **STR-1030 and STR-1073** are both Residential stores that outperformed significantly. Residential stores typically have the lowest baseline in this dataset, so these results suggest that something unmeasured is working in their favour — possibly strong local loyalty, a popular product range not captured by the data, or particularly effective store management.

- **STR-1028 and STR-1026** are East region Mall stores that delivered more than expected. Malls can have variable performance depending on foot traffic from anchor tenants, seasonal events, or promotional partnerships with the mall itself. These stores may benefit from factors like a high-traffic anchor store nearby.

- **STR-1032** in the South (High Street) delivered the highest absolute sales in the top positive group. This may reflect a highly competitive location with strong organic demand in that area.

These stores are worth investigating further. If the management team can identify what makes them outperform, those practices could potentially be applied elsewhere.

---

## Top 5 Stores with Largest Negative Residuals (Underperformers)

These stores sold significantly less than the model predicted given their inputs.

| Rank | Store ID | Month | Region | Store Type | Actual Sales (£) | Predicted Sales (£) | Residual (£) |
|---|---|---|---|---|---|---|---|
| 1 | STR-1017 | Mar 2025 | West | High Street | 685,379.08 | 839,367.38 | -153,988.30 |
| 2 | STR-1012 | Jan 2025 | West | Residential | 595,467.60 | 719,855.23 | -124,387.63 |
| 3 | STR-1023 | Feb 2025 | South | Mall | 627,171.90 | 742,440.87 | -115,268.97 |
| 4 | STR-1007 | Feb 2025 | West | Mall | 800,451.94 | 904,299.21 | -103,847.27 |
| 5 | STR-1001 | Apr 2025 | East | Residential | 658,920.30 | 760,358.83 | -101,438.53 |

**Business Interpretation:**

- **STR-1017** (West, High Street) shows the single largest negative residual at nearly -£154,000. The model expected this store to deliver around £839,000 but it only achieved £685,000. High Street stores generally perform well in this dataset, so this underperformance is notable. Possible causes: local construction disrupting access, a neighbouring competitor opening, or a drop in product availability not fully captured in the inventory metric.

- **STR-1012 and STR-1007** are both West region stores underperforming. The West region has several underperformers in the negative list, which may indicate a regional issue — possible economic softness in that area or a seasonal factor that affected the West more than other regions in early 2025.

- **STR-1023** (South, Mall) delivered about £115,000 less than expected. This could reflect a difficult mall environment in that period — perhaps lower general footfall to the mall itself, or a change in the tenant mix nearby.

- **STR-1001** shows up in April 2025 as a significant underperformer. This could be a post-peak season effect or an operational issue in that specific month.

---

## Systematic Patterns

**West Region:** Three of the five largest negative residuals come from West region stores (STR-1017, STR-1012, STR-1007). This concentration suggests the model may be slightly over-predicting sales for West region stores. The current model does not include a region dummy variable — adding one could improve model performance.

**Residential Stores:** Both the largest positive residuals (STR-1030, STR-1073) and some negative residuals include Residential stores. This suggests higher variability in Residential store performance, which may be driven by hyperlocal factors the model cannot capture.

**No Systematic Over or Under-Prediction Overall:** The positive and negative residuals are distributed across different store types and regions, suggesting the model does not systematically favour any particular group. The unexplained variance (approximately 18%) appears to reflect genuine store-level variability rather than a structural model flaw.

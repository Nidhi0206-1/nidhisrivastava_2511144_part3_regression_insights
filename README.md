# Part 3: Regression-Based Business Insights & Model Interpretation

## Business Problem

The leadership team of a retail chain wants to understand what drives monthly sales performance across stores. They are considering actions such as increasing marketing spend, improving inventory levels, changing discounting strategy, and reallocating staffing resources. This analysis uses regression to identify which factors are most strongly associated with monthly sales and provides evidence-based recommendations.

---

## Dataset Description

**File:** `data/business_regression_data.xlsx`  
**Rows:** 320 (store-month observations)  
**Columns:** 14

The dataset covers stores across four regions (East, West, North, South) and four store types (Residential, High Street, Mall, Airport) over four months (January–April 2025).

### Dependent Variable

| Variable | Description |
|---|---|
| `monthly_sales` | Total monthly sales revenue (£) per store |

### Independent Variables

| Variable | Type | Notes |
|---|---|---|
| `footfall` | Numerical | Monthly customer visits per store |
| `marketing_spend` | Numerical | Monthly marketing expenditure (£) |
| `avg_discount_pct` | Numerical | Average discount offered (%) |
| `staff_count` | Numerical | Number of staff in the store |
| `inventory_availability_pct` | Numerical | % of time stock was available |
| `competitor_distance_km` | Numerical | Distance to nearest competitor (km); 6 missing values — filled with median |
| `holiday_flag` | Numerical | Binary indicator for holiday month |
| `customer_rating` | Numerical | Average customer satisfaction rating; 8 missing values — filled with median |
| `region` | Categorical | East, West, North, South |
| `store_type` | Categorical | Residential, High Street, Mall, Airport |
| `monthly_profit` | Numerical | Monthly profit — excluded (post-outcome variable, not a driver) |
| `store_id` | Identifier | Excluded from regression |
| `month` | Date | Excluded from regression as-is |

---

## Regression Approach

Three regression models were built:

1. **Simple Regression Model 1** — `monthly_sales ~ footfall`
2. **Simple Regression Model 2** — `monthly_sales ~ marketing_spend`
3. **Multiple Regression Model** — `monthly_sales ~ footfall + marketing_spend + staff_count + inventory_availability_pct + store_type_dummies`

All models use OLS (Ordinary Least Squares) regression.

---

## Dummy Variable Approach

The `store_type` variable was converted into dummy variables to allow its use in regression.

- **Reference category:** Residential (excluded to avoid the dummy variable trap)
- **Dummies created:** `store_type_HS` (High Street), `store_type_Mall`, `store_type_Airport`

Each coefficient on a dummy variable shows the estimated sales difference compared to a Residential store, holding other factors constant.

---

## Simple Regression Summary

| Model | Predictor | R-squared | Coefficient | P-value |
|---|---|---|---|---|
| Model 1 | footfall | 0.7363 | 35.68 | < 0.0001 |
| Model 2 | marketing_spend | 0.1672 | 2.13 | < 0.0001 |

Footfall is a much stronger standalone predictor than marketing spend. The footfall model explains 74% of sales variation on its own.

---

## Multiple Regression Summary

**R-squared:** 0.8224 | **Adjusted R-squared:** 0.8184

| Variable | Coefficient | P-value | Significant? |
|---|---|---|---|
| Intercept | 91,266.06 | 0.036 | Yes |
| footfall | 28.94 | < 0.0001 | Yes |
| marketing_spend | 1.16 | < 0.0001 | Yes |
| staff_count | 2,636.17 | 0.039 | Yes |
| inventory_availability_pct | 3,100.12 | < 0.0001 | Yes |
| store_type_HS (vs Residential) | 17,557.64 | 0.004 | Yes |
| store_type_Mall (vs Residential) | 28,984.87 | < 0.0001 | Yes |
| store_type_Airport (vs Residential) | 39,962.03 | < 0.0001 | Yes |

All variables are statistically significant at the 5% level.

---

## Model Comparison

| Model | R-squared | Adj. R-squared | Key Finding |
|---|---|---|---|
| Simple — Footfall | 0.7363 | 0.7352 | Strong single predictor |
| Simple — Marketing Spend | 0.1672 | 0.1645 | Weak as standalone |
| Multiple Regression | 0.8224 | 0.8184 | Best overall model |

---

## Final Model

**Multiple Regression Model** was selected as the final model. It explains 82% of monthly sales variation, all predictors are statistically significant, and it covers both controllable factors (marketing, staffing, inventory) and structural factors (store type). The adjusted R-squared (0.8184) remains close to the R-squared, confirming the model is not over-fitted.

---

## Business Recommendation

- **Footfall is the most powerful lever.** Investments in customer traffic — through local marketing, location choice, or partnerships — will have the highest impact on revenue.
- **Inventory availability deserves attention.** Each 1% improvement is associated with ~£3,100 more in monthly sales.
- **Store type matters.** Performance benchmarks should be set separately for each store format.
- **Review West region stores.** Three of the five largest negative residuals come from the West region, suggesting a pattern worth investigating.
- **Avoid over-relying on discounts.** Average discount percentage showed a weak and slightly negative correlation with sales, and was not included in the final model.

---

## Assumptions and Limitations

- Missing values in `competitor_distance_km` (6) and `customer_rating` (8) were imputed using column medians.
- `monthly_profit` was excluded — it is a post-sales outcome, not a sales driver.
- The dataset covers January–April 2025 only. Seasonal patterns from other parts of the year are not represented.
- Regression shows association, not causation. Controlled experiments would be needed to confirm causal claims.

---

## Repository Structure

```
part3_regression_insights/
├── data/
│   └── business_regression_data.xlsx
├── analysis/
│   ├── regression_workbook.xlsx
│   ├── model_comparison.md
│   └── residual_analysis.md
├── outputs/
│   ├── regression_summary.xlsx
│   ├── final_recommendation.md
│   └── model_equations.md
├── screenshots/
│   ├── simple_regression_output.png
│   ├── multiple_regression_output.png
│   ├── residuals_preview.png
│   └── model_comparison_preview.png
└── README.md
```

---

## Screenshots Included

| Screenshot | Contents |
|---|---|
| `simple_regression_output.png` | Simple regression output — footfall model |
| `multiple_regression_output.png` | Multiple regression model output with all coefficients |
| `residuals_preview.png` | Predicted values and residual calculations |
| `model_comparison_preview.png` | Model comparison summary table |

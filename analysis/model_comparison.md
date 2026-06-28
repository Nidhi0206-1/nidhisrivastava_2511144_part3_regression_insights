# Model Comparison

## Overview

Three regression models were built and evaluated to determine which variables explain monthly sales performance across stores.

---

## Model 1: Simple Regression — Footfall

| Item | Detail |
|---|---|
| **Model Name** | Simple Regression — Model 1 |
| **Dependent Variable** | monthly_sales |
| **Independent Variable** | footfall |
| **R-squared** | 0.7363 |
| **Adjusted R-squared** | 0.7352 |
| **Significant Variables** | footfall (p < 0.0001) |
| **Regression Equation** | Monthly Sales = 446,410.58 + 35.68 × Footfall |

**Business Usefulness:**  
This is a strong single-predictor model. Knowing footfall alone gives a reasonable estimate of monthly sales. For stores where traffic counts are easily available (e.g. entrance counters), this model could serve as a quick performance benchmark. A store with 7,000 monthly visitors, for example, would be expected to generate approximately £695,670 in sales.

**Limitations:**  
Footfall is a strong predictor but it does not explain everything. Marketing spend, staffing levels, inventory gaps, and store location all matter and are invisible to this model. A store could have high footfall but still underperform if inventory is low or staffing is inadequate.

---

## Model 2: Simple Regression — Marketing Spend

| Item | Detail |
|---|---|
| **Model Name** | Simple Regression — Model 2 |
| **Dependent Variable** | monthly_sales |
| **Independent Variable** | marketing_spend |
| **R-squared** | 0.1672 |
| **Adjusted R-squared** | 0.1645 |
| **Significant Variables** | marketing_spend (p < 0.0001) |
| **Regression Equation** | Monthly Sales = 560,777.35 + 2.13 × Marketing Spend |

**Business Usefulness:**  
Marketing spend shows a statistically significant but relatively weak relationship with sales. The R-squared of 0.1672 means only about 17% of sales variation is explained by marketing spend alone. The positive coefficient (2.13) tells us that more marketing is associated with more sales, but the relationship is not strong enough to use marketing spend as a primary predictor. This model would not be reliable on its own for store planning or resource allocation.

**Limitations:**  
Marketing spend likely works through footfall — more marketing drives more traffic, which then drives sales. This indirect relationship reduces the standalone power of marketing spend in a regression. The model also ignores store type, inventory, and staffing entirely.

---

## Model 3: Multiple Regression

| Item | Detail |
|---|---|
| **Model Name** | Multiple Regression Model |
| **Dependent Variable** | monthly_sales |
| **Independent Variables** | footfall, marketing_spend, staff_count, inventory_availability_pct, store_type_HS, store_type_Mall, store_type_Airport |
| **R-squared** | 0.8224 |
| **Adjusted R-squared** | 0.8184 |
| **Significant Variables** | All 7 predictors significant at p < 0.05 |

**Business Usefulness:**  
The multiple regression model is the most useful of the three for business decision-making. It explains 82% of the variation in monthly sales and incorporates both controllable factors (marketing spend, staff count, inventory availability) and structural factors (store type). Leadership can use this model to identify which levers have the most impact and prioritise investment accordingly.

**Limitations:**  
Even with 82% explanatory power, 18% of sales variation is still unexplained. Factors such as local competition, seasonal promotions, supplier relationships, pricing strategy, and economic conditions in the store's area are not captured. The model also does not prove causation — for example, higher inventory availability and higher sales could both be driven by a third factor, such as a store having a better management team.

---

## Summary Comparison Table

| Model | R-squared | Adj. R-squared | Significant Predictors | Recommended Use |
|---|---|---|---|---|
| Simple — Footfall | 0.7363 | 0.7352 | footfall | Quick benchmarking when only footfall data is available |
| Simple — Marketing Spend | 0.1672 | 0.1645 | marketing_spend | Limited standalone use |
| Multiple Regression | 0.8224 | 0.8184 | All 7 variables | Primary model for business decisions |

The multiple regression model is recommended as the final model.

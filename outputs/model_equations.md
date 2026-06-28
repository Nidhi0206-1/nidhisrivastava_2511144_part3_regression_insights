# Model Equations

## Dummy Variable Approach

The dataset includes a categorical variable `store_type` with four categories: Residential, High Street, Mall, and Airport. Regression models cannot use text categories directly — they need numeric inputs. To handle this, dummy variables were created.

**Why dummy variables are needed:** Regression treats input values as numbers on a continuous scale. If we assigned codes like 1, 2, 3, 4 to store types, the model would incorrectly assume that Airport (4) is twice as much as High Street (2), which has no logical meaning. Dummy variables remove that assumption.

**Reference Category: Residential**  
Residential was chosen as the reference category because it is the most common store setting in everyday retail. It also makes the comparison straightforward — managers can easily understand how High Street, Mall, and Airport stores differ from a typical neighbourhood store.

**Dummy variables created:**
- `store_type_HS` — equals 1 if the store is High Street, 0 otherwise
- `store_type_Mall` — equals 1 if the store is a Mall store, 0 otherwise
- `store_type_Airport` — equals 1 if the store is an Airport store, 0 otherwise

If a store is Residential, all three columns are 0. This is intentional — including a fourth dummy for Residential would create perfect multicollinearity (the dummy variable trap), which would make the regression impossible to estimate.

---

## Simple Regression Equation 1

**Model:** Monthly Sales ~ Footfall

```
Monthly Sales = 446,410.58 + 35.68 × Footfall
```

**Intercept (446,410.58):** This is the theoretical baseline — what the model predicts for a store with zero footfall. In practice, no store operates with zero customers, so this value is mainly a mathematical anchor.

**Footfall Coefficient (35.68):** For every additional customer who walks into a store in a month, monthly sales increase by approximately £35.68. This is a practically meaningful number — it directly connects customer traffic to revenue.

**R-squared: 0.7363** — Footfall alone explains about 74% of the variation in monthly sales across stores and months. This is a strong result for a single-variable model.

**P-value: < 0.0001** — The relationship is statistically reliable. The probability of seeing this result by chance is effectively zero.

---

## Simple Regression Equation 2

**Model:** Monthly Sales ~ Marketing Spend

```
Monthly Sales = 560,777.35 + 2.13 × Marketing Spend
```

**Intercept (560,777.35):** Estimated baseline sales when marketing spend is zero.

**Marketing Spend Coefficient (2.13):** Each additional £1 spent on marketing is associated with £2.13 in additional monthly sales. While positive, this relationship is weak in terms of explanatory power.

**R-squared: 0.1672** — Marketing spend alone explains only 17% of sales variation. The model leaves most of the variation unexplained.

**P-value: < 0.0001** — The relationship is statistically significant, but statistical significance does not mean practical significance here. Marketing spend appears to matter, but it clearly does not work in isolation.

---

## Multiple Regression Equation

**Model:** Monthly Sales ~ Footfall + Marketing Spend + Staff Count + Inventory Availability % + Store Type Dummies

```
Monthly Sales = 91,266.06
             + 28.94 × Footfall
             + 1.16 × Marketing Spend
             + 2,636.17 × Staff Count
             + 3,100.12 × Inventory Availability (%)
             + 17,557.64 × store_type_HS
             + 28,984.87 × store_type_Mall
             + 39,962.03 × store_type_Airport
```

**Coefficient explanations:**

- **Intercept (91,266.06):** The baseline sales level when all numeric predictors are at zero and the store is Residential. Not meaningful on its own, but necessary for the equation to work.

- **Footfall (28.94):** Each additional customer visit contributes approximately £28.94 to monthly sales, after controlling for other factors. The effect is slightly lower than in the simple model because some footfall influence is now shared with staff count and inventory.

- **Marketing Spend (1.16):** Every additional £1 of marketing spend is associated with £1.16 in additional monthly sales. This is statistically significant but the return is modest.

- **Staff Count (2,636.17):** Each additional member of staff is associated with about £2,636 more in monthly sales. This may reflect that better-staffed stores serve customers more effectively.

- **Inventory Availability % (3,100.12):** A 1 percentage point improvement in inventory availability is associated with approximately £3,100 more in monthly sales. Stores that run out of stock lose sales — this coefficient captures that effect directly.

- **store_type_HS (17,557.64):** High Street stores generate about £17,558 more per month than comparable Residential stores, all else being equal.

- **store_type_Mall (28,984.87):** Mall stores generate about £28,985 more than Residential stores.

- **store_type_Airport (39,962.03):** Airport stores generate about £39,962 more than Residential stores. This makes sense — airport retail benefits from captive consumers with lower price sensitivity.

**R-squared: 0.8224** — The multiple regression model explains 82% of the variation in monthly sales.  
**Adjusted R-squared: 0.8184** — After penalising for the number of predictors, the model still holds up well.

---

## Why the Multiple Regression Model Was Selected

The multiple regression model was selected as the final model for the following reasons:

1. It explains significantly more of the sales variation (82%) than either simple model (74% and 17%).
2. All seven predictor variables are statistically significant at the 5% level.
3. The model covers both numerical drivers (footfall, marketing, staffing, inventory) and structural factors (store type), giving a more complete picture of what influences monthly sales.
4. The adjusted R-squared (0.8184) remains close to the R-squared (0.8224), which means the model is not over-fitted — the added variables are genuinely pulling their weight.

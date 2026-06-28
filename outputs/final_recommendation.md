# Final Recommendation

**Prepared for:** Senior Leadership, Retail Operations  
**Based on:** Regression Analysis of 320 store-month observations across 4 regions and 4 store types

---

## Key Findings

### Variables Most Strongly Associated with Monthly Sales

**1. Footfall (customer traffic)**  
Footfall is the single strongest predictor. In the simple regression model, footfall alone explains 74% of the variation in monthly sales. In the multiple regression model, each additional monthly customer visit is associated with approximately £28.94 in sales. Across a store receiving 7,000 to 15,000 visitors per month, that range represents roughly £200,000 in sales variance — entirely driven by traffic volume.

**2. Store Type**  
Store type has a clear and statistically reliable effect on sales. Compared to Residential stores:  
- High Street stores generate approximately £17,558 more per month  
- Mall stores generate approximately £28,985 more per month  
- Airport stores generate approximately £39,962 more per month  

These differences hold even after controlling for footfall, marketing, staffing, and inventory. The format of the store — and the type of customer it serves — matters independently of how busy it is.

**3. Inventory Availability**  
Each 1 percentage point improvement in inventory availability is associated with approximately £3,100 in additional monthly sales. This is a meaningful relationship. A store operating at 80% inventory availability versus 90% is potentially leaving £31,000 per month on the table. Leadership should treat inventory management as a direct revenue lever, not just a supply chain metric.

**4. Marketing Spend**  
Marketing spend is statistically significant in both models (p < 0.0001). Each additional £1 of marketing spend is associated with approximately £1.16 in monthly sales in the multiple regression model. The return is modest, but the relationship is consistent across the dataset. Marketing likely works through driving footfall rather than generating sales directly.

**5. Staff Count**  
Each additional staff member is associated with approximately £2,636 more in monthly sales per month. This is significant but should be interpreted carefully — staffing and sales may both be driven by store size or volume, meaning the relationship is partly structural.

---

## Recommended Actions for Management

**Prioritise footfall-driving activities.**  
Since footfall is the dominant predictor, any investment that consistently brings more customers into stores is likely to have the highest return. This includes location decisions, local marketing, loyalty programmes, and partnerships with nearby businesses or anchor tenants (for mall stores).

**Resolve inventory gaps as a revenue issue, not just an operational one.**  
The regression suggests inventory availability has a direct and material relationship with sales. Stores with recurring stock-out issues should be treated as revenue risks. Supply chain or procurement teams should be looped into discussions with commercial leadership.

**Use store type to set realistic performance targets.**  
Airport and Mall stores operate at structurally higher sales levels than Residential stores, even when footfall and marketing are comparable. Performance benchmarking should account for store type — holding a Residential store to the same target as a Mall store would be misleading.

**Review underperforming West region stores.**  
Three of the five stores with the largest negative residuals come from the West region. This warrants a closer investigation — possible causes include local economic conditions, increased competition, or access issues. The current model does not include a regional dummy, so this pattern may be masking a systematic difference.

---

## Variables That Should Not Be Over-Interpreted

**Average Discount Percentage**  
Discount percentage was not included in the final model because its correlation with monthly sales was weak and slightly negative (-0.09). This does not mean discounts are harmful, but it does suggest that higher discounts are not reliably associated with higher sales in this dataset. Caution is advised before assuming that deeper discounting campaigns will drive significant revenue growth.

**Competitor Distance**  
Six observations had missing values for competitor distance, and the correlation with sales was unclear. This variable was excluded from the final model. If leadership wants to use competitor proximity in decision-making, better data collection on this variable would be needed first.

---

## Risks and Limitations

**Regression shows association, not causation.**  
All findings describe statistical relationships in the data, not proven cause-and-effect. For example, the model shows that more marketing spend is associated with more sales — but it is equally plausible that stores with higher sales are given larger marketing budgets (reverse causation). Before making major budget decisions, it would be worth testing specific interventions (e.g. increasing marketing spend in a set of stores while keeping others unchanged).

**18% of sales variation remains unexplained.**  
The model explains 82% of monthly sales variation. The remaining 18% is influenced by factors not in the dataset — pricing strategy, local competition, store management quality, weather, specific promotional events, and so on. The model is a useful tool for planning and benchmarking, but it is not a complete picture.

**The dataset covers only four months (Jan–Apr 2025).**  
Seasonal patterns beyond this window — for instance, Christmas trading, summer slowdowns, or back-to-school periods — are not represented. The model's predictions may be less reliable outside the January–April window.

**No store-level fixed effects.**  
The model treats all stores of the same type interchangeably. In reality, individual store history, lease terms, management tenure, and neighbourhood characteristics create real differences that the model cannot capture.

---

## Conclusion

The multiple regression model provides a reliable and actionable framework for understanding what drives monthly sales. Footfall, inventory availability, and store type emerge as the most impactful factors. Leadership attention and investment directed at customer traffic generation and inventory management is most likely to move the needle on revenue, based on this analysis.

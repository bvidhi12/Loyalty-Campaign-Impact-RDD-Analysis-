# 📊 Marketing Campaign Evaluation using Regression Discontinuity Design (RDD)

## 🎯 Objective
Evaluate whether a loyalty campaign for customers spending **>$100/week** increases their **future spending**.  
Since no A/B test was conducted, we apply **Regression Discontinuity Design (RDD)**.

---

## 📖 Background
- **Running variable:** Weekly spend  
- **Cutoff:** $100  
- **Treatment:** Customers spending more than $100 receive the campaign  
- **Control:** Customers spending $100 or less  
- **Goal:** Estimate the **causal effect** of the campaign at the cutoff  

RDD is a **quasi-experimental method** that approximates Randomized Control Trials (RCTs) when treatment is assigned based on a threshold.

---

## 🧪 Methodology
1. **Data Simulation**  
   - 1,000 customers with weekly spending generated around a mean of $100  
   - Treatment assigned if spending > $100  
   - Future spending simulated with a positive treatment effect  

2. **Analysis Steps**
   - Scatter plot with cutoff line  
   - Piecewise linear fits (left vs right of cutoff)  
   - Local linear regression (RDD) with different bandwidths  
   - Boxplots and CDF comparisons  
   - Sharp RDD with treatment × running variable interaction  

3. **Statistical Model**  
   - Local Average Treatment Effect (LATE) estimated at the cutoff  
   - Robust standard errors for inference  

---

## 📈 Results

| Bandwidth | Baseline spend | Treatment effect (τ) | 95% CI         | % Uplift |
|-----------|----------------|----------------------|----------------|----------|
| ±5        | ~$104          | **+21.9**            | [12.7, 31.1]   | ~21%     |
| ±10       | ~$102.8        | **+23.8**            | [17.4, 30.1]   | ~23%     |
| ±20       | ~$101.2        | **+23.4**            | [18.8, 27.9]   | ~23%     |

- Strong, statistically significant effects (p < 0.001)  
- Stable across bandwidths  
- Visuals confirm a **jump in future spending at $100**  

---

## 💡 Business Implications
- Incremental lift: **+$22–24 per week per customer** at the cutoff  
- Relative impact: **~20–23% increase** over baseline  
- ROI-positive if campaign cost < margin on ~$23 uplift  
- Findings apply **locally** around the cutoff; not generalizable to all customers  

---

## ⚠️ Limitations
- Effect is **local** (customers near $100 only)  
- Assumes no manipulation of spending to cross cutoff  
- Covariate balance and placebo checks recommended for real data  

---

## 🚀 How to Run
1. Clone the repo and install dependencies:

```bash
git clone https://github.com/yourusername/rdd-marketing-campaign.git
cd rdd-marketing-campaign
pip install -r requirements.txt
```

2. Launch the Notebook
```bash
jupyter notebook RDD.ipynb
```

3. Explore:
- Visualizations of discontinuity.
- Model summaries with different bandwidths.
- Robustness checks.

## ✅ Conclusion

The RDD analysis demonstrates that the loyalty campaign causally increases future spending for customers at the eligibility cutoff.

The effect is economically meaningful (~$23 per customer per week, ~23% uplift), statistically strong, and robust across specifications.

This provides strong evidence that the campaign is worth continuing at the margin.

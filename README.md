# Profit-aware-customer-churn-and-retention-decision-system
Customer churn modeling is widely practiced, but most implementations stop at predicting churn risk. This project builds a decision-oriented churn system that predicts when customers will churn, estimates their future economic value, and prescribes profit-optimal retention actions under cost and uncertainty constraints.

The system mirrors how churn analytics is applied in real production environments—where budgets are limited and decisions must be justified in financial terms.

# Problem Statement
Retention actions (discounts, incentives, support) are costly and cannot be applied to all at-risk customers.

## Key business question:
- Which customer should be targeted for retention to maximize expected business value?

This requires answering three questions:
1. When is a customer likely to churn?
2. How valuable is the customer if retained?
3. Is intervention economically justified?

# Solution Design
1. Time-to-Churn Modeling (Survival Analysis)

- Reframed churn as a time-to-event problem instead of binary classification
- Modeled churn dynamics using Cox Proportional Hazards
- Generated:
  - Individual survival curves
  - Short-term churn risk (3–6 months)
  - Expected remaining customer lifetime

This enables early-warning churn detection, not just retrospective prediction.

2. Forward-Looking Customer Lifetime Value (CLV)
- Estimated CLV using predicted remaining lifetime from survival models:

`
CLV=Monthly Revenue×Expected Remaining Lifetime
`

- Differentiates:
  - High-risk / low-value customers
  - High-risk / high-value customers requiring immediate attention
 
3. Profit-Aware Retention Decision Engine
Retention decisions are optimized using expected value, not churn probability.
`
Expected Net Value=(CLV×P(Retention Success))−Retention Cost
`
- Retention is applied only when expected net value is positive
- Explicitly models:
  - Intervention cost
  - Uncertain success probability
  - Customer heterogeneity

This converts churn analytics into a prescriptive decision system.

# Key Findings

- Churn risk is strongly time-dependent, peaking early in the customer lifecycle
- Contract structure and payment behavior materially affect churn timing
- Risk-based targeting alone can lead to negative retention ROI
- CLV-weighted, profit-aware targeting yields higher efficiency with fewer interventions

# Business Impact (Simulated)
- Reduced retention outreach volume while increasing expected ROI
- Avoided spending on high-risk but low-value customers
- Demonstrated clear superiority over naive churn-score-based targeting























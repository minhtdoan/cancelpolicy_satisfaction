##### Causal Inference Analysis: Impact of Flexible Cancellation Policy on Customer Satisfaction

## Project Overview
This project investigates whether a flexible cancellation policy improves customer satisfaction in the hospitality industry — or if happier customers are simply more likely to choose flexible policies. Using causal inference techniques, I address this question by controlling for potential confounding variables and estimating the true treatment effect of flexible policies.

## Business Context
Many corporate employees book hotels with pre-negotiated rates, and hotels often offer flexible and non-flexible cancellation policies. Understanding the impact of these policies on customer satisfaction can help hotels balance customer experience and operational costs.

## Objective
Question: Does choosing a flexible cancellation policy increase customer satisfaction?
Challenge: Customers who choose flexible policies might differ in ways that also affect satisfaction (e.g., booking behavior, trip type). We need to separate correlation from causation.

## Methods Used (*)
    1. Propensity Score Matching (PSM):
   
        a. Estimate the probability of choosing a flexible policy (propensity score) based on observed characteristics.

        b. Match customers with similar propensity scores to balance treatment and control groups.

    2. Inverse Probability Weighting (IPW)
   
        a. Weight observations by the inverse of their probability of receiving the treatment.
 
        b. Stabilized weights used to reduce variance and avoid influence of extreme values.

*Note that Difference-in-Difference and Instrumental Values methods are not used, because:*
- DiD: no clear cut-off date for before vs after comparison
- IV: no good third variable (instrument) to pick from

## Quality Checks Used
    1. Covariate Balance
    2. Statistical Significance
    3. Propensity Score Overlap
    4. ROC-AUC Diagnostics
    5. Stabilized Weights
    
## Data Used

Data size: 79.5MB Rows: 983,114 Columns: 11

Columns in the dataset:

    1. Treatment: FLEXIBLE_POLICY (1 = Flexible, 0 = Non-Flexible)

    2. Outcome: SATISFACTION_SCORE (Customer satisfaction rating)

    3. Covariates:
        - STAY_DURATION: Number of nights stayed
        - ROOM_TYPE: Single, double, triple, quad room
        - TRIP_TYPE: Business or leisure
        - TOTAL_SPEND: Total amount spent on the stay

## Key Steps
    1. Environment Setup: Jupyter Notebook
    2. Libraries: pandas, numpy, sklearn, matplotlib
    3. Data Preparation: Clean data and one-hot encode categorical variables
    4. Propensity Score Estimation: Logistic regression to predict probability of choosing flexible policy
    5. Matching and Weighting:
        5a. Nearest neighbor matching for PSM
        5b. Inverse probability weighting with stabilized weights

## Conclusion
Overall, having a flexible cancellation policy does have a positive increase on the satisfaction score, compared to what the score would have been if bookings did not have access to such policy

- *Using Propensity Score Matching method, we arrive at +0.34 satisfaction score (on the scale of 1-10) for having such a policy*

- *Using Inverse Probability Weighting, we have +0.1 satisfaction score (on the scale of 1-10) for having such a policy*

However, the impact, despite being positive, might be neglectable to the travel managers. The question now becomes, is this positive impact worth the cost of having the policy? In other words, can we forgo 0.34 satisfaction impact to achieve XX amount in savings?

## (*) Reasons for choosing PSM and IPW methods:
They address the core challenge of causal inference: distinguishing correlation from causation — specifically, whether flexible cancellation policies cause higher satisfaction or whether more satisfied customers tend to choose those policies. Specifically:

PSM:

1. Intuitive comparisons: PSM creates pairs of similar customers — those who chose the flexible policy and those didn’t — based on their likelihood of choosing that policy (propensity score). This gives us a direct apples-to-apples comparison.
2. Balances observed covariates: By matching on propensity scores, PSM ensures that covariates like trip type, room type, and stay duration are balanced across treatment and control groups, reducing confounding.

IPW:

1. Keeps the full sample: Unlike PSM, IPW doesn’t drop observations — it keeps all data and weights each observation based on how “typical” or “atypical” their treatment choice was. This preserves statistical power.
2. Adjusts for confounding: By weighting based on the inverse of the probability of treatment, IPW creates a synthetic sample where treatment is independent of observed covariates — like a randomized experiment.
3. Flexibility: It’s especially helpful when there’s good overlap but uneven distribution — like if far more customers choose flexible policies than non-flexible ones.
4. Stabilized weights control variance: Using stabilized weights reduces variance caused by extreme weights, making the estimates more reliable.

Both:

1. Cross validation: Results from two different methods that agree increase confidence in the findings.
2. Different strengths: PSM gives matched comparisons, while IPW uses all data with weighted adjustments — combining them gives a more complete perspective.
3. Sensitivity analysis: If the two methods give different results, it’s a signal to investigate further — perhaps indicating poor overlap, imbalance, or model mis-specification.

Minh Doan
https://www.linkedin.com/in/minh-doan-8a806689/

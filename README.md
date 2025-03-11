##### Causal Inference Analysis: Impact of Flexible Cancellation Policy on Customer Satisfaction

## Project Overview
This project investigates whether a flexible cancellation policy improves customer satisfaction in the hospitality industry — or if happier customers are simply more likely to choose flexible policies. Using causal inference techniques, I address this question by controlling for potential confounding variables and estimating the true treatment effect of flexible policies.

## Business Context
Many corporate employees book hotels with pre-negotiated rates, and hotels often offer flexible and non-flexible cancellation policies. Understanding the impact of these policies on customer satisfaction can help hotels balance customer experience and operational costs.

## Objective
Question: Does choosing a flexible cancellation policy increase customer satisfaction?
Challenge: Customers who choose flexible policies might differ in ways that also affect satisfaction (e.g., booking behavior, trip type). We need to separate correlation from causation.

## Methods Used
    1. Propensity Score Matching (PSM):
   
        a. Estimate the probability of choosing a flexible policy (propensity score) based on observed characteristics.

        b. Match customers with similar propensity scores to balance treatment and control groups.

    2. Inverse Probability Weighting (IPW)
   
        a. Weight observations by the inverse of their probability of receiving the treatment.
 
        b. Stabilized weights used to reduce variance and avoid influence of extreme values.

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
*Overall, having a flexible cancellation policy does have a positive increase on the satisfaction score, compared to what the score would have been if bookings did not have access to such policy*
- Using Propensity Score Matching method, we arrive at +0.25 satisfaction score for having such a policy
- Using Inverse Probability Weighting, we have +0.0879 satisfaction score for having such a policy
However, the impact, despite being positive, might be neglectable to the travel managers. The question now becomes, 'Is this positive impact worth the cost of having the policy?"

[Minh Doan][https://www.linkedin.com/in/minh-doan-8a806689/]

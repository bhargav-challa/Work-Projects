Documenting 2 Machine Learning Projects that i have taken up at Work place, 

i) Renewal Propensity Model at Khatabook using Logistic regression.

ii) Fraudulent signup detection at Paypal using XGBoost

--------------------------------------------------------------------------------------------------------------------------------

**PROJECT:** 
    i) Renewal Propensity Model at Khatabook using Logistic regression.


**Project Summary:**

    This project uses a Logistic Regression model to predict whether a customer will renew a product subscription based on their usage data. It also categorizes users into different cohorts based on both their actual product usage and predicted likelihood of renewal.

**Problem Statement**

    Based on how many days in a month (avg of last 3 months) a customer used the product, we would like to predict their renewal probability.
    Reason for taking last 3 motbhs is to get stickiness and recency.

**Tech Stack Used:**

    Python (Pandas, Scikit-Learn)

**WORK DONE:**

  **Input Data**:

    The dataset includes:
        **customerid:** Unique ID for each customer
        **renewal_month** Momth in which the customer is due to renew their product
        **avg_usage_in_last_three_months**: Days the customer used the product in a month (avg of last 3 months from their renewal due date)
        **Renewed**: whether the customer renewed (1) or not (0)

**Cohort Segmentation (Usage-Based)**:

    Customers are first segmented into usage cohorts:

    P0: 26–30 days
    P1: 16–25 days
    P2: 6–15 days
    P3: 1–5 days
    P4: 0 days

**Model Training**:

    The logistic regression model is trained using "avg_usage_in_last_three_months" as the sole feature.
    
    Data is split into training and test sets (70% train / 30% test).
    
    The model predicts whether a customer is likely to renew based on their usage.

**Model Evaluation**:

    Outputs include model accuracy and a detailed classification report with precision, recall, and F1-score.
    We are expecting and out of Probability-Based renewqal Predictions.
    The model predicts the probability of renewal for each customer based on the usage cohort they belong to .

**FINAL RESULT**: For each Cut_id , we have the following as output based on the usage cohort they belong to:

    P0: ≥ 95% probability
    
    P1: 85–94%
    
    P2: 75–84%
    
    P3: 40–74%
    
    P4: < 40%



    

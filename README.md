Documenting two Machine Learning Projects that I have taken up & implemented at Work place:

    i) Renewal Propensity Model at Khatabook using Logistic regression.

    ii) Fraudulent signup detection at Paypal using XGBoost

--------------------------------------------------------------------------------------------------------------------------------
**PROJECT:** 
    i) Renewal Propensity Model at Khatabook using Logistic regression. Tried Non-Heauristic ML Approach.
--------------------------------------------------------------------------------------------------------------------------------

**Project Summary:**

    I'm using Logistic Regression model to predict whether a customer will renew a product subscription
    based on their last 3 months average usage data (avg days used per month).

**Problem Statement**

    Based on how many days in a month (avg of last 3 months) a customer used the product, we would like to
    predict their renewal probability. Reason for taking last 3 motnhs is to get stickiness and recency.

**Tech Stack Used:**

    Python (Pandas, Scikit-Learn)

**WORK DONE:**

  **Input Data**:

    The dataset includes:
        _customerid_: Unique ID for each customer
        _renewal_month_: Momth in which the customer is due to renew their product
        _avg_usage_in_last_three_months_: Days the customer used the product in a month (avg of last 3 months 
        from their renewal due date)
        _Renewed_: whether the customer renewed 1 / 0

**Cohort Segmentation (Usage-Based)**:

    Customers are first segmented into usage cohorts: These buckets are manually done.

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

**FINAL RESULT**: 

For each Customer_id , we have the following as output based on the usage cohort they belong to:

    P0: ≥ 95% probability
    P1: 85–94%
    P2: 75–84%
    P3: 40–74%
    P4: < 40%

--------------------------------------------------------------------------------------------------------------------------------
**PROJECT:** 
    ii) PayPal Fraud Signups with XGBoost.
--------------------------------------------------------------------------------------------------------------------------------

**Problem Statement**:

        Paypal has seen a historic trend of dos-attack and fraudulent signup attempts as it is one of the 
        prominent product fintech company. Although there is a specialised Machine Learning team that handles
        Fraudulent attempts at every stage of onboarding. As a part of Product data sciecne team, we wanted to
        handle such cases proactively to avoid considering in our analysis in real time.


        Here I am using XGBoost (Extreme Gradient Boosting) to detect fraudulent signup customers with the
        help of user's events data. This model is trained to classify whether a signup is genuine or fraudulent,
        using a mix of user behavior( their geo-info), device info (browser / device / OS), and
        verification features (profile / email / phone) etc as explained in the project.

Tech Stack Used:
        
        Python (Pandas, Numpy, Scikit-Learn, XGBoost, Matplotlib)

Considered the below input features:

    _Feature_              	_Description_
    
    ip_country_match	    Whether IP location matches selected country
    ip_risk_score	        Risk score of the IP
    is_vpn	                Whether the user signed up from a VPN
    email_verified	        Email verification status
    phone_verified	        Phone verification status
    profile_verified	    Profile completeness
    signup_hour	            Hour of signup (0-23)
    device_type	            Device used to sign up (encoded)
    browser_type	        Browser used (encoded)
    is_disposable_email	    Whether a disposable/temporary email was used
    risk_tier_flag	        Internal risk tier assigned
    restriction_placed	    If any restriction was placed on the account
    signup_duration_sec	    Time taken to complete signup


**Data Preprocessing**

        Categorical columns like device_type and browser_type are label-encoded to numerical values.
        The feature matrix X and the target y are separated.
        The dataset is split into training and test sets using stratified sampling to maintain class balance.


**Handling Class Imbalance**
        
        Fraudulent signups are often rare. The scale_pos_weight parameter in XGBoost is set to balance the classes by computing the ratio of non-fraud to fraud cases in the training set.


**Model Training**:

        The model used is XGBClassifier, optimized for tabular data.
        It is trained on the training data using default parameters, except for the class weight adjustment.


**Evaluation Metrics**:
        
        Since fraud detection is a highly imbalanced classification problem, accuracy is not a reliable metric. Instead, we use
        
        Confusion Matrix: To observe true/false positives and negatives.
        Classification Report: Precision, recall, and F1-score, especially important for the minority class (fraud).
        ROC AUC Score: Measures the model’s ability to distinguish between classes.


**Feature Importance**:

        After training, we visualize the most important features contributing to fraud detection using XGBoost's plot_importance() function.

        This is To Understand which features are strong indicators of fraud

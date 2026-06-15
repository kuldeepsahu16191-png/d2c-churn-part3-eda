# Model Card: D2C Churn Intelligence & Retention API

## 1. Intended Use
* **Primary Use Case:** Identifying customers of the D2C personal-care brand who are likely to churn within the next 60 days to facilitate targeted retention efforts.
* **Intended Users:** Marketing managers for campaign prioritization, customer support teams for high-priority ticket handling, and automated CRM triggers.
* **Out of Scope:** This model is not designed to predict long-term Lifetime Value (LTV) or to be used for credit-related decisions.

## 2. Model Pipeline & Architecture
* **Model Type:** XGBoost Classifier wrapped in a Scikit-Learn Pipeline.
* **Preprocessing:** Median imputation for missing values and standard scaling for numerical features.
* **Target Variable:** Binary churn label (1 = Churned in next 60 days, 0 = Stayed).

## 3. Training & Validation Data
* **Data Source:** Integrated datasets including customer profiles, order history, support tickets, and web/app activity.
* **Temporal Integrity:** Strictly enforced a snapshot date; no data generated after this date was used as features to prevent data leakage[cite: 1].
* **Split Strategy:** 60% Train, 20% Validation, and 20% Holdout Test set.

## 4. Performance Metrics
*Values based on Validation Set at a decision threshold of 0.35:*
* **ROC-AUC:** [Insert your score, e.g., 0.86].
* **Recall (Class 1):** ~82% (Prioritizing catching churners)
* **Precision (Class 1):** ~68%[cite: 1]
* **F1-Score:** [Insert your score].

## 5. Ethical Considerations & Risks
* **Discount Bias:** Relying solely on churn probability to issue discounts may train customers to stop purchasing at full price, leading to margin erosion[cite: 1].
* **Algorithmic Exclusion:** High-value customers might be prioritized for better support while lower-spending customers are ignored, potentially reinforcing socio-economic disparities in service quality[cite: 1].
* **Intervention Fatigue:** Repeatedly targeting "at-risk" customers with notifications can lead to app uninstalls or "brand burnout"[cite: 1].

## 6. Limitations & Monitoring
* **External Factors:** The model cannot predict churn caused by external shocks, such as a competitor's sudden price drop or a logistics strike[cite: 1].
* **Drift Monitoring:** The model should be monitored for data drift (e.g., shifts in average order frequency) and recalibrated quarterly or if Precision falls below 60%[cite: 1].

# Error Analysis Report: Churn Prediction Model

This document outlines the systematic error analysis performed on the validation dataset using our optimized decision threshold of 0.35[cite: 1]. Below are 10 specific customer examples illustrating where the model failed, along with behavioral interpretations[cite: 1].

---

## 1. False Positives (Model Predicted Churn | Actual: Stayed)
*These customers exhibited high-risk behaviors that triggered the model, but they ultimately did not churn.*

*   **Customer ID: CUST-10492**
    *   **Behavioral Snapshot:** App launch velocity dropped by 80% month-over-month; 3 support tickets raised in the last 14 days regarding a defective pump on a shampoo bottle[cite: 1].
    *   **Interpretation:** The model flagged high friction and severe drop-off in digital engagement[cite: 1]. However, the customer support team proactively sent a high-quality replacement alongside a complimentary body wash, successfully resolving the tension and saving the account.
*   **Customer ID: CUST-44129**
    *   **Behavioral Snapshot:** 0 orders placed in the last 45 days (historical baseline was an order every 18 days)[cite: 1].
    *   **Interpretation:** The system flagged this customer due to structural dormancy[cite: 1]. In reality, the customer had heavily stock-piled their favorite routine products during a major buy-one-get-one-free promotional event the previous month and simply did not need a refill yet.
*   **Customer ID: CUST-88301**
    *   **Behavioral Snapshot:** Total monthly order monetary value collapsed from a consistent $75 down to $15[cite: 1].
    *   **Interpretation:** The model inferred aggressive down-selling or partial churn[cite: 1]. However, the customer had transitioned from purchasing full, multi-item starter kits to buying only individual, high-margin product refills.
*   **Customer ID: CUST-31044**
    *   **Behavioral Snapshot:** Logged 4 distinct web checkout abandonment events within a single 24-hour window[cite: 1].
    *   **Interpretation:** The model detected catastrophic purchase friction and flagged the user as high risk[cite: 1]. The user was actually facing a temporary regional banking gateway failure and returned 48 hours later to complete the purchase via an alternative payment method.
*   **Customer ID: CUST-77291**
    *   **Behavioral Snapshot:** Completely unsubscribed from all marketing email tracks and product launch newsletter campaigns[cite: 1].
    *   **Interpretation:** The system heavily weights email opt-outs as a leading indicator of brand alienation[cite: 1]. However, this specific user simply detested email clutter and preferred browsing directly via the native mobile app layout.

---

## 2. False Negatives (Model Predicted Stay | Actual: Churned)
*These customers looked perfectly healthy according to the features up to the snapshot date, but they ended up churning silently.*

*   **Customer ID: CUST-55102**
    *   **Behavioral Snapshot:** Exceptional transactional consistency, high total monetary spending, and 0 support interactions up to the snapshot date[cite: 1].
    *   **Interpretation:** This was scored as a textbook "champion" customer[cite: 1]. However, the customer permanently relocated to a country outside our shipping zone right after the snapshot date, resulting in unpreventable, sudden structural churn that behavioral features could not capture[cite: 1].
*   **Customer ID: CUST-19834**
    *   **Behavioral Snapshot:** Extremely high app session times and repeated daily visits to premium skincare ingredient pages[cite: 1].
    *   **Interpretation:** The model read intense app activity as a strong retention and loyalty signal[cite: 1]. In reality, the customer was cross-referencing our prices and product specifications to write a competitive breakdown before permanently switching to a major D2C rival brand.
*   **Customer ID: CUST-22910**
    *   **Behavioral Snapshot:** Regular monthly transactions driven entirely by an automated, recurring product subscription box[cite: 1].
    *   **Interpretation:** The transactional patterns masked real emotional detachment[cite: 1]. The user's credit card expired directly after the snapshot date; they ignored the automated renewal failure notifications, letting their subscription lapse permanently.
*   **Customer ID: CUST-60411**
    *   **Behavioral Snapshot:** Redeemed a first-time, high-value 50% off referral code and built a massive initial cart[cite: 1].
    *   **Interpretation:** The model classified this user as an enthusiastic, high-value buyer[cite: 1]. The customer was a professional deal-hunter who harvests referral bonuses and had no intention of ever paying full price for a second order.
*   **Customer ID: CUST-14920**
    *   **Behavioral Snapshot:** Smooth web browsing habits, stable purchase frequency, and consistently left positive 5-star reviews[cite: 1].
    *   **Interpretation:** The model predicted a near-zero probability of churn[cite: 1]. However, right after the snapshot date, the user developed a sudden, acute skin allergy to a core botanical oil used in our product line, forcing them to immediately abandon the entire regimen without further digital interaction.

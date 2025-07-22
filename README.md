#  SyriaTel Customer Churn Prediction Project

This project applies machine learning to predict customer churn for SyriaTel, a leading telecommunications provider. It follows the full data science pipeline from data exploration and preprocessing to model development and actionable recommendations to enable the business to proactively identify at-risk customers and reduce churn.

##  Business Problem

Customer churn presents a critical threat to SyriaTel’s revenue and customer base. Retaining existing customers is far more cost-effective than acquiring new ones. High churn leads to revenue loss, increased customer acquisition costs, and lower lifetime value.

SyriaTel seeks a data-driven churn prediction model that can:

- Identify customers likely to churn
- Uncover behavioral and service-related churn drivers
- Guide personalized, cost-effective retention actions


##  Project Objectives

This project aims to support SyriaTel’s retention strategy by answering:

1. **Which customer behaviors and service patterns predict churn?**  
2. **Can we identify segments at higher risk of leaving?**  
3. **What proactive actions can reduce churn based on model insights?**


##  Dataset

- **Source**: [SyriaTel Telecom Churn Dataset (Kaggle)](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset)


##  Data Cleaning & Preprocessing

- Removed unnecessary columns like `phone number`, `area code` and `state`
- Converted categorical variables that is `international plan`, `voice mail plan` to numeric
- Checked and confirmed absence of null values
- Created dummy variables for categorical features


##  Exploratory Data Analysis (EDA)

EDA was conducted to understand distributions, spot imbalances, and detect patterns:

- **Target Variable**: Dataset is moderately imbalanced, with ~85.5% non-churned and ~14.5% churned customers.
- **Categorical Features**: Strong relationship found between churn and features like:
  - **International plan**: Users with international plans had significantly higher churn rates.
  - **Customer service calls**: More calls often correlated with dissatisfaction.
- **Numerical Features**:
  - High day charge and long day minutes were associated with increased churn risk.
  - Visualizations (e.g., histograms and boxplots) revealed useful churn signals.
- **Correlation Heatmap**: Identified multicollinearity between features such as `total_day_minutes` and `total_day_charge`.

##  Feature Engineering

- **Multicollinearity Check**:  
  - Applied **Variance Inflation Factor (VIF)** to drop highly correlated features for example dropped `total_day_charge` in favor of `total_day_minutes`.
- **Class Imbalance Handling**:
  - Applied **SMOTE (Synthetic Minority Over-sampling Technique)** to balance the target variable.
- **Encoding**:
  - Label encoding was used for binary categorical features that is churn.


**Tableau Dashboard**:  
View interactive visual insights here:  
[Tableau Dashboard](https://public.tableau.com/app/profile/marilyn.akinyi/viz/SyriatelTelcomChurnPredictionProject/Dashboard1?publish=yes)


##  Modelling
The following models were trained and evaluated:

| Model                 | Accuracy | Recall | Precision | ROC AUC |
|----------------------|----------|--------|-----------|---------|
| Logistic Regression  | 0.681    | 0.680  | 0.266     | 0.768   |
| Decision Tree        | 0.882    | 0.732  | 0.573     | 0.837   |
| Tuned Decision Tree  | 0.873    | 0.680  | 0.550     | 0.821   |
| Random Forest        | 0.882    | 0.608  | 0.590     | 0.860   |
| Tuned Random Forest  | 0.894    | 0.660  | 0.627     | 0.877   |


## Final Model: Decision Tree with Threshold Optimization
While Random Forest slightly outperformed in AUC, the Decision Tree model was selected for its:
- High recall (important for identifying churners),
- Competitive performance,
- Interpretability.

### Threshold Optimization Results:
- **Optimal Threshold**: `0.421`
- **Default Recall**: `0.732`
- **Improved Recall**: `0.753`
- **Improved F1 Score**: `0.655`

**Confusion Matrix (Optimized Threshold):**
[[517 53]
[ 24 73]]


**Classification Report (Optimized Threshold):**

          precision    recall  f1-score   support
       0       0.96      0.91      0.93       570
       1       0.58      0.75      0.65        97


##  Financial Impact Estimation

- **Annual Revenue at Risk**: \$59,243.04
- **False Positive Costs**: \$2,650.00
- **Missed Churn Revenue**: \$19,056.84
- **Recall Rate After Threshold Tuning**: **75.3%**


## Key Visualizations
1. **Target Variable Distribution**  
   ![Churn Distribution](Images\Target Variable Distribution.png)
   - Shows the imbalance in churn vs non-churn customers.

2. **Top 10 Features Most Correlated with Churn**  
   ![Correlation Heatmap](Images\Top 10 Correlated features with Churn.png)
   - Highlights which variables have strongest relationships with churn (e.g., total charges, tenure).

3. **Top 10 Feature Importances from the Decision Tree**  
   ![Feature Importance](Images\Feature importance from Decison Tree.png)
   - Demonstrates which features had the most predictive power in the Decision Tree model.



##  Recommendations

1. **Target Customers Without International Plans**  
   Offer bundled or discounted international plans to reduce churn in this group.

2. **Address High Customer Support Interaction Early**  
   Use follow-ups and satisfaction surveys to retain users with >3 support calls.

3. **Personalize Strategies for Heavy Day/Night Callers**  
   Loyalty bonuses or discounted rates can reduce churn for high-usage segments.

4. **Leverage Churn Predictions in CRM**  
   Integrate the model into CRM workflows to trigger personalized offers in real time.

5. **Prioritize High-Risk Users**  
   Focus retention resources on customers with high day usage and support calls.

6. **Regional & Onboarding Strategy**  
   Focus on churn-heavy states like NJ, CA, TX with improved onboarding experiences.

7. **Incentivize High-Charge Users**  
   Implement personalized or tiered pricing for customers with high monthly bills.


## Limitations

1. **SMOTE May Cause Overfitting**  
   Synthetic samples may reduce generalization without proper validation.

2. **Model Diversity**  
   Only three models were explored; more could boost performance.

3. **Support Call Outcome Missing**  
   Call resolution data could improve prediction accuracy.

4. **Model Drift Over Time**  
   Telecom behavior evolves — periodic retraining will be needed.


##  Next Steps

1. **Try Advanced Models**  
   Explore XGBoost, LightGBM, and neural networks to enhance accuracy.

2. **A/B Test Retention Tactics**  
   Validate model-informed strategies with real-world experiments.



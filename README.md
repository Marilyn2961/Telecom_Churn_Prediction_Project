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


## Data Preparation

- Dropped uninformative or redundant columns:
  - `phone_number`, `state`, `area_code`, `charge_bin`, `number_vmail_messages`
- Encoded categorical variables:
  - `international_plan`, `voice_mail_plan`, and `churn` mapped to 1/0
- Cleaned column names for consistency


##  Exploratory Data Analysis (EDA)

### Univariate Analysis:
- High churn rate among users **without voicemail** and **with international plans**
- Numerical features like **total_day_minutes** and **total_day_charge** show high variability and impact

### Bivariate Analysis:
- **Total charges vs. churn**: higher charges are associated with churn
- **Customer service calls**: churn increases significantly for customers with >3 calls

**Tableau Dashboard**:  
View interactive visual insights here:  
[Tableau Dashboard](https://public.tableau.com/app/profile/marilyn.akinyi/viz/SyriatelTelcomChurnPredictionProject/Dashboard1?publish=yes)


## Data Preparation for Modeling

### Multicollinearity Handling:
- Applied **Variance Inflation Factor (VIF)** to detect multicollinearity
- Dropped 7 correlated features including `total_day_charge`, `total_charge`

### Class Imbalance Fix:
- Original churn rate was ~14.5%
- Used **SMOTE** to balance the training set (50/50 churn vs. no churn)


##  Model Development

We tested multiple models, including:

- Logistic Regression  
- Random Forest  
- **Decision Tree Classifier**  *(Final Model)*

The Decision Tree was chosen for its:

- Interpretability
- Competitive accuracy and recall
- Business-friendliness


##  Model Evaluation

- **Recall**: 75.3% — Model correctly identifies 3 out of 4 actual churners
- **Precision**: Balanced to avoid false positives
- **F1-Score**: Strong performance across both classes


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



# Customer Churn Prediction

This project presents an end-to-end machine learning workflow for predicting customer churn using structured customer, service, and billing data. The focus is on building a robust and interpretable model while handling class imbalance and evaluating performance using appropriate metrics.

## Dataset
The project uses a customer churn dataset containing demographic information, service subscriptions, contract details, and billing history.  
The target variable is **Churn**, indicating whether a customer discontinued the service.

## Problem Framing
Customer churn prediction is formulated as a **binary classification problem** with churn as the positive class.  
Because the dataset is imbalanced, **ROC-AUC** is used as the primary evaluation metric.

## Exploratory Data Analysis
Exploratory analysis highlights several strong churn drivers:
- Customers with **short tenure** churn at significantly higher rates
- **Month-to-month contracts** exhibit substantially higher churn
- Higher **monthly charges** are associated with increased churn risk
- Payment method and internet service type also show meaningful differences

These insights guided feature encoding choices and model selection.

## Preprocessing
- Categorical variables were encoded using binary or one-hot encoding as appropriate
- Service-related categories such as *"No internet service"* were handled consistently
- All features were converted to numeric format
- No missing values remained after preprocessing

## Modeling Approach
Multiple models were evaluated using **5-fold stratified cross-validation**:
- Logistic Regression (baseline, imbalance-aware)
- Random Forest
- Gradient Boosting
- Histogram-based Gradient Boosting

Limited hyperparameter tuning was performed to balance performance and stability.

## Final Model
A **tuned Gradient Boosting classifier** was selected as the final model based on:
- Best and most stable cross-validated ROC-AUC
- Strong performance without unnecessary complexity
- Interpretability and consistency with EDA insights

**Best CV ROC-AUC:** ~0.85

## Feature Importance
Feature importance analysis confirms that:
- Contract type (especially month-to-month)
- Customer tenure
- Pricing-related variables  
are the strongest contributors to churn prediction.

## Limitations & Future Work
- Performance appears constrained by feature signal rather than model complexity
- Future improvements could include:
  - Richer feature engineering
  - Temporal behavior modeling
  - Cost-sensitive decision thresholds
  - External or longitudinal data

## Repository Structure

churn-prediction/
├── 01_churn_eda_modeling.ipynb
└── README.md

## How to Run
1. Clone the repository  
2. Open `01_churn_eda_modeling.ipynb`  
3. Run all cells top to bottom  

All results are reproducible using fixed random seeds.

## Notebook
📓 Main analysis notebook:  
[`notebooks/01_churn_eda_modeling.py.ipynb`](notebooks/01_churn_eda_modeling.py.ipynb)

# Telco Customer Churn Prediction (XGBoost)

## Overview
This project builds a customer churn prediction model using the Telco Customer Churn dataset from Hugging Face.  
The goal is to identify customers likely to churn so retention actions can be taken.

## Dataset
Source: `aai510-group1/telco-customer-churn`  
The dataset already provides predefined **train** and **test** splits.

## Preprocessing
The following columns were removed to avoid leakage and noise:
- `Customer ID` (identifier)
- `Churn Category`, `Churn Reason` (post-outcome)
- `Customer Status` (direct leakage)
- `Churn Score`, `Satisfaction Score` (engineered/post-churn)
- `Lat Long` (redundant string feature)

Missing values were filled with `"None"`.  
Categorical features were encoded numerically.

## Model
- Algorithm: **XGBoost (XGBClassifier)**
- Task: Binary classification (Churn / No Churn)

## Evaluation
Default threshold (0.5):
- Accuracy ≈ **86%**
- Churn recall ≈ **68%**

Lowered threshold (0.35):
- Accuracy ≈ **84%**
- Churn recall ≈ **78%**

Lowering the threshold improves churn detection at the cost of more false positives, which is often desirable in churn prediction.

# Diabetes Prediction Model

## Overview
This project builds a machine learning pipeline to predict the likelihood of diabetes based on patient data. \
The focus is not only on predictive performance, but also on **real-world applicability**, particularly in a medical context to **minimize false negatives**. 

### Project Goals
The objective of this project is to:
- Predict whether a patient is likely to have diabetes 
- Compare multiple classification models
- Optimize decision thresholds to maximize **recall**
In medical applications, failing to detect a positive case (false negative) can have severe consequences. \
Therefore, this project emphasizes recall over precision.

## Dataset
The dataset incorporates demographic variables like
- gender
- age (meaningful)

as well as various variables which can be helpful in predicting whether a patient is likely to have diabetes:
- hypertension
- heart disease
- smoking history
- bmi (meaningful)
- HbA1c level (important)
- blood glucose level (important)

The target variable is an encoded diabetes variable: 0 if the patient has no diabetes, 1 if the patient has diabetes.

The dataset used in this project is available on Kaggle: \
-> https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset

## Methodology
The project follows a structured machine learning workflow:

### 1. Data Preprocessing
- Handling categorical variables (encoding)
- Feature scaling (for Logistic Regression)
- Train-test split

### 2. Models Used
- Logistic Regression
- Decision Tree
- Random Forest
- Dummy Classifier (baseline)

### 3. Handling Class Imbalance
- Use of the *balanced* option for models to weigh the imbalanced diabetes class (0: ≈91%, 1: ≈9%) properly
- Threshold tuning to improve recall

### 4. Evaluation Metrics
- Accuracy
- Precision
- Recall (focus)
- ROC-AUC

## Model Evaluation

### Baseline Model
A Dummy Classifier was used as a baseline.
- AUC = 0.5
- Indicates no classifying power (equivalent to random guessing)

### ROC Curve
ROC curves were used to evaluate overall model performance across all thresholds. \
-> Random Forest achieved the best overall separation (highest AUC)

### Threshold Optimization
Custom thresholds were introduced to prioritize recall.

This led to:
- Significant increase in recall (fewer false negatives)
- Expected decrease in precision (trade-off)

### Confusion Matrices
Confusion matrices were analyzed for:
- Default threshold (0.5)
- Custom thresholds

This provides insight into:
- False negatives (critical in this context)
- False positives (acceptable to a degree)

## Model Insights
Logistic Regression
- Provides interpretable coefficients
- Shows how features influence diabetes risk

Decision Tree
- Easy to visualize and interpret
- Captures non-linear relationships

Random Forest
- Best overall performance
- Most robust model

## Final Model 
The Random Forest with a custom threshold was selected as the final model due to:
- Highest recall
- Strong ROC-AUC performance
- Robustness to noise and feature interactions

## Limitations
The Diabetes Prediction Model is limited by the following:
- Dataset may not represent real-world distribution
- No temporal data
- No clinical validation

## Future Work
Possible extensions include:
- Use real clinical data
- Try gradient boosting (XGBoost)

For the full analysis see the notebook: \
-> [notebook/analysis_diabetes.ipynb](https://github.com/kubaamarczak/diabetes-prediction-system/blob/main/notebooks/analysis_diabetes.ipynb)
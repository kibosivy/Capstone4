# Predicting Financial Inclusion in East Africa

## Project Overview
This project focuses on predicting whether individuals in East African countries own a bank account.  
It uses demographic and socio-economic data from Kenya, Rwanda, Tanzania, and Uganda.  

The target variable is **bank_account** (Yes/No).  
The task is framed as a **binary classification problem**.

---

## Objectives
- Understand the dataset and demographic factors affecting financial inclusion.
- Handle class imbalance and preprocess features for machine learning.
- Build, tune, and evaluate predictive models.
- Generate predictions for unseen test data.

---

## Dataset Description
The dataset includes:
- **Demographics**: Age, gender, marital status, household relationship.
- **Socio-economic**: Education level, job type, cellphone access.
- **Household info**: Household size, urban/rural location.
- **Target variable**: `bank_account` (Yes/No).

Training set shape: **(23,524, 13)**  
Test set shape: **(10,086, 12)**

---

## Methodology

### 1. Data Preprocessing
- Dropped irrelevant columns (e.g., `uniqueid` kept only for submission).
- Checked and handled missing values.
- One-hot encoded categorical features.
- Scaled/standardized numeric features where appropriate.

### 2. Handling Class Imbalance
- Target distribution was skewed (majority: no bank account).
- Used **SMOTE (Synthetic Minority Oversampling Technique)** to balance training data.

### 3. Train-Test Split
- 70% training, 30% testing.
- Stratified sampling used to maintain target distribution.

### 4. Model Training
- Baseline model: **RandomForestClassifier**.
- Hyperparameter tuning with **GridSearchCV** on parameters:
  - `n_estimators`
  - `max_depth`
  - `min_samples_split`
  - `min_samples_leaf`
  - `max_features`

### 5. Model Evaluation
Evaluated using:
- Accuracy
- Precision
- Recall
- F1-score
- ROC–AUC
- Confusion Matrix
- Classification Report

### 6. Predictions on Test Data
- Applied the tuned model on the test dataset.
- Generated submission file with:
  - `uniqueid`
  - Predicted `bank_account`

---

## Results

### Metrics
- **Accuracy**: `0.9148`
- **Precision**: `0.8569`
- **Recall**: `0.4680`
- **F1-score**: `0.6054`
- **ROC–AUC**: `0.9573`

### Confusion Matrix
[[5996 77]
[ 524 461]]


---

## Outliers

Outlier treatment was considered during preprocessing, but not applied. The reasons are:

- The dataset represents real survey responses, and extreme values (e.g., very large household sizes or very old respondents) may reflect real-world conditions rather than errors.  
- Outlier removal could distort the socio-economic representation of the population.  
- Tree-based models like Random Forest are robust to outliers, reducing the need for explicit outlier handling.  

Thus, keeping outliers preserved the integrity of the dataset while maintaining fairness in the model.

---
## Key Insights
- The model performs well overall with high accuracy and strong ROC–AUC.
- Precision is high, but recall is lower for the minority class (bank account owners).
- The model is better at identifying people **without** bank accounts.

---

## Next Steps
- Test additional models (XGBoost, Neural Networks).
- Perform feature importance analysis to identify strongest predictors.
- Explore cost-sensitive learning and ensemble techniques to improve recall.

---

## Files in Repository
- `Train.csv` — Training dataset
- `Test.csv` — Test dataset
- `main.ipynb` — Jupyter notebook with full workflow
- `submission.csv` — Final predictions for test set
- `README.md` — Project documentation

---

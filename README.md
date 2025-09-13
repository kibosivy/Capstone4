# Predicting Financial Inclusion in East Africa

## Project Overview
This project focuses on predicting whether individuals in East African countries own a bank account. It uses demographic and socio-economic data from **Kenya, Rwanda, Tanzania, and Uganda**.

The target variable is **`bank_account` (Yes/No)**.  
The task is framed as a **binary classification problem**.

---

## Problem Statement
Financial inclusion remains a critical challenge across many African countries, with large segments of the population still excluded from formal banking services. Understanding the demographic, social, and economic factors that influence whether individuals own a bank account is essential for improving access to financial products. However, the decision to open and maintain a bank account is not uniform and depends on multiple factors such as age, education, household size, location, and employment type. Without data-driven insights, policymakers, NGOs, and financial institutions struggle to design targeted strategies that effectively promote financial inclusion.

---
## Objectives
- Understand the dataset and demographic factors affecting financial inclusion.  
- Handle class imbalance and preprocess features for machine learning.  
- Build, tune, and evaluate a predictive model using **F1 score**.  
- Perform **error analysis** and visualize **learning and loss curves**.  
- Generate predictions for unseen test data.

---

## Dataset Description
The dataset includes:

- **Demographics:** Age, gender, marital status, household relationship.  
- **Socio-economic:** Education level, job type, cellphone access.  
- **Household info:** Household size, urban/rural location.  
- **Target variable:** `bank_account` (Yes/No).

- Training set shape: `(23,524, 13)`  
- Test set shape: `(10,086, 12)`

## Dataset Source
The dataset used in this project was sourced from [Zindi: Financial Inclusion in Africa](https://zindi.africa/competitions/financial-inclusion-in-africa).  

---

## Methodology

### 1. Data Preprocessing
- Dropped irrelevant columns (e.g., `uniqueid` kept only for submission).  
- Checked and handled missing values.  
- **One-hot encoded categorical features**.  
- **Scaled numeric features** using `StandardScaler`.

### 2. Handling Class Imbalance
- Target distribution was skewed (majority: no bank account).  
- Used **downsampling** to reduce the majority class, preserving real-world distribution.

### 3. Train-Test Split
- **70% training, 30% testing**.  
- Stratified sampling used to maintain target distribution.

### 4. Model Training
- **Model:** Logistic Regression  
- **Hyperparameter tuning:** `RandomizedSearchCV` with parameters:  
  - `C` (regularization strength)  
  - `penalty` (L1, L2)  
  - `class_weight` (None, balanced)

### 5. Model Evaluation
- Evaluated using **F1 score** on the test set.  
- **F1 Score achieved:** 0.756  
- Additional evaluation included:  
  - **Confusion matrix**  
  - **Predicted probability distributions per class**

### 6. Predictions on Test Data
- Applied the tuned Logistic Regression model on the test dataset.  
- Generated submission file with:  
  - `uniqueid`  
  - Predicted `bank_account`

### 7. Error Analysis and Learning/Loss Curves
- **Error analysis:** Examined misclassified samples to identify patterns or limitations of the model.  
- **Learning and loss curves:** Visualized training performance over iterations to ensure proper convergence and detect overfitting/underfitting.

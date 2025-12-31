#  Customer Churn Analysis
## Predicting Customer Attrition using Logistic Regression

# 🎯 Project Overview

## 📋 Problem Statement
Telecom companies typically identify at-risk customers only after they've already decided to leave, when retention opportunities are limited. This reactive approach leads to:

- 📉 High customer churn rates
- 💸 Lost revenue and acquisition costs  
- 📊 Declining market share

## 🚀 Solution
**Customer Churn Analysis** is a Predictive Model that flags at-risk customers before they churn, enabling proactive retention strategies, personalized offers, and customer experience improvements.

# 📊 Dataset Description

## 📁 Source Information
- **Dataset**: [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- **Institution**: Telecom Industry Dataset
- **License**: Public Domain (Kaggle)

## 📈 Statistics Overview

| Metric | Value |
|--------|-------|
| Original Records | 7,043 customers |
| After Preprocessing | 7,032 customers |
| Features | 20 predictor variables |
| Target Classes | Binary |
| Class Distribution | No Churn: 73.46%, Churn: 26.54% |
| Train/Test Split | 80% / 20% |

## 🧹 Data Preprocessing

### 🔍 Filtering & Cleaning
- **Handled Missing Values**: Converted 'TotalCharges' from string to numeric, handled 11 records with missing values
- **Data Cleaning**: Removed rows with NaN values in 'TotalCharges'

### 🔢 Encoding & Splitting
- **Binary Encoding**: No Churn = 0, Churn = 1
- **One-Hot Encoding**: Applied to categorical variables
- **Stratified Split**: 80/20 split maintaining class distribution

## 🗂️ Feature Categories

### 1. 👥 Customer Demographics (4 features)
- Gender
- Senior Citizen status
- Partner status
- Dependents status

### 2. 💰 Service Subscriptions (10 features)
- Phone service
- Multiple lines
- Internet service type
- Online security
- Online backup
- Device protection
- Tech support
- Streaming TV
- Streaming movies

### 3. 📊 Account Information (6 features)
- Tenure (months with company)
- Contract type
- Paperless billing
- Payment method
- Monthly charges
- Total charges

### 4. 🔍 Target Variable
- Churn status (Yes/No)

## 🛠️ Methodology

### 📅 Development Timeline (10-Day Sprint)

| Day | Focus | Key Activities |
|-----|-------|----------------|
| **Day 2** | Importing Libraries & Dataset | Loading Customer-Churn.csv, importing essential libraries |
| **Day 3** | Data Preprocessing (Part-1) | Initial exploration, handling missing values, data cleaning |
| **Day 4** | Data Preprocessing (Part-2) | Feature selection, target variable encoding, train-test split |
| **Day 5** | Data Preprocessing (Part-3) | Column transformation setup, OneHotEncoder configuration |
| **Day 6** | Data Preprocessing (Part-4) | Feature name extraction, transformed DataFrame creation |
| **Day 8** | Baseline Model Training | Logistic Regression pipeline with class balancing |
| **Day 9** | Model Evaluation (Part-1) | Confusion matrix, accuracy score, predictions |
| **Day 10** | Model Evaluation (Part-2) | ROC-AUC score, coefficient analysis, SHAP interpretability |

### ⚙️ Technical Implementation

**Data Processing:**
- Binary target encoding: No Churn (0) vs. Churn (1)
- One-hot encoding for categorical variables using ColumnTransformer
- Stratified 80/20 train-test split
- Feature transformation pipeline

**Model Architecture:**
- Scikit-learn Pipeline with preprocessing integration
- Logistic Regression with balanced class weights
- 46 total features after one-hot encoding

**Key Hyperparameters:**
- `max_iter=5000`: Ensures convergence
- `class_weight="balanced"`: Handles 73/27 class imbalance
- `random_state=42`: Reproducible results

**Evaluation Framework:**
- Confusion Matrix & Accuracy Score
- ROC-AUC for discrimination ability
- Coefficient analysis for feature importance
- SHAP values for model interpretability

## 📈 Results

### Model Performance Metrics

| Metric | Score |
|--------|-------|
| **Accuracy** | `0.786` |
| **ROC-AUC Score** | `0.848` |

### Confusion Matrix Analysis

**Interpretation:**
- **True Positives (187)**: Correctly identified churners ✅
- **True Negatives (923)**: Correctly identified loyal customers ✅
- **False Positives (110)**: False alarms (predicted churn but stayed)
- **False Negatives (180)**: Missed churners ⚠️ *Critical metric*

**Performance Insights:**
- **78.6% overall accuracy** on test data
- **84.8% ROC-AUC** indicates good discrimination ability
- **Higher false negatives (180)** suggests room for improvement in identifying actual churners
## 🔍 Model Explainability

### Top 10 Churn Predictors (Coefficient Analysis)

#### ⚠️ **Positive Coefficients** (Increase Churn Risk)
1. **Month-to-month contracts** (highest positive coefficient)
2. **Fiber optic internet service**
3. **No online security**
4. **No tech support**
5. **Electronic check payment method**

#### ✅ **Negative Coefficients** (Decrease Churn Risk)
1. **Two-year contracts** (strongest protective factor)
2. **Tenure** (longer tenure reduces churn)
3. **Automatic payment methods**
4. **Tech support subscription**
5. **Online security service**
### 📊 **Key Business Insights from SHAP Analysis**

#### **Contract Type is the #1 Predictor**
- Month-to-month: High churn risk
- Two-year contracts: Strong retention factor
- One-year contracts: Moderate protection

#### **Service Quality Critical for Retention**
- Customers without tech support more likely to churn
- Online security subscribers show higher loyalty
- Multiple service bundles increase stickiness

#### **Payment Method Signals Risk**
- Electronic checks: Highest churn correlation
- Automatic payments: Most stable payment method
- Mailed checks: Moderate risk

#### **Customer Tenure Matters**
- New customers (low tenure): Highest churn risk
- Long-term customers: Most loyal segment
- Tenure shows strong inverse relationship with churn

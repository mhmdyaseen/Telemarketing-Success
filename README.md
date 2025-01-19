# Bank Marketing Campaign Analysis & Prediction

## Project Overview
This project analyzes a bank marketing campaign dataset to predict whether a client will subscribe to a term deposit. The analysis includes comprehensive data preprocessing, exploratory data analysis (EDA), feature engineering, and model building using various machine learning algorithms.

## Dataset Description
The dataset contains customer information and campaign details with:
- Training set: 39,211 records
- Test set: 10,000 records
- Features: 16 columns including demographic data, banking history, and campaign information

## Key Steps and Findings

### 1. Data Preprocessing

**Missing Value Treatment:**
- Several columns had missing values:
  - job: 0.58%
  - education: 3.74%
  - contact: 26.36%
  - poutcome: 75.11%
- Missing values were handled using:
  - Most frequent value imputation for 'job' and 'education'
  - Constant value 'unknown' for 'contact' and 'poutcome'

### 2. Exploratory Data Analysis

**Key Demographics Insights:**
- Age distribution shows higher subscription rates in the 20-40 and 60-70 age groups
- Management and retired professionals showed higher subscription rates
- Education level correlates with subscription likelihood, with tertiary education showing better response

**Banking Behavior:**
- Balance distribution revealed:
  - 5,436 clients with positive balance subscribed
  - 156 clients with negative balance subscribed
  - 235 clients with zero balance subscribed
- Previous campaign success strongly indicated future subscription likelihood

**Campaign Metrics:**
- Duration of contact showed strong correlation with subscription success
- Number of contacts (campaign) showed diminishing returns after certain attempts
- Previous campaign outcome was a strong predictor

### 3. Feature Engineering

**New Features Created:**
- Date components: Extracted day, month, and year from last contact date
- Balance indicator: Created binary feature for positive balance
- Standardized numerical features
- One-hot encoded categorical variables
- Ordinal encoded education levels

### 4. Feature Selection

Used RFECV (Recursive Feature Elimination with Cross-Validation) to identify 26 most important features including:
- Demographic: age, education
- Financial: balance
- Campaign-related: duration, campaign, previous contacts
- Temporal: last day, last month
- Categorical: job types, contact method, previous outcome

### 5. Model Building and Evaluation

**Models Tested:**
1. Logistic Regression
2. SGD Classifier
3. Decision Tree Classifier
4. Random Forest Classifier
5. AdaBoost Classifier
6. XGBoost Classifier

**Performance Comparison (F1 Scores):**
- XGBoost: 0.772 (validation)
- Random Forest: 0.769 (validation)
- Decision Tree: 0.734 (validation)
- Logistic Regression: 0.732 (validation)
- AdaBoost: 0.676 (validation)
- SGD Classifier: 0.657 (validation)

**Best Performing Model: XGBoost**
- Training F1 Score: 0.797
- Best Parameters:
  - max_depth: 5
  - learning_rate: 0.1
  - n_estimators: 100
  - subsample: 0.8
  - colsample_bytree: 1.0
  - scale_pos_weight: 2

### 6. Key Findings

1. **Customer Profile Impact:**
   - Education level and job type significantly influence subscription likelihood
   - Age shows non-linear relationship with subscription probability
   - Previous banking relationship matters

2. **Campaign Execution:**
   - Contact duration is a strong predictor
   - Previous campaign success strongly indicates future success
   - Contact method influences response rate

3. **Financial Indicators:**
   - Account balance correlates with subscription probability
   - Housing and loan status provide relevant context
   - Default history impacts subscription likelihood

4. **Model Performance:**
   - XGBoost outperformed other models, suggesting complex non-linear relationships in the data
   - Feature selection improved model efficiency while maintaining performance
   - Class imbalance handling through model parameters improved prediction quality

## Recommendations

1. **Campaign Targeting:**
   - Focus on customers with positive previous campaign outcomes
   - Prioritize customers with higher education levels and stable jobs
   - Consider customer's current banking relationship and balance

2. **Campaign Execution:**
   - Optimize contact duration based on customer segment
   - Choose appropriate contact method based on customer profile
   - Plan follow-up strategy based on initial response

3. **Model Implementation:**
   - Use XGBoost model for prediction with optimized parameters
   - Monitor and update model periodically with new campaign data
   - Consider ensemble approach for critical decisions

This analysis provided me a robust framework for predicting term deposit subscriptions and optimizing marketing campaign effectiveness. The selected model's performance suggests reliable predictive capability, while the insights gained can directly inform marketing strategy and customer targeting approaches.

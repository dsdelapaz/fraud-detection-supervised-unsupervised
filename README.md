# Credit Card Fraud Detection using Logistic Regression

## Overview

A **binary classification model for credit card fraud detection** using transaction data through a **logistic regression model**. The focus is on exploratory data analysis (EDA), feature engineering from temporal and demographic variables, and interpretable modeling under severe class imbalance.

---

## Dataset

The dataset is takenn from:
Credit Card Transactions Fraud Detection Dataset 
(https://www.kaggle.com/datasets/kartik2112/fraud-detection)

It consists of anonymized credit card transactions containing:

* Transaction amount
* Merchant and transaction category 
* User demographic features
* is_fraud binary response variable

Due to file size and constraints, the raw datasets are not included in this repository.

---

## Data Preparation

### Cleaning and filtering

* Removed personally identifiable and high-cardinality identifiers
* Converted date fields to proper datetime formats
* Handled missing values
* Consolidated training and test datasets for consistent preprocessing

### Feature engineering

* Temporal features extracted from transaction timestamps:

  * Day, weekday, month, year, hour, minute
* Demographic features:

  * User age
  * Age group bins
* Geographic features:

  * City population
  * City population deciles

The result is an **analytical base table** suitable for modeling and interpretation.

---

## Exploratory Data Analysis

Extensive EDA was performed to understand fraud patterns across:

* Transaction categories
* Gender and age groups
* Occupations and cities
* Temporal dimensions (hour, weekday, month)
* City population size

Key insights:

* Fraud is highly **imbalanced** relative to non-fraud transactions
* Fraud rates vary substantially by transaction category, time of day, and population density
* Certain demographic and transactional features exhibit higher fraud propensity

---

## Modeling Approach

### Baseline Model: Logistic Regression

* Standardized numeric features
* Label-encoded categorical variables
* Class imbalance addressed using `class_weight='balanced'`
* Evaluated using a train–test split

### Feature Selection

* **Recursive Feature Elimination (RFE)** used to identify the most informative predictors
* Model retrained using prioritized features to assess performance trade-offs

### Alternative Encoding Strategy

* One-hot encoding applied to categorical variables
* Compared against label-encoded approach to examine effects on performance and interpretability

---

## Evaluation Metrics

Given the imbalanced nature of fraud detection, evaluation focuses on:

* **Precision**: correctness of fraud predictions
* **Recall**: ability to capture fraudulent transactions
* **Accuracy**: overall classification correctness
* **ROC–AUC**: discrimination ability across thresholds
* **Confusion Matrix**: error distribution analysis

Recall is emphasized due to the high cost of missed fraud cases.

---

## Results

* Logistic regression achieved **high recall** at the expense of precision, consistent with fraud detection objectives
* Feature selection via RFE reduced model complexity while maintaining comparable performance
* One-hot encoding increased dimensionality without proportional gains in predictive power
* Model coefficients provided clear interpretability into fraud-driving factors

These results highlight the trade-offs between **model simplicity, interpretability, and detection sensitivity**.

---

## Libraries Used

* Python
* pandas, NumPy
* scikit-learn
* matplotlib, seaborn

---



# Bank Customer Churn Prediction

This project develops a data-driven approach to predicting customer churn in the banking sector using supervised machine learning. Rather than focusing solely on predictive accuracy, the analysis emphasises decision-making under class imbalance, demonstrating how probability-based models can be translated into actionable business insights.

By comparing Logistic Regression, k-Nearest Neighbours, and Random Forest models, and applying decision-threshold optimisation via Youden’s J statistic, the project highlights how model performance depends not only on the algorithm but also on how predictions are operationalised. The results show that threshold optimisation can substantially improve churn detection, making the models more suitable for real-world retention strategies where missing a churner is more costly than incorrectly flagging a loyal customer.

---

## 📌 Project Overview

Customer churn poses a major challenge for retail banks, as losing existing customers directly impacts profitability and long-term sustainability.  
This project formulates churn prediction as a **binary classification problem**, aiming not only to achieve high predictive accuracy but to provide **actionable probability estimates** that support targeted customer retention strategies.

The analysis goes beyond default model settings by demonstrating how **decision-threshold optimisation (Youden’s J statistic)** can significantly improve churn detection—an essential consideration in cost-sensitive business environments.

---

## 📊 Dataset Description

- **Size:** 10,000 bank customers  
- **Target Variable:**  
  - `churn` (1 = customer left, 0 = customer retained)
- **Class Distribution:**  
  - ~20% churners  
  - ~80% non-churners (moderately imbalanced)

### Key Features

| Feature | Description |
|------|------------|
| credit_score | Customer credit score |
| country | Country of residence |
| gender | Customer gender |
| age | Customer age |
| tenure | Years with the bank |
| balance | Account balance |
| products_number | Number of bank products held |
| active_member | Active membership status |
| estimated_salary | Estimated annual salary |
| credit_card | Credit card ownership |

---

## 🔍 Exploratory Data Analysis (EDA)

The EDA investigates:
- **Target imbalance**, highlighting why accuracy alone is misleading  
- **Demographic patterns**, showing higher churn among older customers  
- **Customer engagement**, revealing significantly lower churn among active members  
- **Feature correlations**, confirming churn is driven by multiple interacting factors rather than a single dominant variable  

Key insights:
- **Age** shows the strongest positive relationship with churn  
- **Active membership** is the strongest negative driver of churn  
- Financial variables such as salary and credit score show weak direct effects

---

## 🧠 Methodology

### Preprocessing
- Categorical encoding
- Feature standardisation (critical for distance-based models)
- Stratified train–test split to preserve class proportions
- Careful pipeline design to prevent data leakage

---

### Models Implemented

- **Logistic Regression**
  - Interpretable baseline model
  - Hyperparameter tuning via cross-validation
  - Probability-based decision making

- **k-Nearest Neighbours (kNN)**
  - Non-parametric model capturing local, non-linear patterns
  - Probability calibration for fair threshold comparison

- **Random Forest**
  - Ensemble model with strong discriminative power
  - Used as a performance benchmark

---

## ⚖️ Evaluation Strategy

Given the imbalanced nature of churn data, evaluation focuses on:
- Accuracy
- Precision
- Recall
- ROC–AUC
- Confusion matrices

⚠️ **Key principle:**  
Accuracy alone is insufficient when the cost of missing a churner is higher than falsely flagging a loyal customer.

---

## 🎯 Threshold Optimisation (Youden’s J Statistic)

Instead of relying on the default probability threshold (0.5), the project applies **Youden’s J statistic** to:

- Maximise the trade-off between **True Positive Rate** and **False Positive Rate**
- Improve churn detection (recall)
- Align model decisions with real-world business objectives

Thresholds are optimised **using training data only** to ensure fair test evaluation.

---

## 📈 Results Summary

| Model | Threshold | Accuracy | Precision | Recall |
|------|----------|----------|-----------|--------|
| Logistic Regression | 0.5 | 0.804 | 0.562 | 0.179 |
| Logistic Regression | Youden | 0.734 | 0.403 | **0.632** |
| kNN | 0.5 | 0.830 | 0.655 | 0.353 |
| kNN | Youden | 0.798 | 0.503 | 0.561 |
| Random Forest | 0.5 | **0.866** | **0.818** | 0.441 |

### Interpretation
- **Random Forest** achieves the highest overall accuracy and ROC–AUC  
- **Logistic Regression** benefits most from threshold optimisation, becoming the best model when **churn detection is prioritised**
- **kNN** provides a strong balance between accuracy and recall
- Model choice and threshold selection must be considered **jointly**

---

## 🧩 Key Business Insights

- Active customers are significantly less likely to churn
- Older customers face higher churn risk
- Threshold optimisation can be more impactful than switching models
- Probability outputs are more valuable than binary predictions in decision-making contexts

---

## 📂 Repository Structure

```text
├── Bank Customer Churn.ipynb     # Full analysis and model implementation
├── Bank Customer Churn.pdf      # Academic-style report
├── README.md                    # Project documentation

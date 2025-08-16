# Census Income  — Project Report

## Table of Contents

1. [Introduction](#introduction)
2. [Data Exploration & Preparation](#data-exploration--preparation)
3. [Custom Transformer Design](#custom-transformer-design)
4. [Preprocessing Pipelines](#preprocessing-pipelines)
5. [Model Selection & Evaluation](#model-selection--evaluation)
6. [Classification Metrics](#classification-metrics)
7. [Final Model Evaluation](#final-model-evaluation)
8. [Conclusion & Explanation of Metrics](#conclusion--explanation-of-metrics)

---

## 1. Introduction

This project aims to classify individuals as earning more or less than $50K/year using census data. The workflow follows best practice machine learning steps: data preprocessing, transformation, modeling, and evaluation.

## 2. Data Exploration & Preparation

- Loaded dataset with `pandas`, replacing missing values ("?") with NaN.
- Inspected data types, missing values, and split features and labels.
- Used train/test split (80/20) for robust model validation.

## 3. Custom Transformer Design

A custom transformer, `CensusIncomeTransformer`, was built to process numeric data:

- When `create_new_column=True`, it:
    - Adds a new column: `days_per_week` × `hours_per_day` (total weekly hours).
    - Removes the original `days_per_week` and `hours_per_day` columns.
- When `create_new_column=False`, it skips these steps and returns the input unmodified.
- Designed to accept NumPy arrays (as output by an imputer in a pipeline).

## 4. Preprocessing Pipelines

- **Numeric Pipeline (`num_pipeline`):**
    - SimpleImputer (mean)
    - Custom Transformer (`CensusIncomeTransformer`)
    - StandardScaler

- **Categorical Pipeline (`cat_pipeline`):**
    - SimpleImputer (most_frequent)
    - OneHotEncoder (drop='first', sparse_output=False)

- Combined into a ColumnTransformer (`preprocessing`), specifying exact columns for each pipeline.

## 5. Model Selection & Evaluation

Trained three classifiers:
- Logistic Regression
- Stochastic Gradient Descent (SGD)
- Random Forest

All models achieved similar accuracy scores (~84–85%) via 3-fold cross-validation.

| Model                | Mean Accuracy (CV=3) |
|----------------------|---------------------|
| Logistic Regression  | ~85%                |
| SGD Classifier       | ~85%                |
| Random Forest        | ~85%                |

## 6. Classification Metrics

For the chosen Logistic Regression model, calculated:
- **Precision** (pos_label=">50K"): 0.74
- **Recall**: 0.60
- **F1 Score**: 0.66

All metrics computed with cross-validated predictions.

## 7. Final Model Evaluation

- Applied the full preprocessing pipeline to the test set (using `.transform()`, not `.fit_transform()`).
- Test set accuracy for Logistic Regression: **0.85** (rounded to 2 decimal places).

## 8. Conclusion & Explanation of Metrics

- **Accuracy** measures overall correctness but can be misleading if classes are imbalanced.
- **Precision** tells us, out of all predicted ">50K" incomes, how many were correct.
- **Recall** tells us, out of all actual ">50K" incomes, how many the model found.
- **F1 Score** balances precision and recall, useful in uneven class distributions.

**In summary:**  
Our logistic regression model achieves strong generalization (85% accuracy on test data). Precision (0.74) is higher than recall (0.60), suggesting the model is more conservative in predicting high income (fewer false positives, but more missed positives). The F1 score (0.66) reflects this tradeoff. For real-world deployment, further improvement (e.g., hyperparameter tuning, feature engineering) and business/context-aware thresholding may be desirable.

---
**Prepared by:**  
SamrahFar  
Jan 2025

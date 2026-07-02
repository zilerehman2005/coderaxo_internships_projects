# Week 2 Assignment – Core ML Pipeline & First Models

**Internship:** Coderaxo AI/ML Internship
**Week:** 2
**Notebook:** `Week2_ML_Pipeline_Assignment.ipynb`

## Overview

This week focused on understanding the end-to-end machine learning pipeline and applying it to
two classic datasets — **House Prices** (regression) and **Titanic** (classification) — using
Linear Regression, Logistic Regression, and Decision Tree models, followed by building a
reusable preprocessing pipeline with `Pipeline` and `ColumnTransformer`.

## What I Did

### Task 1 – ML Pipeline Theory
Explained the 6 core steps of a machine learning pipeline (Problem Definition → Data Collection
→ Preprocessing → EDA/Feature Engineering → Model Training → Evaluation/Deployment), walked
through with a Loan Prediction example.

### Task 2 – Linear Regression (House Prices dataset)
- Loaded and explored the dataset (1460 rows, 81 columns).
- Selected numeric features and imputed missing values (median strategy).
- Split data 80/20 into train/test sets.
- Trained a `LinearRegression` model.
- Evaluated using MAE, MSE, RMSE, and R².

**Result:** R² = 0.82, RMSE ≈ $36,837

### Task 3 – Logistic Regression (Titanic dataset)
- Loaded and explored the dataset (891 rows, 12 columns).
- Handled missing values: `Age` (median), `Embarked` (mode), dropped `Cabin` (77% missing).
- Encoded categorical features (`Sex`, `Embarked`) via one-hot encoding.
- Scaled numerical features (`Age`, `Fare`, `SibSp`, `Parch`) with `StandardScaler`.
- Trained a `LogisticRegression` model and evaluated with Accuracy, Precision, Recall, F1, and
  a Confusion Matrix.

**Result:** Accuracy = 80.4%, Precision = 79.3%, Recall = 66.7%, F1 = 0.72

### Task 4 – Decision Tree (Titanic dataset)
- Trained a `DecisionTreeClassifier` (max_depth=5) on the same preprocessed data as Task 3.
- Compared its accuracy against the Logistic Regression model.

**Result:** Decision Tree Accuracy = 76.5% (Logistic Regression performed better on this split)

### Task 5 – Preprocessing Pipeline
- Built a full preprocessing workflow using `Pipeline` + `ColumnTransformer`, handling numeric
  (impute + scale) and categorical (impute + one-hot encode) features separately, then feeding
  both into a single `LogisticRegression` classifier.
- Explained why pipelines are useful, what data leakage is, and how pipelines prevent it.

**Result:** Pipeline Model Accuracy = 79.9%

### Optional Challenge
Created an **Actual vs. Predicted** scatter plot for the Linear Regression model to visualize
prediction accuracy across the price range.

## Tools & Libraries
- Python, Jupyter Notebook
- pandas, numpy
- scikit-learn (LinearRegression, LogisticRegression, DecisionTreeClassifier, Pipeline,
  ColumnTransformer, StandardScaler, OneHotEncoder, SimpleImputer)
- matplotlib, seaborn

## Datasets
- [House Prices – Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data)
- [Titanic – Machine Learning from Disaster](https://www.kaggle.com/c/titanic/data)

## Folder Structure
```
.
├── Week2_ML_Pipeline_Assignment.ipynb   # Main notebook (all 5 tasks + optional challenge)
├── house_train.csv                       # House Prices dataset
├── titanic_train.csv                     # Titanic dataset
├── README.md                             # This file
└── screenshots/
    └── results.png                       # Add your notebook output screenshot(s) here
```

## How to Run
1. Clone/download this folder and keep the CSV files in the same directory as the notebook.
2. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn jupyter
   ```
3. Launch Jupyter and run all cells:
   ```bash
   jupyter notebook Week2_ML_Pipeline_Assignment.ipynb
   ```

## Screenshot

<!-- Add your screenshot below. Place the image file inside a `screenshots/` folder next to
     this README, then update the path if needed. -->

![Notebook Results](screenshots/results.png)

---
*Part of the Coderaxo AI/ML Internship — Week 2 submission.*

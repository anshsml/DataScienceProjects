# Project 7: Loan Approval Model Selection with Pipelines and Grid Search

**Course:** DSC 550 – Data Mining (Week 8)

## Overview
Predicts whether a loan application is approved. The project uses scikit-learn pipelines and `GridSearchCV` to tune one model and then to choose among several model types.

## Data
`Loan_Train.csv`: 614 loan applications with applicant demographics, income, loan amount, credit history and property area. The target is `Loan_Status` (Y/N).

## Approach
1. Dropped `Loan_ID` and rows with missing values, then one-hot encoded the categorical columns.
2. Split into 80% training and 20% test data.
3. Built a pipeline with a `MinMaxScaler` followed by a `KNeighborsClassifier`.
4. Used a grid search to tune `n_neighbors` from 1 to 10 with 5-fold CV.
5. Widened the search to include **logistic regression** and **random forest** with their own hyperparameter grids. The search treats the model type itself as a parameter.

## Results
| Model | Test accuracy |
|---|---|
| Default KNN (k = 5) | 0.781 |
| Tuned KNN (k = 3) | 0.792 |
| **Best overall: Logistic regression (C = 10)** | **0.823** |

Logistic regression beat both KNN models. The cross-validation score for the best model was 0.810.

## Files
- `DSC550_Week8.ipynb`: notebook
- `Loan_Train.csv`: dataset

## Tools
Python, pandas, NumPy, scikit-learn (Pipeline, MinMaxScaler, KNeighborsClassifier, LogisticRegression, RandomForestClassifier, GridSearchCV)

## How to run
```bash
pip install pandas numpy scikit-learn
jupyter notebook DSC550_Week8.ipynb
```

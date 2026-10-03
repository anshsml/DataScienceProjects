# Project 2: Customer Churn Prediction and Revenue Impact

**Course:** DSC 680 – Applied Data Science (Milestone 2)

## Overview
Telecom companies lose revenue when customers cancel. This project predicts which customers are likely to churn and estimates how much revenue a targeted retention campaign could protect.

**Research questions**
1. Which customer segments have the highest churn rates?
2. Which features are the strongest predictors of churn?
3. Can classification models reliably flag high-risk customers, and how does logistic regression compare with a random forest?
4. How much revenue is at stake among the highest-risk customers?

## Data
IBM **Telco Customer Churn** dataset (`WA_Fn-UseC_-Telco-Customer-Churn.csv`): 7,043 customers and 21 columns. It covers demographics, account details (contract, payment method, tenure, charges), the services each customer subscribes to, and a `Churn` label. `Sample_Telco.csv` is a 48-row sample of the same data.

## Approach
- **Preparation:** all steps run inside an scikit-learn `ColumnTransformer` pipeline. That means median/mode imputation, scaling of numeric columns and one-hot encoding of categorical ones (`handle_unknown='ignore'`). `customerID` is removed before modeling.
- **Exploration:** churn rates by contract type, payment method, internet service and tech support, plus class balance, tenure and monthly charges.
- **Models:** logistic regression (an interpretable baseline) and a random forest (500 trees, max depth 5). Both use `class_weight='balanced'`.
- **Evaluation:** a stratified 70/30 split with 5-fold stratified cross-validation on the training set. Models are scored on ROC-AUC, accuracy, precision, recall and F1.
- **Business scenario:** customers are ranked by predicted risk and the top 20% are targeted. The scenario assumes a 30% retention effect and $50 per customer for the offer.

## Results
| Model (holdout) | ROC-AUC | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|---|
| Logistic regression | **0.845** | **0.761** | **0.534** | 0.770 | **0.631** |
| Random forest | 0.817 | 0.685 | 0.451 | **0.854** | 0.590 |

Logistic regression is the better model overall. The random forest finds more of the churners, but it also flags more customers who wouldn't have left.

**Example revenue scenario (not a causal estimate)**
- Targeted customers (top 20% by risk): 1,409, of whom 1,203 actually churned
- Annual revenue at stake: about $1.15M
- Revenue kept if 30% of those churners stay: about $345K
- Cost of the offer: $70K, for a **net value of about $275K**

## Files
- `DSC680_Milestone2.ipynb`: full analysis with charts
- `DSC680_Milestone2_AnishSamuel.docx`: written milestone report
- `WA_Fn-UseC_-Telco-Customer-Churn.csv`: full dataset
- `Sample_Telco.csv`: small sample

## Tools
Python, pandas, NumPy, Matplotlib, scikit-learn (Pipeline, ColumnTransformer, LogisticRegression, RandomForestClassifier, StratifiedKFold)

## How to run
```bash
pip install pandas numpy matplotlib scikit-learn
jupyter notebook DSC680_Milestone2.ipynb
```

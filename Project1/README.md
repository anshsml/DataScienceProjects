# Project 1: Feature Reduction and Feature Selection

**Course:** DSC 550 – Data Mining (Week 6)

## Overview
This project compares ways to reduce the number of features before training a model. Part 1 uses dimensionality reduction on a regression problem. Part 2 uses statistical feature selection on a classification problem.

## Data
- **House prices** (`train.csv`, Kaggle *House Prices: Advanced Regression Techniques*): 1,460 homes, 81 columns, with `SalePrice` as the target.
- **Mushrooms** (`mushrooms.csv`, UCI *Mushroom* dataset): all-categorical features with an edible/poisonous label.

Neither CSV is included in this folder. Download them and put them next to the notebook before running it.

## Approach
**Part 1: PCA and variance threshold for linear regression**
1. Dropped `Id` and any column missing more than 40% of its values.
2. Filled numeric gaps with the median and categorical gaps with the mode, then one-hot encoded.
3. Trained a baseline linear regression (80/20 split).
4. Retrained on PCA components that keep 90% of the variance.
5. Retrained on min-max scaled features with variance above 0.1.

**Part 2: χ² feature selection for a decision tree**
1. One-hot encoded the mushroom features and trained a decision tree.
2. Drew the tree with Graphviz.
3. Picked the 5 best features with `SelectKBest(chi2)` and retrained the tree on them.

## Results
| Model | R² | RMSE |
|---|---|---|
| Linear regression, all features | 0.643 | 52,299 |
| PCA (90% variance → 1 component) | 0.064 | 84,755 |
| Variance threshold (> 0.1) | **0.656** | **51,393** |

PCA ran on unscaled data, so the large-valued columns dominated and only one component was kept. That one component left out most of the useful signal. Choosing features by variance after scaling did slightly better than the baseline.

| Mushroom classifier | Accuracy |
|---|---|
| Decision tree, all features | 1.000 |
| Decision tree, 5 χ² features | 0.974 |

The five selected features were `odor_f`, `odor_n`, `gill-size_n`, `stalk-surface-above-ring_k` and `stalk-surface-below-ring_k`. Odor alone separates most of the classes.

## Files
- `DSC550_Week6.ipynb`: notebook with code and outputs

## Tools
Python, pandas, NumPy, scikit-learn (LinearRegression, PCA, MinMaxScaler, DecisionTreeClassifier, SelectKBest), Graphviz

## How to run
```bash
pip install pandas numpy scikit-learn graphviz
jupyter notebook DSC550_Week6.ipynb
```

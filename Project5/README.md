# Project 5: Clustering ALS Patients with K-Means

**Course:** DSC 630 – Predictive Analytics (Week 4)

## Overview
Unsupervised learning applied to clinical data from patients with ALS (amyotrophic lateral sclerosis). The aim is to find patient subgroups that could point to different disease progression patterns.

## Data
`als_data.csv`: 2,223 patients and 101 columns. Each clinical measurement (for example albumin, trunk function and urine pH) is summarized with features such as `_min`, `_max`, `_median` and `_range`.

## Approach
1. Checked for and dropped missing values.
2. Standardized every feature with `StandardScaler`. K-means uses distances, so unscaled features with large values would dominate.
3. Ran K-means for k = 2 to 10 and plotted the silhouette score for each.
4. Chose the k with the highest silhouette score and fit the final model.
5. Reduced the data to 2 principal components with PCA and plotted the clusters.

## Results
- **Best number of clusters: k = 2**, chosen by silhouette score.
- The PCA plot shows two fairly distinct groups with some overlap. Overlap is expected in real medical data, where patient traits change gradually.
- The clusters could help with studying progression trends, personalizing treatment, and building features for later predictive models.

## Files
- `Anish_Samuel_DS630_Assignment4.ipynb`: notebook
- `Anish_Samuel_DS630_Assignment4.html` / `.pdf`: rendered output with charts
- `als_data.csv`: dataset

## Tools
Python, pandas, NumPy, Matplotlib, scikit-learn (StandardScaler, KMeans, silhouette_score, PCA)

## How to run
```bash
pip install pandas numpy matplotlib scikit-learn
jupyter notebook Anish_Samuel_DS630_Assignment4.ipynb
```

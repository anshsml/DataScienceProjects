# Project 6: Data Wrangling with pandas – Boston Housing and Adult Income

**Course:** DSC 540 – Data Preparation (Weeks 1–3)

## Overview
Core pandas data wrangling on two well-known datasets: loading files, reshaping, summary statistics, string cleanup, filtering, grouping and merging.

## Data
- `Boston_housing.csv`: 506 census tracts and 14 features, including crime rate, rooms, age and price.
- `adult_income_data.csv`: UCI *Adult* census income data, 32,561 rows. The file has no header row, so `adult_income_names.txt` supplies the column names.

## Approach
**Boston housing (Activity 3.01)**
- Removed unneeded columns, then plotted a histogram of each remaining feature.
- Plotted crime rate against price, using a log scale on crime rate to spread out the skewed values.
- Calculated summary statistics (average rooms, median age, average distance to employment centers).
- Found that **41.5%** of homes are priced under $20K.

**Adult income (Activity 4.01)**
- Read the column names from the text file and loaded the CSV with them.
- Checked for nulls, ran `describe()`, and removed leading and trailing spaces from every text column.
- Filtered to ages 30–50 and computed age statistics for each occupation with `groupby`.
- Took samples of two subsets and joined them on `occupation` with an inner merge.

**pandas Series arithmetic**
- Added and subtracted Series whose indexes only partly match, to show how pandas lines up labels and fills gaps with NaN.

## Files
- `DSC540_Assignment_week3.ipynb`: notebook
- `Boston_housing.csv`, `adult_income_data.csv`, `adult_income_names.txt`: data

## Tools
Python, pandas, NumPy, Matplotlib

## How to run
```bash
pip install pandas numpy matplotlib
jupyter notebook DSC540_Assignment_week3.ipynb
```

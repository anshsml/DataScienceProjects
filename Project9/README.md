# Project 9: Web Scraping, Outlier Handling and SQLite

**Course:** DSC 540 – Data Preparation (Weeks 5–6)

## Overview
Three data-acquisition and cleaning tasks: scraping a table from a web page, handling missing values and outliers, and storing records in a SQLite database.

## Approach and results
**Activity 5.01: Scraping GDP data from Wikipedia**
- Downloaded *List of countries by GDP (nominal)* and parsed it with BeautifulSoup.
- Found the `wikitable` and rebuilt its two-row header into single column names, such as `IMF Forecast`, `World Bank Year` and `United Nations Estimate`.
- Removed footnote markers and thousands separators, then loaded the rows into a pandas DataFrame.

**Activity 6.01: Handling outliers and missing data**
- `visit_data.csv` has 1,000 visitor records. Missing values: 296 first and last names, 505 genders and 26 visit counts. There are no duplicate rows.
- Used box plots to find outliers, then removed them with the 1.5 × IQR rule, leaving 974 rows.
- As a second approach, kept only visit counts between 100 and 2,900, leaving 923 rows.

**Exercise 3: Creating a SQLite table**
- Created a `contacts` table in `contacts.db`, inserted sample address records and read them back into pandas.

## Files
- `DSC540_Assignment_Week5.ipynb`: notebook
- `data/visit_data.csv`: visitor data
- `data/List of countries by GDP (nominal) - Wikipedia.html` (and `_files/`): saved copy of the scraped page
- `contacts.db`: SQLite database created by the notebook

## Tools
Python, BeautifulSoup, requests, regular expressions, pandas, Matplotlib, Seaborn, SQLite

## How to run
```bash
pip install pandas beautifulsoup4 requests matplotlib seaborn
jupyter notebook DSC540_Assignment_Week5.ipynb
```
The scraping cell downloads the live Wikipedia page. If the page layout has changed, the table may not parse the same way.

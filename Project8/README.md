# Project 8: Querying a Relational Database with SQL and Python

**Course:** DSC 540 – Data Preparation (Weeks 11–12)

## Overview
Answers questions about a SQLite database of pet owners and their pets. The SQL queries run from Python with the built-in `sqlite3` module and use grouping, subqueries and NULL handling.

## Data
`data/petsdb`: a SQLite database with two tables.
- `persons`: owner details (id, first and last name, age, city, …)
- `pets`: pet records linked by `owner_id`, including `pet_type` and `treatment_done`

## Questions answered
| Question | Answer |
|---|---|
| Which age has the most people? | 73 (5 people) |
| How many people have no last name? | 60 |
| How many people own more than one pet? | 43 |
| How many pets have received treatment? | 150 |
| How many treated pets have a known pet type? | 68 |
| How many pets live in the city "east port"? | 49 |
| How many pets in "east port" have received treatment? | 49 |

The notebook also opens, checks and closes the database connection, and counts people at each age with `GROUP BY`.

## Files
- `DSC540_Assignment_Week11.ipynb`: SQL notebook
- `data/petsdb`: SQLite database
- `DSC550_Week8.ipynb`: copy of the Project 7 notebook (see [Project 7](../Project7))

## Tools
Python, SQLite, SQL (`GROUP BY`, `HAVING`, subqueries, `IS NULL`)

## How to run
Only the Python standard library is needed.
```bash
jupyter notebook DSC540_Assignment_Week11.ipynb
```

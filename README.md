# MLB-Free-Agent-Analysis
# Evaluating MLB Free Agent Value Through Data Analytics

This project analyzes MLB free-agent batters (1998–2013) to answer a simple
front-office question:

> **Which hitters are the best (and worst) value for money, and can we predict fair salaries going into free agency?**

Using historical performance metrics and inflation-adjusted salaries, the
project combines:

- **Descriptive analysis** – how salaries and stats evolved over time.
- **Predictive modeling** – segmented Random Forest models to estimate
  fair 2013 salaries and flag under/over-valued players.

The repo is fully reproducible: you can clone it, install dependencies,
and rerun the analysis end-to-end.

---

## 1. Business Context

Small-market MLB teams can't win bidding wars with big clubs. They need to:

- **Identify undervalued hitters** before the market prices them correctly.
- **Avoid overpaying for brand names** whose production no longer matches their cost.
- **Use data** as a negotiation anchor when discussing contract value.

This project simulates the work of a junior analyst in a front office,
using a historical free-agent dataset to:

1. Understand how the market has valued different offensive stats since the *Moneyball* era.
2. Predict "fair" salaries for 2013 free agents based on prior performance.
3. Highlight players who look like bargains or overpays relative to those predictions.

---

## 2. Data

- **File:** `data/baseballcase_data.csv`  
- **Scope:** MLB free-agent batters, 1998–2013  
- **Grain:** One row per player-season leading into a free-agent contract  
- **Key columns used:**
  - `Next Salary ADJ` → converted to `SalaryAdj` (inflation-adjusted next-year salary)
  - `Year` – contract year
  - `HR` – home runs in prior season
  - `OBP` – on-base percentage
  - `SLG` – slugging percentage
  - `WAR` – wins above replacement
  - `Age` – player age
  - `Player` – player name (used for interpretation)

Basic cleaning includes:

- Standardizing column names
- Converting key fields to numeric
- Dropping rows with missing values in core variables

---

## 3. Project Structure

```text
mlb-free-agent-value/
  ├─ README.md               # Project overview (this file)
  ├─ requirements.txt        # Python dependencies
  ├─ data/
  │    ├─ baseballcase_data.csv
  │    └─ baseballcase_data_glossary.xlsx
  ├─ notebooks/
  │    ├─ 01_descriptive_analysis.ipynb
  │    └─ 02_predictive_modeling.ipynb
  ├─ reports/
  │    ├─ descriptive_report.pdf
  │    └─ predictive_report.pdf
  └─ figures/
       └─ *.png              # All plots from notebooks

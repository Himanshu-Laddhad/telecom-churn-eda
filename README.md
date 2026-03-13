# Telecom Customer Churn — Exploratory Data Analysis

An end-to-end exploratory analysis of a telecom dataset with **3,333 customers** to uncover the patterns and features that drive customer churn. The project surfaces data quality issues, detects statistical outliers, and quantifies the predictive signal of both numeric and categorical features — laying the groundwork for a downstream churn prediction model.

## Highlights

- **42.4% churn rate** among International Plan subscribers vs. only 11.5% without — the single strongest churn signal
- Identified that the three area codes in the dataset are randomly distributed across all 51 states, flagging the geographic features as unreliable for modelling
- `CustServCalls` emerges as the strongest numeric predictor (r ≈ 0.21) — customers who contact support ≥4 times churn at 3× the baseline rate
- Detected upper-end outliers in `IntlCalls` via box plot visualisation

## Project Structure

```
telecom-churn-eda/
├── telecom_churn_eda.ipynb    # Main analysis notebook
├── Churn.csv                  # Dataset — 3,333 rows × 22 columns
└── README.md
```

## Analysis Sections

| Section | Description |
|---|---|
| 1. Data Loading & Inspection | Shape, dtypes, first rows, missing value audit |
| 2. State & Area Code Analysis | Data quality check — reveals geographic encoding issues |
| 3. Outlier Detection | Box plot of `IntlCalls` to identify statistical outliers |
| 4. Churn vs. Usage Patterns | Scatter plot of `CustServCalls` vs. `DayMins` coloured by churn |
| 5. Categorical Predictors | Churn rates by International Plan and Voicemail Plan |
| 6. Numeric Predictors | Box plots for 9 numeric features split by churn status |
| 7. Key Findings & Conclusions | Summary table of top predictors and recommendations |

## Key Findings

| Finding | Detail |
|---|---|
| **Strongest numeric predictor** | `CustServCalls` — high call frequency strongly associated with churn |
| **Strongest plan predictor** | International Plan → **42.4% churn** vs. 11.5% without (31 pp gap) |
| **Protective factor** | Voicemail Plan subscribers churn less — 8.7% vs. 16.7% |
| **Data quality issue** | Area codes (408, 415, 510) appear across all 51 states randomly — not geographically meaningful |
| **Collinearity** | `DayMins` and `DayCharges` are near-perfectly correlated — use only one |
| **Recommended features** | `CustServCalls`, `IntlPlan`, `DayMins`, `VmailPlan`, `VMailMessage` |

## Tech Stack

| Tool | Purpose |
|---|---|
| Python 3 | Core language |
| Pandas | Data loading, cleaning, groupby analysis |
| NumPy | Numeric operations |
| Matplotlib | Base plotting |
| Seaborn | Statistical visualisations (box plots, scatter plots, count plots) |

## Getting Started

```bash
git clone https://github.com/himanshuladdhad/telecom-churn-eda.git
cd telecom-churn-eda
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook telecom_churn_eda.ipynb
```

> Make sure `Churn.csv` is in the same directory as the notebook before running.

## Dataset

The [Telecom Churn dataset](https://archive.ics.uci.edu/ml/datasets/Churn+in+Telecom+Dataset) from the UCI Machine Learning Repository contains records for 3,333 telecom customers with 20 potential predictor variables and a binary churn target.

---

*Part of my data science portfolio. See also: [MLB Salary Prediction](https://github.com/himanshuladdhad/mlb-salary-prediction) · [Bankruptcy Prediction Ensemble](https://github.com/himanshuladdhad/bankruptcy-prediction-ensemble)*

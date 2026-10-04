# Cognifyz Data Science Internship — Level 3

## Overview
Level 3 builds on the Level 2 handoff by using the engineered dataset to:

1) **Predictive Modeling**: train regression models to predict `Aggregate rating`.
2) **Customer Preference Analysis**: analyze how `Cuisines` relate to ratings and vote-based popularity.
3) **Data Visualization**: create visual storytelling that ties findings together.

## Dataset
- Engineered dataset (from Level 2 Task 3 Feature Engineering):
  - `Level-3/data/engineered_dataset.csv`

## Task 1 — Predictive Modeling
- Objective: Predict `Aggregate rating` (**regression** problem).
- Feature leakage: `Aggregate rating`, `Rating text`, and `Rating color` are excluded from predictors.
- Train/Test split: **80% train / 20% test** (`random_state=42`).

### Model comparison (test set)
| Model             | MAE | RMSE | R² |
| ----------------- | --: | ---: | --: |
| Linear Regression | 1.0333 | 1.2458 | 0.3181 |
| Decision Tree     | 0.2847 | 0.4363 | 0.9164 |
| Random Forest     | 0.1968 | 0.3016 | 0.9600 |

### Sensitivity: models without `Votes`
| Model             | R² with Votes | R² without Votes |
| ----------------- | ------------: | ----------------: |
| Linear Regression | 0.3181 | 0.3054 |
| Decision Tree     | 0.9164 | -0.0481 |
| Random Forest     | 0.9600 | 0.4628 |

### Key diagnostics produced
- Actual vs Predicted plots
- Residual plots (scatter + histograms)
- Random Forest feature importance (non-causal)

## Task 2 — Customer Preference Analysis
- Objective: Analyze cuisine ↔ rating and cuisine popularity by votes.
- Cuisine field handling: `Cuisines` is split on commas and **exploded** so each (restaurant, cuisine) pair is counted.
- Vote attribution: each listed cuisine receives the restaurant’s full `Votes` and `Aggregate rating` (multi-label association; totals across cuisines may overlap).

### Most popular cuisines by votes (top examples)
- North Indian, Chinese, Italian, Continental, Fast Food, American, Cafe, Mughlai, Desserts, Asian

### Higher observed mean ratings (n ≥ 30, top examples)
- Sandwich, Steak, Sushi, Breakfast, Mediterranean, Bar Food, Indian, European, BBQ, Seafood

### Lowest observed mean ratings (n ≥ 30, bottom examples)
- Biryani, Street Food, Tibetan, Raw Meats, Mithai

## Task 3 — Data Visualization
Visualizations include:
- Rating distribution histogram
- Cuisine average rating (top cuisines)
- City average rating (min sample filter)
- Feature-vs-target plots (e.g., Votes vs Aggregate rating, Price range bands, booking/delivery flags)
- Recap plots for Task 1 and Task 2 (where their output files exist)

## Technologies
- Python 3.11.15
- pandas, numpy
- matplotlib, seaborn
- scikit-learn
- joblib

## How to Run
From `Level-3/`:

python -m jupyter nbconvert --to notebook --execute --inplace \
  Task-1_Predictive_Modeling/notebook.ipynb

python -m jupyter nbconvert --to notebook --execute --inplace \
  Task-2_Customer_Preference_Analysis/notebook.ipynb

python -m jupyter nbconvert --to notebook --execute --inplace \
  Task-3_Data_Visualization/notebook.ipynb

## Limitations (high level)
- `Aggregate rating = 0` represents an “unrated” convention in the dataset; the model may struggle to separate “not rated” from genuinely low ratings.
- Cuisine popularity uses multi-label vote attribution; totals overlap across cuisines.
- Visual comparisons are descriptive; they do not prove causation.

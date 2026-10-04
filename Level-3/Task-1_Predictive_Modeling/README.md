# Task 1 — Predictive Modeling

## Objective
Train regression models to predict `Aggregate rating`.

## Dataset / Input
- `../data/engineered_dataset.csv`

## Leakage rules followed
Excluded from predictors:
- `Aggregate rating` (target)
- `Rating text`, `Rating color` (direct labels of the same rating scale)

## Train/Test split
- 80% train / 20% test (`random_state=42`)

## Models compared (test set)
| Model             | MAE | RMSE | R² |
| ----------------- | --: | ---: | --: |
| Linear Regression | 1.0333 | 1.2458 | 0.3181 |
| Decision Tree     | 0.2847 | 0.4363 | 0.9164 |
| Random Forest     | 0.1968 | 0.3016 | 0.9600 |

## Sensitivity check (without `Votes`)
| Model             | R² with Votes | R² without Votes |
| ----------------- | ------------: | ----------------: |
| Linear Regression | 0.3181 | 0.3054 |
| Decision Tree     | 0.9164 | -0.0481 |
| Random Forest     | 0.9600 | 0.4628 |

## Outputs
- Tables:
  - `outputs/tables/model_comparison.csv`
  - `outputs/tables/model_comparison_without_votes.csv`
  - `outputs/tables/model_comparison_votes_ablation.csv`
  - `outputs/tables/test_predictions.csv`
- Figures:
  - `outputs/figures/actual_vs_predicted.png`
  - `outputs/figures/residuals.png`
  - `outputs/figures/residual_histograms.png`
  - `outputs/figures/rf_feature_importance.png`
  - `outputs/figures/r2_votes_ablation.png`
- Models:
  - `models/*.joblib`

# Task 3 — Data Visualization

## Objective
Create the visual storytelling layer for Level 3, connecting:
- Predictive modeling outcomes (Task 1)
- Cuisine preference outcomes (Task 2)

## Dataset / Input
- `../data/engineered_dataset.csv`
- Optional recap inputs (if present):
  - Task 1: `../Task-1_Predictive_Modeling/outputs/tables/model_comparison.csv`
  - Task 2: `../Task-2_Customer_Preference_Analysis/outputs/tables/cuisine_stats_all.csv`

## Visualization groups
1) **Rating distribution**
- Histogram of `Aggregate rating` with mean/median overlays.

2) **Cuisine / City comparisons**
- Average rating by cuisine (top cuisines, with sample filters).
- Average rating by city (min sample filter).

3) **Feature vs target**
- Votes vs rating (log-scaled votes)
- Price range vs rating
- Booking/delivery flags vs rating

## Outputs
- Figures are saved to `outputs/figures/`, including:
  - `rating_distribution_histogram.png`
  - `avg_rating_by_cuisine.png`
  - `avg_rating_by_city.png`
  - `votes_vs_rating.png`
  - `rating_by_price_range_boxplot.png`
  - `rating_by_booking_and_delivery.png`
  - recap plots: `task1_model_error_comparison.png`, `task1_model_r2_comparison.png`, `task2_top_cuisines_votes.png`

## Limitations
Charts are descriptive and do not establish causation.

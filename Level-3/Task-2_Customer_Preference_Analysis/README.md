# Task 2 — Customer Preference Analysis

## Objective
Analyze the relationship between cuisine types, ratings, and popularity (by votes).

## Dataset / Input
- `../data/engineered_dataset.csv`

## Cuisine field handling
`Cuisines` is comma-separated and multi-label.

Transformation used:
- Drop missing/blank cuisines (9 rows)
- Split on commas and explode into a long format of (restaurant × cuisine)
- De-duplicate repeated (Restaurant ID, Cuisine) pairs

## Vote attribution methodology (documented)
Each cuisine label receives the restaurant’s full `Votes` and `Aggregate rating`.
- This is an association approach for multi-label data.
- Totals across cuisines may overlap, so cuisine-level vote sums exceed the dataset-wide vote sum.

## Outputs
- Tables:
  - `outputs/tables/cuisine_stats_all.csv`
  - `outputs/tables/cuisine_popularity_by_votes.csv`
  - `outputs/tables/cuisine_rating_min30.csv`
- Figures:
  - `outputs/figures/top_cuisines_by_votes.png`
  - `outputs/figures/top_cuisines_by_restaurant_count.png`
  - `outputs/figures/top_cuisines_by_mean_rating.png`
  - `outputs/figures/cuisine_votes_vs_mean_rating.png`

## Key findings (from computed results)
- Most popular cuisines by votes (top examples): North Indian, Chinese, Italian, Continental, Fast Food, American, Cafe, Mughlai, Desserts, Asian.
- Higher observed mean ratings (n ≥ 30, top examples): Sandwich, Steak, Sushi, Breakfast, Mediterranean, Bar Food, Indian, European, BBQ, Seafood.
- Lowest observed mean ratings (n ≥ 30, bottom examples): Biryani, Street Food, Tibetan, Raw Meats, Mithai.

## Limitations
- Multi-label attribution overlaps votes across cuisines.
- Small-sample cuisines are filtered out for “higher/lower” ranking claims (n ≥ 30).
- Observed averages are descriptive associations, not causal evidence.

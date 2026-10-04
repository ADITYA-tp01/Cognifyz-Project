# Task 1: Table Booking & Online Delivery

## Objective

Investigate whether table booking and online delivery are associated with restaurant ratings and price ranges.

## Methodology

- Loaded `Dataset.csv` (read-only).
- Identified columns: `Has Table booking`, `Has Online delivery`, `Aggregate rating`, `Price range`.
- Validated data: no missing values in these columns, no duplicates.
- Calculated distribution percentages and group-wise averages.
- Generated visualizations with `plt.savefig` before `plt.show`.

## Results

| Table Booking | Restaurant Count | Percentage |
|---------------|------------------:|----------:|
| Yes           |             1,158 |     12.12% |
| No            |             8,393 |     87.88% |

| Online Delivery | Restaurant Count | Percentage |
|-----------------|------------------:|----------:|
| Yes             |             2,451 |     25.66% |
| No              |             7,100 |     74.34% |

| Table Booking | Restaurants | Average Rating |
|---------------|------------:|--------------:|
| Yes           |       1,158 |         3.442 |
| No            |       8,393 |         2.559 |

| Price Range | Delivery Yes | Delivery No | Delivery % |
|------------:|-------------:|------------:|----------:|
| 1           |          701 |       3,743 |     15.77% |
| 2           |        1,286 |       1,827 |     41.31% |
| 3           |          411 |         997 |     29.19% |
| 4           |           53 |         533 |      9.04% |

## Visualizations

Saved to `outputs/figures/`:
- `table_booking_distribution.png`
- `online_delivery_distribution.png`
- `table_booking_vs_rating.png`
- `online_delivery_by_price_range.png`

Tables saved to `outputs/tables/` as CSV.

## Findings

1. 12.12% of restaurants offer table booking; 87.88% do not.
2. 25.66% offer online delivery; 74.34% do not.
3. Restaurants with table booking have an average rating of 3.442 vs 2.559 without (difference = 0.883).
4. Online delivery availability varies across price ranges; price range 2 has the highest share (41.31%), price range 4 the lowest (9.04%).

## Conclusion

Table booking is a minority feature but is associated with higher ratings. Online delivery is more common but still not majority; its availability peaks in the mid price range (2).
# Task 2: Price Range Analysis

## Objective

Determine the most common price range, average rating per range, and the rating color associated with the highest average rating.

## Methodology

- Loaded `Dataset.csv` (read-only).
- Identified columns: `Price range`, `Aggregate rating`, `Rating color`, `Rating text`.
- Validated mapping of `Rating color` to `Rating text` (e.g., Yellow = Good, Dark Green = Excellent).
- Calculated counts, percentages, and mean ratings.
- Mapped the highest price-range average onto the dataset's observed rating-color bands.

## Results

| Price Range | Restaurant Count | Percentage |
|------------:|------------------:|----------:|
| 1           |             4,444 |     46.53% |
| 2           |             3,113 |     32.59% |
| 3           |             1,408 |     14.74% |
| 4           |               586 |      6.14% |

**Most common price range**: 1

| Price Range | Number of Restaurants | Average Rating |
|------------:|----------------------:|--------------:|
| 1           |                 4,444 |          2.000 |
| 2           |                 3,113 |          2.941 |
| 3           |                 1,408 |          3.683 |
| 4           |                   586 |          3.818 |

**Highest average rating**: Price range 4 at 3.818, mapped to dataset rating color **Yellow** (text: Good).

## Visualizations

Saved to `outputs/figures/`:
- `price_range_distribution.png`
- `average_rating_by_price_range.png`
- `rating_color_mean_bands.png`

Tables saved to `outputs/tables/` as CSV.

## Findings

1. The most common price range is 1, with 4,444 restaurants (46.53%).
2. Average rating increases with price range; price range 1 lowest (2.000), price range 4 highest (3.818).
3. The dataset rating color representing this highest average rating is Yellow (Good), based on the observed `Aggregate rating` bands.

## Conclusion

Lower price ranges dominate the dataset. Higher price ranges have higher average ratings. The highest average rating among price ranges maps to Yellow (Good) in the dataset's rating-color scheme.
# Cognifyz Data Science Internship — Level 2

## Overview

This repository contains the implementation of **Cognifyz Level 2**, which consists of three tasks:
1. **Table Booking & Online Delivery Analysis**
2. **Price Range Analysis**
3. **Feature Engineering**

All work is performed on the provided `Dataset.csv` (unchanged). The engineered dataset from Task 3 is the handoff for Level 3.

## Dataset

- **File**: `Dataset.csv` (raw, not modified)
- **Rows**: 9,551
- **Columns**: 21
- **Key columns used**:
  - `Restaurant Name`, `Address`
  - `Has Table booking`, `Has Online delivery`
  - `Aggregate rating`, `Price range`
  - `Rating color`, `Rating text`
  - `Cuisines`, `Votes`, `Average Cost for two`

## Project Structure

```
Level-2/
├── Task-1_Table_Booking_Online_Delivery/
│   ├── notebook.ipynb
│   ├── outputs/
│   │   ├── figures/
│   │   └── tables/
│   └── README.md
├── Task-2_Price_Range_Analysis/
│   ├── notebook.ipynb
│   ├── outputs/
│   │   ├── figures/
│   │   └── tables/
│   └── README.md
├── Task-3_Feature_Engineering/
│   ├── notebook.ipynb
│   ├── outputs/
│   │   ├── figures/
│   │   └── tables/
│   ├── data/
│   │   └── engineered_dataset.csv
│   └── README.md
└── README.md
```

## Methodology

Each notebook follows the 11-section structure from the plan:

1. Title & Objective
2. Dataset Overview
3. Import Libraries
4. Load Dataset
5. Data Validation
6. Analysis / Feature Engineering
7. Visualizations
8. Results
9. Findings
10. Conclusion
11. (Optional) Additional Notes

## Task 1 — Table Booking & Online Delivery

**Objective**: Investigate whether restaurant services (table booking, online delivery) are associated with ratings and price ranges.

**Key Outputs**:
- Table-booking distribution (12.12% Yes, 87.88% No)
- Online-delivery distribution (25.66% Yes, 74.34% No)
- Average ratings: with table booking = 3.442, without = 2.559
- Online delivery availability by price range (highest in price range 2 at 41.31%)
- Saved tables & figures in `outputs/`

**Findings**:
1. 12.12% of restaurants offer table booking; 87.88% do not.
2. 25.66% offer online delivery; 74.34% do not.
3. Restaurants with table booking have an average rating of 3.442, compared with 2.559 for those without it (difference = 0.883).
4. Online delivery availability varies across price ranges; price range 2 has the highest share (41.31%), while price range 4 has the lowest (9.04%).

## Task 2 — Price Range Analysis

**Objective**: Determine the most common price range, average rating per range, and the rating color associated with the highest average rating.

**Key Outputs**:
- Most common price range: 1 (46.53% of restaurants)
- Average ratings by price range:
  - Price range 1: 2.000
  - Price range 2: 2.941
  - Price range 3: 3.683
  - Price range 4: 3.818
- Highest average rating is in price range 4 (3.818), mapped to dataset rating color **Yellow** (text: Good).

**Findings**:
1. The most common price range is 1, with 4,444 restaurants (46.53% of the dataset).
2. Average aggregate rating increases with price range; price range 1 has the lowest (2.000) and price range 4 the highest (3.818).
3. The dataset rating color representing this highest average rating is Yellow (Good), based on the observed `Aggregate rating` bands in the `Rating color` column.

## Task 3 — Feature Engineering

**Objective**: Create new features for Level 3 modeling without modifying the original dataset.

**Features Added**:
| Feature | Type | Description |
|---|---|---|
| `Restaurant_Name_Length` | Numerical | Number of characters in restaurant name |
| `Address_Length` | Numerical | Number of characters in address |
| `Has_Table_Booking` | Binary | 1 if `Has Table booking` = Yes, else 0 |
| `Has_Online_Delivery` | Binary | 1 if `Has Online delivery` = Yes, else 0 |
| `Cuisine_Count` | Numerical | Number of comma-separated cuisines; 0 if missing |

**Validation**:
- No data leakage
- Binary columns ∈ {0, 1}
- Length features ≥ 0
- Original columns retained
- Engineered dataset saved to `Task-3_Feature_Engineering/data/engineered_dataset.csv`

**Findings**:
1. Five features added; original 21 columns retained.
2. `Restaurant_Name_Length` ranges from 2 to 54 characters.
3. `Address_Length` ranges from 13 to 132 characters.
4. `Has_Table_Booking` and `Has_Online_Delivery` are binary and match the original Yes/No columns.
5. `Cuisine_Count` = 0 for 9 rows (missing/empty `Cuisines`).
6. Engineered file is the Level 2 → Level 3 handoff.

## Technologies Used

- Python 3.11.15
- pandas, numpy, matplotlib, seaborn
- Jupyter notebook (executed headlessly)

## How to Run

```bash
# From the Level-2 directory
python -m jupyter nbconvert --to notebook --execute --inplace \
    Task-1_Table_Booking_Online_Delivery/notebook.ipynb
python -m jupyter nbconvert --to notebook --execute --inplace \
    Task-2_Price_Range_Analysis/notebook.ipynb
python -m jupyter nbconvert --to notebook --execute --inplace \
    Task-3_Feature_Engineering/notebook.ipynb
```

Outputs (tables, figures, engineered CSV) will appear in each task’s `outputs/` and `data/` folders.

## Quality Assurance

- Original `Dataset.csv` never modified.
- No invented columns or results.
- No unnecessary machine learning in Level 2.
- All values derived from actual calculations.
- Visualizations are titled, labeled, and based on computed values.
- Requirements reflect only actually used libraries (pandas, numpy, matplotlib, seaborn, jupyter).
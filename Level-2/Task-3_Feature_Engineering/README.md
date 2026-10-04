# Task 3: Feature Engineering

## Objective

Create additional numerical and binary features for Level 3 modeling without modifying the original dataset.

## Methodology

- Loaded `Dataset.csv` read-only.
- Classified columns as numerical, categorical, or text after schema inspection.
- Added five documented features:
  - `Restaurant_Name_Length`: character count of `Restaurant Name`
  - `Address_Length`: character count of `Address`
  - `Has_Table_Booking`: 1 for Yes, 0 for No
  - `Has_Online_Delivery`: 1 for Yes, 0 for No
  - `Cuisine_Count`: count of comma-separated cuisines; 0 for missing/empty values
- Retained all 21 original columns.
- Validated types, missing values, ranges, duplicate rows, and binary values.

## Results

- Rows: 9,551
- Columns before: 21
- Columns after: 26
- New features: 5
- `Has_Table_Booking = 1`: 1,158
- `Has_Online_Delivery = 1`: 2,451
- `Restaurant_Name_Length`: 2 to 54 characters
- `Address_Length`: 13 to 132 characters
- `Cuisine_Count = 0`: 9 rows

The original 9 missing `Cuisines` values are represented as `Cuisine_Count = 0`. No missing values were introduced in the five new features.

## Feature Dictionary

| Feature | Type | Description |
|---|---|---|
| `Restaurant_Name_Length` | Numerical | Number of characters in restaurant name |
| `Address_Length` | Numerical | Number of characters in address |
| `Has_Table_Booking` | Binary | 1 if table booking is Yes, otherwise 0 |
| `Has_Online_Delivery` | Binary | 1 if online delivery is Yes, otherwise 0 |
| `Cuisine_Count` | Numerical | Count of cuisine labels; 0 if missing/empty |

## Validation

- Original `Dataset.csv` was not written to.
- Both encoded columns contain only 0 and 1.
- Encoded values exactly match the original Yes/No columns.
- Length and cuisine-count features are non-negative integers.
- Reloaded engineered dataset has shape `(9551, 26)`.
- No duplicate rows were introduced.

## Outputs

- Engineered dataset: `data/engineered_dataset.csv`
- Feature dictionary: `outputs/tables/feature_dictionary.csv`
- Feature inventory: `outputs/tables/feature_inventory.csv`
- Binary feature counts: `outputs/tables/binary_feature_counts.csv`
- Visualizations: `outputs/figures/text_length_distributions.png`, `outputs/figures/encoded_service_features.png`

## Conclusion

The engineered dataset is validated and ready for Level 3. It contains only documented, leakage-free transformations suitable for descriptive analysis or predictive modeling.

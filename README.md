# Flight Price Prediction Project

## Overview
This project focuses on predicting flight prices using a dataset containing various flight-related features. The goal is to preprocess the raw data, extract meaningful features, and prepare it for machine learning model training. The notebook covers data loading, extensive feature engineering, and categorical data encoding.

## Dataset
The project utilizes two datasets:
- `Data_Train.xlsx`: Contains the training data with flight details and prices.
- `Test_set.xlsx`: Contains the test data with flight details (prices are missing and are the target for prediction).

Both datasets are concatenated into a single DataFrame (`final_df`) for consistent preprocessing.

## Feature Engineering
Several features have been engineered from existing columns to provide more granular and useful information for modeling:

### Date and Time Features
- **`Date_of_Journey`**: Split into `Date`, `Month`, and `Year` columns, all converted to integer types. The original `Date_of_Journey` column is then dropped.
- **`Arrival_Time`**: Processed to extract `Arrival_hour` and `Arrival_min`, converted to integers. The original `Arrival_Time` column is dropped.
- **`Dep_Time`**: Processed to extract `Dept_hour` and `Dept_min`, converted to integers. The original `Dep_Time` column is dropped.

### Duration Feature
- **`Duration`**: Extracted the hour component into `duration_hour` and converted to integer. Rows where `duration_hour` was '5m' were identified and removed, indicating potential data anomalies. The original `Duration` column is dropped.

### Total Stops
- **`Total_Stops`**: Mapped categorical string values ('non-stop', '1 stop', etc.) to numerical integer representations (0, 1, etc.).

### Route Column
- The `Route` column was dropped as its information might be redundant or too complex for direct use after extracting other features.

## Data Encoding
Categorical features have been transformed into numerical representations suitable for machine learning algorithms:

- **Label Encoding**: `Airline`, `Source`, `Destination`, and `Additional_Info` columns were encoded using `sklearn.preprocessing.LabelEncoder`. This assigns a unique integer to each unique category.

- **One-Hot Encoding**: While `LabelEncoder` was applied to `Airline`, `Source`, and `Destination`, a subsequent step demonstrated `pd.get_dummies` for one-hot encoding these columns, which creates new binary columns for each category, avoiding ordinality assumptions.

## Setup and Prerequisites
To run this notebook, you will need the following Python libraries:
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

You can install them using pip:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
```
(Note: `openpyxl` is required for reading `.xlsx` files with pandas).

## Usage
1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```
2. Ensure you have the `Data_Train.xlsx` and `Test_set.xlsx` files in the same directory as your notebook.
3. Run the Jupyter Notebook cells sequentially to perform data preprocessing and feature engineering.

Further steps would involve model training, evaluation, and hyperparameter tuning.

# Raw Dataset

This folder contains the raw dataset files used for the Sales & Demand Forecasting project.

## Dataset Source

Kaggle — Store Sales - Time Series Forecasting

Dataset:
https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data

## Raw Files Used

The project uses the following raw files:

- train.csv
- test.csv
- stores.csv
- transactions.csv
- oil.csv
- holidays_events.csv
- sample_submission.csv

## Why the Raw CSV Files Are Not Stored in This Repository

The original Kaggle dataset contains large CSV files, particularly `train.csv` and `test.csv`.

To keep this GitHub repository lightweight and practical, the original raw CSV files are not uploaded.

The processed modeling dataset generated from the raw data is available in:

`data/processed/daily_sales_model_data.csv`

## Reproducing the Project

1. Download the dataset from the Kaggle source above.
2. Place the downloaded CSV files inside this `data/raw/` folder.
3. Run the notebook:

`notebooks/sales_forecasting.ipynb`

The notebook performs data preparation, feature engineering, model training, evaluation, and forecasting.
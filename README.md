````markdown
# Retail Sales Forecasting & Business Demand Planning System

## Future Interns — Machine Learning Task 1

An end-to-end machine learning project for forecasting retail sales and supporting business demand planning using historical sales and time-series features.

## Project Overview

Retail businesses need reliable sales forecasts for inventory planning, staffing, promotions, and daily operations.

This project develops a machine learning-based retail sales forecasting system using the Store Sales — Time Series Forecasting dataset. Multiple regression and ensemble models were developed and evaluated using chronological validation.

The final selected model is XGBoost, which achieved the best overall validation performance among the evaluated models.

## Business Problem

Retail sales vary based on:

- Day-of-week patterns
- Monthly and seasonal effects
- Weekend behavior
- Previous sales patterns
- Promotions
- Holidays
- Long-term trends

The objective is to use historical sales patterns and time-series features to predict future daily sales and support business demand planning.

## Dataset

Dataset: Store Sales — Time Series Forecasting

Source:

https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data

The dataset contains retail sales information from stores and product families in Ecuador.

### Dataset Files

- train.csv
- test.csv
- stores.csv
- transactions.csv
- oil.csv
- holidays_events.csv
- sample_submission.csv

Raw Kaggle data is not included in the repository because of dataset size and distribution considerations.

## Project Workflow

1. Business problem definition
2. Data understanding
3. Data quality analysis
4. Data preprocessing
5. Daily sales aggregation
6. Exploratory data analysis
7. Time-series feature engineering
8. Chronological train-validation split
9. Baseline model development
10. Random Forest improvement
11. HistGradientBoosting experimentation
12. XGBoost experimentation
13. Model comparison
14. Error analysis
15. Feature importance analysis
16. 30-day future sales forecasting
17. Business insight generation

## Feature Engineering

### Calendar Features

- Year
- Month
- Quarter
- Day
- Day of week
- Weekend indicator

### Lag Features

- Lag 1
- Lag 3
- Lag 5
- Lag 7
- Lag 14
- Lag 21
- Lag 28
- Lag 30

### Rolling Features

- Rolling mean 3
- Rolling mean 7
- Rolling mean 14
- Rolling mean 30
- Rolling standard deviation 7
- Rolling standard deviation 14

### Exponential Weighted Features

- EWM 7
- EWM 14

Historical rolling features were shifted to prevent future-data leakage.

## Validation Strategy

A chronological train-validation split was used instead of a random split because this is a time-series forecasting problem.

Validation period:

**2016-07-01 to 2017-08-15**

This approach better represents how the model would perform when predicting future observations from historical data.

## Models Evaluated

- Baseline Random Forest
- Improved Random Forest
- HistGradientBoosting
- Tuned HistGradientBoosting
- XGBoost
- Tuned XGBoost

## Model Performance

|            Model           |       MAE     |      RMSE      |      MAPE      |
|----------------------------|---------------|----------------|----------------|
| Baseline Random Forest     | 76,821.42     | 133,556.96     | 47.50%         |
| Improved Random Forest     | 70,350.96     | 110,149.09     | 28.28%         |
| HistGradientBoosting       | 75,580.38     | 113,794.55     | 27.77%         |
| Tuned HistGradientBoosting | 82,841.34     | 119,229.88     | 26.69%         |
| **XGBoost**                | **67,607.60** | **105,464.50** | **24.64%**     |
| Tuned XGBoost              | 77,764.03     | 114,031.17     | 25.44%         |

## Final Model

### XGBoost

XGBoost was selected as the final model because it achieved the lowest validation error among the evaluated models.

### Performance

- MAE: **67,607.60**
- RMSE: **105,464.50**
- MAPE: **24.64%**

Compared with the baseline Random Forest:

- MAE improved by approximately **12.0%**
- RMSE improved by approximately **21.0%**
- MAPE improved by approximately **48.1%**

The tuned XGBoost model did not outperform the original XGBoost model on the chronological validation set. Therefore, the original XGBoost model was selected as the final model.

## Feature Importance

The most influential XGBoost features were:

|      Feature      | Importance |
|-------------------|------------|
| `lag_7`           | 23.96%     |
| `is_weekend`      | 22.25%     |
| `lag_14`          | 12.10%     |
| `day_of_week_num` | 8.35%      |
| `rolling_mean_7`  | 8.07%      |
| `lag_1`           | 5.15%      |
| `ewm_7`           | 5.01%      |
| `rolling_mean_3`  | 2.54%      |
| `day`             | 1.91%      |
| `ewm_14`          | 1.89%      |

The results show that recent weekly sales patterns and weekly calendar behavior are important for predicting retail demand.

## Business Insights

The final XGBoost model achieved:

- Average actual daily sales: **831,372.98**
- Average predicted daily sales: **811,621.94**
- MAE as a percentage of average sales: **8.13%**
- Maximum actual daily sales: **1,463,083.96**
- Maximum predicted daily sales: approximately **1.20 million**

These results can support:

- Inventory planning
- Workforce planning
- Promotion planning
- Demand monitoring
- Operational decision-making

## 30-Day Sales Forecast

The final XGBoost model was used to generate a recursive 30-day sales forecast.

Forecast output:

`outputs_xgboost/forecasts/30_day_sales_forecast.csv`

Forecast visualization:

`outputs_xgboost/figures/xgboost_future_30_day_forecast.png`

## Project Structure

```text
FUTURE_ML_01/
│
├── data/
│   ├── raw/
│   │   └── README.md
│   └── processed/
│       └── daily_sales_model_data.csv
│
├── notebooks/
│   ├── random_forest.ipynb
│   ├── improved_random_forest.ipynb
│   ├── hist_gradient_boosting.ipynb
│   └── xgboost.ipynb
│
├── models/
│   ├── random_forest_model.joblib
│   ├── random_forest_features.joblib
│   ├── xgboost_model.joblib
│   └── xgboost_features.joblib
│
├── outputs_random_forest/
│   ├── figures/
│   ├── forecasts/
│   ├── model_performance.csv
│   ├── feature_importance.csv
│   └── business_insights.csv
│
├── outputs_xgboost/
│   ├── figures/
│   ├── forecasts/
│   ├── model_performance.csv
│   ├── feature_importance.csv
│   ├── business_insights.csv
│   ├── final_model_comparison.csv
│   └── final_xgboost_summary.csv
│
├── README.md
├── requirements.txt
└── .gitignore
````

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* XGBoost
* Jupyter Notebook
* Joblib
* Git
* GitHub

## Key Learning Outcomes

* Time-series data preparation
* Exploratory data analysis
* Feature engineering
* Lag and rolling features
* Chronological model validation
* Ensemble machine learning
* XGBoost regression
* Hyperparameter experimentation
* Model comparison
* Error analysis
* Feature importance analysis
* Future demand forecasting
* Business-oriented machine learning

## Task Status

**Future Interns Machine Learning Task 1 — Completed**

The project provides an end-to-end machine learning workflow from retail sales data preparation to model evaluation and 30-day future demand forecasting.

```
```

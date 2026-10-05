````markdown
# Retail Sales Forecasting & Business Demand Planning System

## Future Interns — Machine Learning Task 1

A machine learning project for analyzing historical retail sales, identifying demand patterns, comparing forecasting models, and generating a 30-day sales forecast for business demand planning.

---

## Project Overview

Retail businesses need accurate demand estimates to support inventory planning, promotional decisions, staffing, and day-to-day operations.

This project uses historical retail sales data to:

- Analyze overall sales trends
- Identify weekly and monthly seasonality
- Analyze promotional activity
- Study holiday and external factors
- Create time-series features
- Compare machine learning models
- Analyze prediction errors
- Identify important forecasting features
- Generate a 30-day future sales forecast

---

## Dataset

The project uses the **Store Sales - Time Series Forecasting** dataset from Kaggle.

The dataset contains retail sales information from stores and product families along with promotion and external information.

### Dataset Summary

| Property | Value |
|---|---:|
| Total records | 3,000,888 |
| Stores | 54 |
| Product families | 33 |
| Start date | 2013-01-01 |
| End date | 2017-08-15 |
| Dataset frequency | Daily |
| Target variable | Sales |

Raw dataset files are not included in this repository because of their size. They should be downloaded from Kaggle and placed inside `data/raw/`.

---

## Technologies Used

- Python 3.11
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook
- Joblib
- Git
- GitHub

---

## Project Workflow

```text
Raw Dataset
      ↓
Data Understanding
      ↓
Data Cleaning
      ↓
Daily Sales Aggregation
      ↓
Exploratory Data Analysis
      ↓
Feature Engineering
      ↓
Chronological Train-Test Split
      ↓
Model Training
      ↓
Model Evaluation
      ↓
Error Analysis
      ↓
Feature Importance Analysis
      ↓
30-Day Future Forecast
      ↓
Business Insights
````

---

## Data Preparation

The following data preparation steps were performed:

* Checked missing values
* Checked duplicate records
* Converted date columns to datetime format
* Sorted records chronologically
* Aggregated sales at daily level
* Analyzed sales distribution
* Examined weekly sales patterns
* Examined monthly sales patterns
* Analyzed promotional activity
* Examined holiday information
* Examined the relationship between oil prices and sales

Extreme sales values were not automatically removed because unusual values can represent genuine business demand.

---

## Exploratory Data Analysis

### Overall Sales Trend

Daily total sales were analyzed across the complete historical period to understand long-term growth, fluctuations, and unusual demand periods.

### Weekly Seasonality

Average sales were compared across the days of the week to identify recurring weekly demand patterns.

### Monthly Seasonality

Average sales were analyzed by month to identify recurring seasonal behavior.

### Promotion Analysis

The relationship between the number of products on promotion and daily sales was analyzed.

### Holiday Analysis

Sales on holiday and non-holiday dates were compared to identify calendar effects.

### External Factor Analysis

Oil prices were compared with daily sales to examine their relationship with overall retail demand.

---

## Feature Engineering

Time-series and calendar-based features were created for machine learning.

### Calendar Features

* Year
* Month
* Quarter
* Day
* Day of Week
* Weekend Indicator

### Lag Features

* Lag 1 day
* Lag 7 days
* Lag 14 days
* Lag 30 days

### Rolling Features

* 7-day rolling mean
* 14-day rolling mean
* 30-day rolling mean

Rolling features were calculated using previous observations to avoid using future sales information.

---

## Train-Test Strategy

A chronological train-test split was used instead of a random split.

```text
Historical Data
      ↓
Training Period
2013 → 2016
      ↓
Testing Period
2017
```

This approach is appropriate for time-series forecasting because future observations should not be used to train the model.

---

## Machine Learning Models

### Linear Regression

Linear Regression was used as the baseline model.

### Random Forest Regressor

Random Forest was used to capture nonlinear relationships between historical sales, calendar features, lag features, and rolling statistics.

---

## Model Performance

| Model             |           MAE |           RMSE |       MAPE |
| ----------------- | ------------: | -------------: | ---------: |
| Linear Regression |     83,290.98 |     141,134.40 |     49.63% |
| Random Forest     | **76,821.42** | **133,556.96** | **47.50%** |

### Best Performing Model

**Random Forest Regressor**

Random Forest achieved lower MAE, RMSE, and MAPE than Linear Regression on the chronological test period.

---

## Feature Importance

The Random Forest model identified recent historical sales patterns as the strongest predictors.

The most important features included:

1. `lag_7`
2. `lag_14`
3. `lag_1`
4. `rolling_mean_7`
5. `day`
6. `day_of_week_num`

This indicates that recent daily and weekly sales patterns have a strong influence on predicted demand.

---

## Error Analysis

Prediction errors were analyzed over the test period to identify periods where the model performed poorly.

Error analysis helps identify unusual demand patterns, holidays, sharp sales changes, and periods where forecasting becomes more difficult.

---

## Future Sales Forecast

A recursive forecasting approach was used to generate a **30-day future sales forecast** after the end of the available historical data.

### Forecast Period

**2017-08-16 to 2017-09-14**

### Forecast Summary

| Metric                   |        Value |
| ------------------------ | -----------: |
| Average forecasted sales |   795,445.31 |
| Highest forecasted sales | 1,186,865.70 |
| Lowest forecasted sales  |   642,288.34 |

The forecast uses historical sales, lag features, rolling averages, and calendar features.

---

## Business Insights

* Average historical daily sales were approximately **637,556**.
* The highest recorded daily sales were approximately **1.46 million**.
* **Sunday** had the highest average sales among the days of the week.
* **December** had the highest average monthly sales.
* Random Forest performed better than the Linear Regression baseline.
* Recent weekly sales patterns were among the strongest predictors of future demand.

These insights can support short-term inventory planning, demand monitoring, and promotional planning.

---

## Project Outputs

```text
outputs/
├── business_insights.csv
├── feature_importance.csv
├── model_performance.csv
└── forecasts/
    ├── 30_day_sales_forecast.csv
    └── final_sales_forecast.csv
```

### Saved Model Files

```text
models/
├── random_forest_sales_model.joblib
└── model_features.json
```

---

## Project Structure

```text
FUTURE_ML_01/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   └── sales_forecasting.ipynb
│
├── src/
│
├── models/
│   ├── random_forest_sales_model.joblib
│   └── model_features.json
│
├── outputs/
│   ├── figures/
│   ├── forecasts/
│   ├── business_insights.csv
│   ├── feature_importance.csv
│   └── model_performance.csv
│
├── dashboard/
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/harshith3987-lgtm/FUTURE_ML_01.git
cd FUTURE_ML_01
```

### 2. Create Virtual Environment

```bash
python -m venv .venv
```

### 3. Activate Environment

For Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Add Dataset

Download the **Store Sales - Time Series Forecasting** dataset from Kaggle and place the required CSV files inside:

```text
data/raw/
```

Required files:

```text
train.csv
test.csv
stores.csv
transactions.csv
oil.csv
holidays_events.csv
```

### 6. Run the Notebook

Open:

```text
notebooks/sales_forecasting.ipynb
```

Run the notebook cells sequentially to reproduce the analysis, model training, evaluation, and forecasting results.

---

## Model Evaluation

The models were evaluated using:

### Mean Absolute Error (MAE)

Measures the average absolute difference between actual and predicted sales.

### Root Mean Squared Error (RMSE)

Measures prediction error while giving greater weight to larger errors.

### Mean Absolute Percentage Error (MAPE)

Measures the average percentage difference between actual and predicted values.

Lower values indicate better forecasting performance.

---

## Key Results

The **Random Forest Regressor** performed better than the Linear Regression baseline across all three evaluation metrics.

```text
Random Forest
MAE  :  76,821.42
RMSE : 133,556.96
MAPE :      47.50%
```

The model was then used to generate a 30-day recursive sales forecast.

---

## Business Applications

The forecasting system can support:

* Inventory planning
* Demand planning
* Sales monitoring
* Promotional planning
* Workforce planning
* Short-term business forecasting
* Identification of recurring demand patterns

---

## Limitations

* The current forecasting model works with aggregated daily sales.
* Store-level and product-family-level forecasting can be developed further.
* Additional external variables can be incorporated directly into the forecasting model.
* Hyperparameter tuning has not been extensively performed.
* Forecast uncertainty and confidence intervals are not currently included.

---

## Future Improvements

* Hyperparameter tuning
* Store-level forecasting
* Product-family forecasting
* Direct integration of promotion features into the forecasting model
* Holiday-aware forecasting
* Advanced time-series models
* Gradient boosting models
* Forecast confidence intervals
* Interactive Power BI dashboard
* Automated forecasting pipeline
* Model monitoring and retraining

---

## Conclusion

This project demonstrates an end-to-end machine learning workflow for retail sales forecasting.

Historical sales data was analyzed to identify trends, seasonality, promotional patterns, holiday effects, and external relationships. Time-based lag and rolling features were then created and used to train machine learning models.

Among the evaluated models, the **Random Forest Regressor** achieved the best performance and was used for future demand forecasting.

The final system provides both predictive results and business-oriented insights that can support retail demand planning and decision-making.

---

## Project Status

**Completed — Future Interns Machine Learning Task 1**

The project includes:

* Data understanding
* Data preparation
* Exploratory data analysis
* Feature engineering
* Time-based train-test splitting
* Machine learning model training
* Model comparison
* Model evaluation
* Error analysis
* Feature importance analysis
* 30-day future forecasting
* Business insights
* Saved model and output files

---

## Author

**Harshith CH**

B.Tech — Computer Science and Engineering (AI & ML)

GitHub: [https://github.com/harshith3987-lgtm](https://github.com/harshith3987-lgtm)

```
```

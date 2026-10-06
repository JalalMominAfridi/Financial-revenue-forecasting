# Financial-revenue-forecasting
Time-series forecasting of U.S. retail sales using Naive, Seasonal Naive, ARIMA, SARIMA and Exponential Smoothing models.
# Financial Revenue Forecasting

## Overview

This project develops a time-series forecasting model using real-world monthly U.S. retail sales data.

The objective is to determine whether statistical forecasting models can improve predictive performance compared with simple baseline approaches.

The project evaluates five forecasting approaches:

- Naive
- Seasonal Naive
- ARIMA
- SARIMA
- Exponential Smoothing (ETS)

---

## Business Problem

Accurate revenue forecasting can support financial planning, budgeting, resource allocation, inventory planning, and strategic decision-making.

The central business question is:

> Can historical retail sales patterns be used to forecast future sales, and does statistical time-series modelling outperform simple forecasting baselines?

---

## Dataset

The analysis uses real monthly U.S. retail sales data.

**Source:** Federal Reserve Economic Data (FRED)

**Original source:** U.S. Census Bureau

**Series:** Retail Sales: Retail Trade

**Series ID:** MRTSSM44000USS

**Frequency:** Monthly

**Unit:** Millions of U.S. dollars

**Adjustment:** Seasonally Adjusted

The data was accessed programmatically through the FRED data interface.

---

## Methodology

### 1. Data Acquisition

The retail sales series was downloaded programmatically from FRED using Python.

### 2. Data Validation

The dataset was checked for:

- Missing values
- Duplicate records
- Duplicate dates
- Invalid dates
- Negative values
- Time-frequency consistency

### 3. Exploratory Analysis

The analysis examined:

- Long-term trends
- Year-over-year growth
- Rolling statistics
- Monthly seasonality
- Time-series decomposition

### 4. Train / Validation / Test

A chronological split was used to prevent future information from leaking into the model development process.

The data was divided into:

- Training period
- Validation period
- Unseen test period

### 5. Forecasting Models

Five models were compared:

#### Naive

Uses the most recent observation as the forecast.

#### Seasonal Naive

Uses the corresponding observation from the previous seasonal cycle.

#### ARIMA

Models autoregressive relationships, differencing, and moving-average effects.

#### SARIMA

Extends ARIMA by incorporating seasonal dynamics.

#### Exponential Smoothing

Models level, trend, and seasonal patterns using exponentially weighted historical observations.

---

## Evaluation Metrics

The models were evaluated using:

### MAE

Mean Absolute Error measures the average absolute difference between predicted and actual values.

### RMSE

Root Mean Squared Error penalizes larger forecasting errors more strongly.

### MAPE

Mean Absolute Percentage Error expresses average forecasting error as a percentage.

---

## Final Results

The final models were evaluated on the previously unseen test period.

| Model | MAE | RMSE | MAPE |
|---|---:|---:|---:|
| **ETS** | **7,484.08** | **8,101.02** | **1.18%** |
| SARIMA | 10,692.59 | 12,394.06 | 1.70% |
| ARIMA | 16,685.87 | 21,886.74 | 2.57% |
| Seasonal Naive | 35,038.00 | 39,185.10 | 5.45% |

### Best Model

**Exponential Smoothing (ETS)** achieved the strongest performance on the unseen test period.

It achieved:

- MAE: **7,484.08 million USD**
- RMSE: **8,101.02 million USD**
- MAPE: **1.18%**

---

## Important Model Selection Insight

An important finding was that the best model during validation was not the best model on the final test period.

Seasonal Naive initially achieved the lowest validation error.

However, when the models were evaluated on the completely unseen test period, ETS significantly outperformed the Seasonal Naive model.

This demonstrates why model selection should be based on out-of-sample performance rather than simply choosing the most sophisticated model.

---

## Final Forecast

After model evaluation, the ETS model was retrained using all available historical observations.

The model was then used to forecast the following 12 months.

### Forecast Summary

**Total forecasted sales:** approximately **$8.085 trillion**

**First-month forecast growth:** approximately **0.40%**

**Forecasted 12-month growth:** approximately **4.45%**

![12-Month Revenue Forecast](images/revenue_forecast.png)

---

## Business Interpretation

The model forecasts approximately 4.45% growth in retail sales over the next twelve months compared with the previous twelve-month period.

The forecast can support:

- Revenue planning
- Budget preparation
- Inventory management
- Workforce planning
- Capacity planning
- Strategic planning
- Financial scenario analysis

The forecast should not be interpreted as a guaranteed outcome. Future sales may be affected by inflation, interest rates, consumer confidence, unemployment, supply-chain disruptions, policy changes, and unexpected economic events.

---

## Limitations

The current model is primarily based on historical sales behavior.

It does not explicitly incorporate external explanatory variables such as:

- Inflation
- Interest rates
- GDP
- Consumer confidence
- Unemployment
- Consumer spending
- Retail employment

Future improvements could include:

- SARIMAX with external variables
- Dynamic regression
- Prophet
- XGBoost
- Gradient boosting
- LSTM
- Ensemble forecasting

---

## Technologies

- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Statsmodels
- Google Colab

---

## Repository Structure

```text
financial-revenue-forecasting/
│
├── financial_revenue_forecasting.ipynb
├── README.md
├── requirements.txt
│
├── images/
│   └── revenue_forecast.png
│
└── results/
    ├── final_model_comparison.csv
    └── future_revenue_forecast.csv

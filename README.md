# AI-Based Decision-Support System for Day-Ahead Electricity-Price Forecasting in the German Power Market

This repository contains the code and analysis developed for my M.Sc. Data Science thesis. The project explores how statistical and machine-learning models can forecast German day-ahead electricity prices and support electricity-market decisions.

The research considers both **forecasting accuracy** and the **practical economic value of forecast-informed decisions**.

## Project Overview

Electricity prices reflect changing demand, renewable generation, and recurring daily and seasonal patterns. These relationships make price forecasting a challenging task, particularly during periods of high volatility.

This project develops an end-to-end workflow covering data acquisition, preprocessing, exploratory analysis, feature engineering, forecasting, and decision-support evaluation.

## Research Questions

1. How accurately can statistical and machine-learning models forecast German day-ahead electricity prices?
2. How do load, renewable generation, and temporal features contribute to forecasting performance?
3. How do forecast-informed bidding decisions compare with benchmark strategies?
4. What economic benefits can the proposed decision-support approach provide under the evaluation assumptions?

## Data

The analysis uses electricity-market data from the **ENTSO-E Transparency Platform**, covering the study period **2022–2024**.

| Dataset | Purpose |
|---|---|
| German day-ahead electricity prices | Forecasting target and historical price features |
| Electricity load | Analysis of demand-related price patterns |
| Solar generation | Analysis of renewable supply conditions |
| Wind generation | Analysis of renewable supply conditions |
| Calendar variables | Representation of recurring temporal patterns |

Data preprocessing includes timestamp alignment, timezone handling, missing-value checks, and aggregation of higher-frequency observations to hourly resolution.

## Methodology

### 1. Exploratory Data Analysis

The analysis examines:

- Price distributions, volatility, and negative-price observations.
- Hourly, weekly, and monthly price patterns.
- Relationships between electricity prices, load, and renewable generation.
- Correlations between candidate forecasting features.

### 2. Feature Engineering

The feature set includes:

- **Temporal features:** hour, day of the week, month, weekends, and holidays.
- **Lagged features:** historical prices, load, solar generation, and wind generation.
- **Rolling statistics:** moving averages and measures of recent price variability.

### 3. Forecasting Models

The modelling workflow compares benchmark approaches with regression and tree-based models:

- Naive forecast.
- Moving-average forecast.
- Linear and regularized regression.
- Random Forest.
- XGBoost.

A chronological split separates model development and evaluation:

| Split | Period |
|---|---|
| Training | 2022–2023 |
| Testing | 2024 |

Forecasting performance is assessed using **MAE**, **RMSE**, and **MAPE**. MAPE requires caution because electricity prices can be zero, close to zero, or negative.

### 4. Decision Support

A rule-based decision layer translates predicted prices into simplified bid/no-bid signals. These signals are evaluated against benchmark strategies to investigate whether forecasting improvements translate into economic value.

The economic evaluation represents a simplified simulation, with outcomes dependent on the strategy rules and market assumptions.

## Workflow

1. Data acquisition.
2. Preprocessing and hourly alignment.
3. Feature engineering.
4. Dataset merging.
5. Exploratory data analysis.
6. Model training and evaluation.
7. Decision-support simulation and visualization.

## Technology Stack

**Python**, pandas, NumPy, scikit-learn, XGBoost, Matplotlib, Seaborn, Jupyter Notebook, and Streamlit.

ENTSO-E data retrieval uses the `entsoe-py` package.

## Reproducibility and Interpretation

Run the analysis in the workflow order above, configuring local data paths and your own ENTSO-E API token where required. API credentials should remain outside version control.

For a realistic day-ahead evaluation, every input must be available at the forecast issuance time. Realized load and generation values, as well as recent price lags and rolling statistics, require careful alignment with that information cutoff. Experiments using inputs unavailable at that time should be interpreted as retrospective analysis.

## Author

**Sher Razi**  
M.Sc. Data Science

Developed as part of the thesis:

*AI-Based Decision-Support System for Day-Ahead Electricity-Price Forecasting in the German Power Market.*

# steo-style-oil-price-model
An STEO(Short Term Energy Outlook) style weekly WTI forecasting model using oil market fundamentals, term structure and inventory data. 

# STEO-Style Oil Model

A weekly WTI forecasting model inspired by the U.S. EIA's STEO framework.  
This project combines oil market fundamentals, curve structure, and inventory data to generate short-term directional forecasts for WTI crude.

## Project Objective

The goal of this project is to build a transparent, economically interpretable forecasting framework for WTI prices using weekly data.  
Rather than relying on black-box prediction, the model emphasizes market structure, supply-demand signals, and out-of-sample validation.

## Key Features

- Weekly WTI spot price forecasting
- Feature engineering using:
  - Spot-CL1 structure
  - Brent-WTI structure shifts
  - Cushing inventory changes
- SARIMAX mean model
- Walk-forward validation
- Monte Carlo scenario engine for bear/base/bull cases
- GARCH-based volatility and confidence band framework

## Data Sources

- U.S. Energy Information Administration (EIA)
- Yahoo Finance / futures pricing
- CFTC positioning data
- Additional market data inputs where relevant

## Methodology

The base forecasting framework uses a SARIMAX mean model with exogenous oil market features:

- Spot-Cl1_lag1
- BZ1_CL1_change_lag4
- Chng_CushingStocks_lag1

Model performance is evaluated using:
- Chronological train/test split
- Walk-forward validation
- RMSE
- MAE
- Directional accuracy

## Results

Example out-of-sample performance:

- Walk-forward RMSE: ~3.21
- MAE: ~2.13
- Directional accuracy: ~60.9%

These results suggest that oil curve structure and inventory changes provide predictive value at the weekly horizon.

## Repository Structure

steo-style-oil-model/
│
├── README.md
├── requirements.txt
├── .gitignore
├── LICENSE
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_pull_and_cleaning.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_model_estimation.ipynb
│   ├── 04_walk_forward_validation.ipynb
│   └── 05_scenario_analysis_and_confidence_bands.ipynb
│
├── src/
│   ├── data_loader.py
│   ├── feature_engineering.py
│   ├── modeling.py
│   ├── validation.py
│   └── scenario_engine.py
│
├── outputs/
│   ├── charts/
│   ├── tables/
│   └── forecasts/
│
└── docs/
    └── methodology.md

## Example Outputs

**Include a few charts here:
- Actual vs predicted weekly WTI changes
- Forecast fan chart / confidence bands
- Scenario paths for bear/base/bull cases**

## Next Steps

- Expand toward pooled/ensemble STEO-style architecture
- Add macro and refined product features
- Compare weekly vs monthly forecasting setups
- Integrate regime-dependent feature assumptions

## Disclaimer

This project is for research and educational purposes only and does not constitute investment advice.

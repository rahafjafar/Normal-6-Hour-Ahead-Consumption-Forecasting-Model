# 6-Hour Water Consumption Forecasting Model

## Overview
This project extends the 3-hour forecasting approach to predict total household water consumption over the next six hours (t+1 to t+6).

The extended forecasting horizon provides additional time for households and water management operators to anticipate consumption and make informed decisions.

## Methodology

### 1. Data Preparation
- Used the cleaned Jordanian water consumption dataset.
- Constructed the target variable as the sum of the next six hourly consumption readings.
- Included only normal consumption periods in model training.
- Prevented data leakage by keeping future readings exclusively for target construction.

### 2. Feature Engineering
The model builds on the feature engineering approach used in the 3-hour model, including:
- Cyclic time features.
- Weekly refill-cycle features based on a 168-hour cycle.
- Historical lag features.
- Rolling statistical features.

Additionally, three momentum features were introduced:
- 6-hour rolling consumption sum.
- 12-hour rolling consumption sum.
- 24-hour rolling consumption sum.

These features help capture recent consumption trends and short-term increases in water usage.

### 3. Model Optimization
The HistGradientBoostingRegressor architecture was used, with hyperparameter optimization through:
1. L2 Regularization Search.
2. Manual Random Search.
3. Quantum-behaved Particle Swarm Optimization (QPSO).

The selected configuration was **HGB_manual_2**.

### 4. Evaluation
The dataset was divided chronologically:
- 60% Training
- 20% Validation
- 20% Testing

Performance was measured using MAE, RMSE, SMAPE, and R².

## Final Results

| Metric | Test Result |
|---|---:|
| MAE | 19.70 |
| RMSE | 26.89 |
| SMAPE | 9.32% |
| R² | 0.9401 |

**Selected Model:** HGB_manual_2

## Saved Artifacts
- `normal_6h_consumption_forecasting_model.pkl`
- `normal_6h_forecasting_validation_results.csv`
- `normal_6h_forecasting_feature_importance.csv`
- `normal_6h_forecasting_final_metrics.csv`
- `master_dataset_with_expected_next_6h_normal_consumption.csv`

## Technologies
Python, Pandas, NumPy, Scikit-learn, Matplotlib, Joblib.

## Purpose
The model provides medium-term water consumption forecasts and supplies expected consumption values to downstream modules, including anomaly detection and the smart water recommendation system.

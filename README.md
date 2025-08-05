# ETF Tracking Difference Forecasting

This repository contains code for forecasting monthly **ETF tracking differences** using a progressive modelling framework. The goal is to improve predictive accuracy through successive model enhancements, from classical time-series methods to advanced machine learning and hybrid approaches.

## 📌 Project Overview
Tracking difference measures the deviation between an ETF’s return and its benchmark index. Anticipating these deviations enables more informed portfolio allocation and risk management decisions.  
This project develops and evaluates five forecasting models using **expanding-window cross-validation**:

1. **SARIMA–GARCH**  
   - Seasonal ARIMA with GARCH(1,1) variance modelling.
2. **MS-VIX-SARIMA**  
   - Markov-switching SARIMA, with regimes inferred from the VIX index to capture volatility-dependent behaviour.
3. **XGBoost**  
   - Gradient Boosted Decision Trees with engineered lag features and ETF-level static attributes.
4. **Hybrid: SARIMA–GARCH + XGBoost**  
   - Combines SARIMA forecasts as features in XGBoost to model non-linear residual patterns.
5. **Hybrid: MS-VIX-SARIMA + XGBoost**  
   - Extends the above hybrid with volatility-regime forecasts.

## ⚙️ Methodology
- **Data**: Monthly ETF prices, returns, macro indicators (including VIX), and ETF fundamentals.  
- **Preprocessing**:  
  - Outlier winsorization and Yeo–Johnson transformation.  
  - Feature engineering with multiple lags and categorical encoding.  
- **Validation**:  
  - Initial window: 60 months, expanding by 30 months each fold.  
  - Horizon: 3-month ahead forecasts.  
  - Metrics: Mean Absolute Error (MAE), Mean Squared Error (MSE), R².  
  - Model comparison: Diebold–Mariano test.  
- **Visualization**: Time series plots, volatility regime shading, feature importance (gain), SHAP values.

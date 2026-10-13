# 🛺 Auto Surge: Autorickshaw Fare Surge Prediction

Predicts a **surge multiplier (1.0x to 3.0x)** for autorickshaw fares from weather, traffic, demand and event signals, and explains each prediction with SHAP.

Course project: 21CSC305P Machine Learning, Review 1 (Cab Surge Price Prediction using Regression-Based ML).

## Features
- Live predictor with sliders and presets (rainy rush hour, festival night, ...)
- Fare estimate: base fare = Rs 30 for the first 1.5 km + Rs 15/km, then multiplied by the surge
- SHAP chart: exact Shapley contributions of each feature to the prediction
- 24-hour surge curve for the chosen conditions
- Model tab: R2, MAE, RMSE, actual vs predicted, feature importance (gain and mean |SHAP|)

## Model
- Gradient-boosted regression trees (XGBoost-style, squared error): 140 trees, depth 3, learning rate 0.12
- Trains in the browser on page load (no backend, no dependencies)
- 8 features: hour, weekend, rain, temperature, traffic index, search-trend demand, event, city tier

## Data (important)
No public autorickshaw pricing dataset exists, so the app trains on **4,000 simulated rides** generated from hand-written rules. Metrics show the model can learn those rules, not real-world accuracy. Next step: replace the simulator with real weather (Open-Meteo), traffic (TomTom/Google), demand (Google Trends) and event data, plus real fares as labels.

## Run
Open `index.html` in any browser.

## Deploy
GitHub repo > Settings > Pages > Deploy from branch `main` / root.

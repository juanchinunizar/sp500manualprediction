# S&P 500 Price Change Forecasting with Random Forest in R

This repository documents an iterative project to build a robust model for forecasting the monthly price movements of the S&P 500.

The primary goal is to demonstrate a rigorous modeling process, identifying common pitfalls in time-series forecasting and implementing solutions to overcome them.

## Project Journey & Methodology
This analysis evolved through three stages:

1. Initial Attempt (Failure): A direct prediction of the absolute Real.Price. This approach failed, as tree-based models (like Random Forest) are fundamentally unable to extrapolate values outside the range of their training data (i.e., they cannot predict new all-time-highs).

2. Second Attempt (Failure): Predicting the percentage change and then accumulating those changes. This model also failed, suffering from compounding error (or "prediction drift"), where small prediction errors accumulate over time, causing the forecast to deviate dramatically from reality.

3. Final Model (Success): The successful and final model (modelo3.R) solves these problems by:

Predicting the monthly percentage change (Price_Change).

Applying feature engineering (using price lags and moving averages) to provide the model with essential historical context (momentum and trend).

Using a "one-step-ahead" prediction method, which bases each new forecast on the actual data from the previous month. This prevents the compounding error seen in the second attempt.

## Key Outcome
The final model successfully tracks the real-world data and achieves approximately 66.5% directional accuracy on the test set (i.e., it correctly predicts whether the market will move up or down in a given month).

For a detailed breakdown, please see the fully-commented R script (modelo3.R), which includes the feature engineering process, model training, and diagnostic analysis (such as feature importance and residuals).

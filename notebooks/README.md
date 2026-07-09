dataset
Historical market data was collected using the Yahoo Finance (yfinance) Python library.

Task 1 – Data Preprocessing and Exploratory Data Analysis

Objective

Prepare clean financial data suitable for forecasting and portfolio optimization.

Completed Work

Data Collection

- Downloaded historical data from Yahoo Finance using `yfinance`
- Stored datasets for TSLA, SPY, and BND

Data Cleaning

- Checked missing values
- Removed missing observations where necessary
- Verified data types
- Flattened MultiIndex columns before saving CSV files
- Saved cleaned datasets into the `data/processed` directory

Exploratory Data Analysis

Performed several analyses including:

- Closing price trends
- Daily return calculations
- Rolling mean
- Rolling volatility
- Outlier detection

Stationarity Analysis

Performed the Augmented Dickey-Fuller (ADF) test on:

- Closing prices
- Daily returns

The results were used to determine whether differencing would be required before fitting ARIMA models.

Risk Metrics

Calculated:

- Historical Value at Risk (95% VaR)
- Historical Sharpe Ratio

These metrics provide insight into downside risk and risk-adjusted returns.

Task 2 – Time Series Forecasting

Objective

Develop forecasting models to predict Tesla stock prices and compare statistical and deep learning approaches.

Completed Work

Data Preparation

- Loaded cleaned TSLA dataset
- Selected closing prices for forecasting
- Chronologically split data into:

| Dataset  | Period    |
| -------- | --------- |
| Training | 2015–2024 |
| Testing  | 2025–2026 |

Forecasting Models

The project implements:

- ARIMA
- LSTM Neural Network

  task 3 Forecast Future Market Trends

  The LSTM model was selected because it achieved substantially lower MAE, RMSE, and MAPE than ARIMA. Since a standard LSTM provides point forecasts rather than prediction intervals, the analysis focuses on the forecasted trend. Confidence intervals are a limitation of the standard LSTM implementation.

The model predicts that prices will remain close to the recent trading range, suggesting no significant acceleration or decline during the forecast horizon. This may indicate a period of market consolidation following the higher volatility observed in previous years.

forcast realibilty
The LSTM model provides point forecasts but does not directly estimate confidence intervals. Therefore, uncertainty cannot be visualized using prediction bands as with ARIMA models. Short-term forecasts are generally more reliable than long-term forecasts because uncertainty accumulates as each predicted value is used to generate future predictions. Consequently, the six-month forecast should be interpreted with caution and used alongside broader financial analysis.

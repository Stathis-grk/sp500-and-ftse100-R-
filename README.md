# Project Overview
This project analyzes the monthly returns of two major stock market indices:

S&P500: Represents the performance of 500 large companies listed on US stock exchanges (NYSE and NASDAQ).

FTSE100: Represents the 100 largest companies listed on the London Stock Exchange (LSE).

The analysis includes visualizations, time series modeling, Granger causality tests, and cointegration analysis.

## Analysis
Time Series Visualization
Converted the series to logarithms (lsp for S&P500, lftse for FTSE100) and plotted their trends.

Observations:

Both indices show similar trends with occasional declines (some sharp) due to economic downturns (e.g., 2008 financial crisis, COVID-19 in 2020).

lsp exhibits stronger growth compared to lftse, likely due to the US market's broader economic expansion (e.g., technology sector).
Converted the series to logarithmic returns (rsp and rftse).

![image](https://github.com/user-attachments/assets/45f92f74-3633-4141-9285-c1cc001ac134)

## AR and ARMA Models for S&P500 Returns (rsp)
Estimated two models using all data except the last 12 months:

AR(2): AIC = -679.5371

ARMA(3,1): AIC = -675.5371

Conclusion: The AR(2) model provides better in-sample fit due to its lower AIC value.
![image](https://github.com/user-attachments/assets/9b90611c-fffe-4350-846e-5f7b40c59d17)

## Automated Model Selection with auto.arima
Used auto.arima (with up to 15 lags and stepwise=FALSE) to find the best model.

Best Model: ARIMA(0,0,0) (white noise), with AIC = -683.54.

This model outperforms the AR(2) and ARMA(3,1) models.
![image](https://github.com/user-attachments/assets/95f39076-8137-4f60-b0c5-e549cc9e7c39)

## Granger Causality Test (VAR Model)
Tested for Granger causality between rsp (S&P500) and rftse (FTSE100).

Results:

No Granger causality exists between the two indices (high p-values: 0.478 for rftse → rsp, 0.9521 for rsp → rftse).
![image](https://github.com/user-attachments/assets/9e1ab84d-e86f-498c-9cc2-8ce583b593da)

## Unit Root Testing (Augmented Dickey-Fuller Test)
Tested whether lsp and lftse are I(1) processes (non-stationary in levels but stationary in first differences).

Results:

Levels: Non-stationary (t > critical value at 5% significance).

First differences: Stationary (t < critical value).

Conclusion: Both series are best characterized as I(1) processes.
![image](https://github.com/user-attachments/assets/c31fa568-7ba8-4de3-9c4f-8b06f2a6a9a0)
![image](https://github.com/user-attachments/assets/2e599f0d-3ac4-4db0-93e5-7ea54ed7e3a9)
  With Differences:
![image](https://github.com/user-attachments/assets/31bf53ff-a4b6-4642-9815-12ad875e5b48)
![image](https://github.com/user-attachments/assets/a7598e08-d7b1-40b9-9567-e16df3bad17b)

## Cointegration Test (Engle-Granger)
Tested for a cointegrating relationship between lsp and lftse.

Results:

No cointegration exists (t-statistic = -2.4932 > critical value of -3.37 at 5% significance).
![image](https://github.com/user-attachments/assets/964231cc-af0a-4876-92c7-c93a67239f43)
![image](https://github.com/user-attachments/assets/e2ddcc08-54fa-4b52-a936-0baac930a693)

# Key Findings
Both indices exhibit similar trends but with stronger growth in the S&P500.

The best model for S&P500 returns is ARIMA(0,0,0) (white noise).

No Granger causality exists between S&P500 and FTSE100 returns.

Both indices are I(1) processes but not cointegrated.





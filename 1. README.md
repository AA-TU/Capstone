# Capstone

Project Overview

The efficient market hypothesis and high degree of noise has historically made predicting price and trends in financial markets a notoriously difficult task. Activity in the stock market has seen record volumes globally and is a major area of business for investors of all types, from the every day individual to established institutions. The market is a liquidity enabler for investors to meet various goals such as aiding in financing capital costs, hedging risk, investment costs, and speculation.

The area of interest will be exploring the operations of the US Treasury and Fed and its effect on systemic liquidity. Systemic liquidity can be defined as the aggregate of public, insured and private money aka the flow of capital and credit within the global financial system. The focus will be dissecting the change rate of these flows and their inherent lag on impacting risk asset prices. 

The proposed solution is to develop machine learning models for estimating liquidity to predict the future value of the 10-year US treasury bond. The 10 year is one of the most liquid instruments in the world and is widely used as the global debt benchmark. It is a key input in calculating financing costs across various assets.

The goal is to implement Regression Analysis, Decision Trees, LSTM, and CNN.

Datasets:

The dependent variable will be the price of the US 10 Year treasury bond. Independent variables are components that make up private and public systemic liquidity. 

- 10 Year Rates: https://fred.stlouisfed.org/series/DGS10
- Bank Reserves, Fed Balance Sheet, Loans: https://www.federalreserve.gov/releases/h41/
- Treasury Operating Cash Balance: https://fiscal.treasury.gov/reports-statements/dts/
- Treasury General Account: https://fred.stlouisfed.org/series/WTREGEN
- Overnight Reverse Repurchase Agreements: https://fred.stlouisfed.org/series/RRPONTSYD
- Deposits, All Commercial Banks: https://fred.stlouisfed.org/series/DPSACBW027SBOG


When working with a time-series, it is crucial to perform Exploraty Data Analysis to ensure the data is sufficient for modeling. Treasury products are actively traded, producing sequenced, timestamped data with a finite 'closing' print daily. There are days during the business week where markets will be closed for trading due to holidays, exchange issues, etc., thus showing a NaN value. Handling missing values is key during data pre-processing, especially for time-series data as it can disrupt the time order dependence aspect of the model, which may skew assumptions.

![NaN](https://github.com/AA-TU/Capstone/assets/114870779/6b151ebb-1675-48ba-9a0d-bdbb25c9c6c8)


The base model will be an ARIMA model. ARIMA makes use of lagged moving averages to smooth time series data and focuses on historical data to predict future values. They are widely used in technical analysis to forecast future security prices. We will perform univariate analysis with the DGS10 dataset. 
![10-Year Rates](https://github.com/AA-TU/Capstone/assets/114870779/0bc29253-6c78-46f8-ba89-9436cb91d0c4)

Conversion from non-stationary to stationary time-series is required for parameter tuning. This is achieved with the differencing function to caluclate the difference between consecutive observations. The idea is to remove any trend or seasonanlity baked into the dataset to then use for modeling. The Augmented Dickey Fuller test is used to confirm the conversion to a stationary time-series. 
The next step is to use the differenced values as an input to identify optimal order lags of the AR and MA components. 

Source: https://people.duke.edu/~rnau/411arim3.htm

ACF and PACF plots: 

![ACF](https://github.com/AA-TU/Capstone/assets/114870779/2af01b9f-5ea0-4d8d-abf1-dd38801fb1c6) ![PACF](https://github.com/AA-TU/Capstone/assets/114870779/78f544ec-41aa-4716-8273-ce4b5c8324eb)

Checking the distribution of residuals helps validate normality of the differences. We can see that the plot follows a relatively normal distriubtion after first order differencing, thus we can move forward with the validation process.

![residual check](https://github.com/AA-TU/Capstone/assets/114870779/7806c3df-4607-4e5b-a96f-8fe7b6312851)

The evaluation metric to be used is the Root Mean Squared Error. This is chosen because it measures the average magnitude of errors between predicted and observed errors, squaring the differences so there's larger weights to the errors. 
Base model has RMSE output of 0.08549. On average, there is an error of 0.08549 units when comparing prediction against actual values. We will use this as the benchmark for advanced modelling techniques in the next section.

![model output](https://github.com/AA-TU/Capstone/assets/114870779/949d0ce3-802a-43d3-b1aa-f42a64c00e7e)

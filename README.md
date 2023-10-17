# Capstone

Project Overview

The efficient market hypothesis and high degree of noise has historically made predicting price and trends in financial markets a notoriously difficult task. Activity in the stock market has seen record volumes globally and is a major area of business for investors of all types, from the every day individual to established institutions. The market is a liquidity enabler for investors to meet various goals such as aiding in financing capital costs, hedging risk, investment costs, and speculation.

The area of interest will be exploring the operations of the US Treasury and Fed and its effect on systemic liquidity. Systemic liquidity can be defined as the aggregate of public, insured and private money aka the flow of capital and credit within the global financial system. The focus will be dissecting the change rate of these flows and their inherent lag on impacting risk asset prices. 

The proposed solution is to develop machine learning models for estimating liquidity to predict the future value of the 10-year US treasury bond. The 10 year is one of the most liquid instruments in the world and is widely used as the global debt benchmark. It is a key input in calculating financing costs across various assets.

Regression Analysis, Decision Trees, Random Forest.

Datasets:

The dependent variable will be the price of the US 10 Year treasury bond. Independent variables are components that make up private and public systemic liquidity. 

10 Year US bond: Ticker 'IEF' as the ETF proxy.

Money and credit via private liquidity 
- Consumer credit https://fred.stlouisfed.org/series/TOTALSL
- M0 https://fred.stlouisfed.org/series/BOGMBASE
- M1 https://fred.stlouisfed.org/series/M1SL
- M2 https://fred.stlouisfed.org/series/WM2NS
- M3 https://fred.stlouisfed.org/series/MABMM301USM189S
- Credit: https://fred.stlouisfed.org/series/FDHBPIN

Money and credit between public entities: 
- Bank credit, all commercial banks https://fred.stlouisfed.org/series/TOTBKCR
- Dollars in circulation, domestic https://fred.stlouisfed.org/series/CURRCIR
- Deposits, all commercial banks https://fred.stlouisfed.org/series/DPSACBW027SBOG
- Fed Funds Rate https://fred.stlouisfed.org/series/EFFR 

Fed/US Treasury:
- Reverse repo https://fred.stlouisfed.org/series/RRPONTSYD
- Treasury General Account https://fred.stlouisfed.org/series/WTREGEN
- System Open Market Account https://fiscaldata.treasury.gov/datasets/daily-treasury-statement/operating-cash-balance

# Stock Price Backtesting Strategy: LSTM + Bollinger Bands + RSI

This project implements a stock trading strategy that combines **technical indicators** (Bollinger Bands and RSI) with a **deep learning model (LSTM)** to generate buy/sell/hold signals. The strategy is designed for backtesting across multiple assets and time periods to evaluate performance.

## Table of Contents

- [Overview](#overview)  
- [How It Works](#how-it-works)  
- [Approach](#approach)  
- [Run on Google Colab](#run-on-google-colab)  
- [Performance Summary](#performance-summary)  
- [Limitations and Future Work](#limitations-and-future-work)  
- [Asset Coverage](#asset-coverage)

## Overview

The goal of this project is to simulate a signal-driven stock trading strategy that uses both technical analysis and machine learning to identify potential long opportunities in financial markets.

Originally, a **Random Forest classifier** was used to predict price movement direction based on engineered features. After observing limited generalization, the project shifted toward a deep learning approach using an LSTM model trained on historical stock prices.

## How It Works
- Backtesting is done using the `zipline` library.
- A full performance report is automatically generated using `quantstats`.

## Approach

- **Signal Logic**:  
  - **Buy**: LSTM predicts price increase, price is below lower Bollinger Band, and RSI indicates oversold  
  - **Sell**: LSTM predicts price decrease, price is above upper Bollinger Band, and RSI indicates overbought  
  - **Hold**: All other conditions

- **Modeling**:  
  - LSTM uses 50-day historical windows to predict the next day's price  
  - Trained on S&P 500 data (2013–2020), tested on 2023–2024  
  - Compared against MACD, RSI, Bollinger Bands individually before combining

- **Trading Strategy**:  
  - Focuses on long-only trades  
  - Assumes a bullish market

## Run on Google Colab

To run the project without local setup:

1. Open the [Google Colab Notebook](https://colab.research.google.com/drive/1AbwW1OT2dvgDomi6sNQQWjJsqviQfofM?usp=sharing)
2. Upload the required files (as indicated in the notebook)
3. Click **"Run All"** to start the strategy and view results

## Performance Summary

- Validated across 50 stocks from 10 sectors between 2018 and 2022  
- Outperformed standalone technical or ML-based strategies  
- Demonstrated improved generalization on out-of-sample test sets
<img width="1197" height="583" alt="image" src="https://github.com/user-attachments/assets/9c2c7f96-14a1-47a1-baf6-cdf5d691278e" />
<img width="419" height="677" alt="image" src="https://github.com/user-attachments/assets/7901bb9c-b89d-494a-93c2-98945ac638f9" />


## Limitations and Future Work

- Long-only strategy; limited in sideways or bear markets  
- LSTM performance may degrade in volatile regimes  
- Potential improvements:
  - Add short-selling capabilities  
  - Use dynamic signal thresholds  
  - Explore transformer-based or hybrid models

## Asset Coverage

Backtests were conducted on 50 S&P 500 stocks representing a range of sectors, including:

- Technology  
- Finance  
- Healthcare  
- Energy  
- Consumer Goods  
- Industrials  
- Utilities  
- Real Estate  
- Communication Services  
- Materials

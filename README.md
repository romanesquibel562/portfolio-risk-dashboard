# Portfolio Risk Dashboard

## Overview

This project presents a professional-grade Portfolio Risk Dashboard built using Python, SQL (PostgreSQL), and Tableau. It simulates a real-world financial risk management workflow used by investment banks, hedge funds, and asset managers. The pipeline measures, analyzes, and visualizes key risk metrics for a five-asset equity portfolio.

## Purpose

To showcase end-to-end data analysis, ETL pipeline design, and risk visualization capabilities using industry-relevant risk metrics. The goal is to replicate the work of quantitative analysts and risk managers, making this portfolio an ideal demonstration of technical and financial fluency for data analyst, financial analyst, or quant roles.

## Data Sources

- Financial data: Collected using the Yahoo Finance API via the `yfinance` Python package.
- Assets analyzed: A user-defined set of 5 tickers (e.g., AAPL, JNJ, MSFT, NVDA, TSLA).
- Date range: Historical data from 2020-01-01 to 2024-12-31; rolling metrics use the last 30 days.

## Technology Stack

- Python: Data collection, processing, metric calculations, ETL pipeline
- PostgreSQL: Risk metrics exported to structured tables for persistence and Tableau connection
- Tableau: Visualization and dashboard creation
- Libraries used: pandas, numpy, yfinance, scipy, sqlalchemy, python-dotenv, logging

## Risk Metrics Calculated

### Portfolio and Asset-Level Metrics

- Sharpe Ratio: Measures return per unit of risk, annualized
- Value at Risk (VaR):
  - Historical VaR (1-Day, 95%): Empirical loss threshold
  - Parametric VaR (1-Day, 95%): Assuming normal distribution
- Rolling Volatility: 20-day rolling standard deviation, annualized
- Maximum Drawdown: Largest peak-to-trough drop for each asset
- Optimal Portfolio Weights: Calculated using Minimum Variance Optimization

## Code Structure

### risk_pipeline.py

- Accepts 5 user-defined tickers
- Downloads historical price data from Yahoo Finance
- Calculates all risk metrics
- Builds and exports a summary DataFrame to PostgreSQL
- Writes to table: `risk_metrics`

### rolling_risk_metrics.py

- Fetches most recent 30 days of data
- Calculates rolling Sharpe Ratio and Parametric VaR
- Appends to table: `rolling_risk_metrics`
- Simulates past 7 days for dashboard visualization

## PostgreSQL ETL

- Data is stored in two relational tables:
  - `risk_metrics`
  - `rolling_risk_metrics`
- Environment credentials are secured using `.env` and `python-dotenv`
- The ETL pipeline verifies credentials and logs success/failure

## Tableau Dashboard Visuals

- Sharpe Ratio Over Time by Ticker
  - Includes raw Sharpe and 3-day moving average
  - Interactive ticker and date range filter

    ![image](https://github.com/user-attachments/assets/b7020a05-b3a6-436a-83d3-a535a36f9ba3)


- 1-Day Parametric VaR Over Time by Ticker
  - Shows downside risk evolution
  - Highlights worst-case VaR points
  - (shows lack of movement, which can translate to stable prices)
 
    ![image](https://github.com/user-attachments/assets/2504a07e-3b7e-4514-a4e0-0bf64a1b6f20)


- Pie Chart: Portfolio Allocation by Optimal Weights:

    ![image](https://github.com/user-attachments/assets/348730e5-7e69-478f-b06d-3a35fa98f908)


- Bar Chart: Maximum Drawdown by Ticker

- KPI Table: Summary of Sharpe, VaR, Drawdown, Rolling Volatility

## Parameter Design

- Alpha for VaR: 0.05 (95% confidence)
- Rolling window: 20 trading days
- Sharpe annualization: 252 trading days
- Risk-free rate: 3% annually (daily rate used in calculation)

## Key Findings (Sample Output)

- Portfolio Weights: JNJ holds ~80% due to low volatility and diversification
- Portfolio Return: 9.82% annually
- Portfolio Volatility: 18.79%
- Highest Drawdowns: TSLA and NVDA exceed 60%
- Most Efficient Asset: NVDA has highest Sharpe but also highest volatility

## Project Highlights

- Rolling metrics simulate live updates for VaR and Sharpe
- Interactive Tableau dashboard for real-time risk exploration
- Modular, well-logged, and secure ETL system

## How to Upload Code to GitHub

### Folder vs Files

- Upload the entire project folder (recommended)
- Include:
  - `risk_pipeline.py`
  - `rolling_risk_metrics.py`
  - `.env.example`
  - `README.md`
  - Tableau workbook `.twb` (optional)

### Add a `.gitignore` file to exclude:

### Include `.env.example` instead of `.env`:


## Conclusion

This project replicates core risk management functions used by financial institutions. It demonstrates:

- Quantitative analysis and portfolio construction
- Database pipeline architecture
- Dashboard creation and communication of complex risk concepts

The structure, metrics, and insights make this project ideal for demonstrating readiness for roles in finance, risk, or data analytics.

## Author

**Roman Esquibel**  
BS in Economics, MS in Data Analytics  
LinkedIn: https://www.linkedin.com/in/roman-esquibel-75b994223/
Email: romanesquib@gmail.com 
Location: California, United States




# Multi-Asset ETF Portfolio Strategy Analysis

This project analyzes the performance of a diversified portfolio of exchange-traded funds (ETFs) representing major global asset classes. The goal of the analysis is to understand how portfolio allocation decisions influence risk and return over time.

Rather than investing in a single asset class, investors often build portfolios that combine equities, bonds, real estate, and commodities. Diversification allows investors to reduce risk while still achieving attractive long-term returns.

In this project, historical ETF price data is used to simulate thousands of potential portfolios. The analysis evaluates how different asset weightings affect portfolio performance and identifies the portfolio with the strongest risk-adjusted return.

The analysis is implemented in Python using financial data from Yahoo Finance.

---

# Assets Analyzed

The portfolio includes ETFs representing several major segments of the global financial market.

• **SPY** — S&P 500 (U.S. large-cap equities)  
• **QQQ** — Nasdaq 100 (technology-heavy U.S. equities)  
• **VTI** — Total U.S. stock market  
• **EFA** — International developed market equities  
• **VNQ** — U.S. real estate investment trusts (REITs)  
• **TLT** — Long-term U.S. Treasury bonds  

Each ETF represents a different asset class, allowing us to study the effects of diversification within a multi-asset portfolio.

---

# Methodology

The analysis follows a portfolio construction pipeline commonly used in quantitative finance and portfolio management.

### 1. Data Collection

Historical ETF price data is downloaded directly from Yahoo Finance using the `yfinance` Python library.

Adjusted closing prices are used to ensure that dividends and stock splits are properly accounted for.

Example code:

```python
import yfinance as yf

tickers = ["SPY", "QQQ", "VTI", "EFA", "VNQ", "TLT"]

prices = yf.download(tickers, start="2015-01-01")["Adj Close"]
2. Return Calculation

Daily returns are calculated from the historical price data.

Returns are used instead of prices because they allow us to compare assets on the same scale and measure portfolio performance.

Example code:

returns = prices.pct_change().dropna()
3. Correlation Analysis

A correlation matrix is calculated to understand how assets move relative to each other.

Assets with lower correlation provide stronger diversification benefits.

Example code:

corr_matrix = returns.corr()
4. Portfolio Simulation

The project uses Monte Carlo simulation to generate thousands of random portfolio allocations.

Each simulated portfolio assigns random weights to each asset while ensuring the weights sum to 1.

For every portfolio we calculate:

• Expected return
• Portfolio volatility
• Sharpe ratio

Example simulation logic:

import numpy as np

num_portfolios = 10000
weights = np.random.random(len(tickers))
weights /= np.sum(weights)

This process is repeated thousands of times to explore the full range of possible portfolio allocations.

5. Portfolio Optimization

After simulating thousands of portfolios, we identify the portfolio with the highest Sharpe ratio, which represents the strongest risk-adjusted return.

The Sharpe ratio measures how much return an investor receives for each unit of risk taken.

Formula:

Sharpe Ratio = (Portfolio Return − Risk-Free Rate) / Portfolio Volatility

Key Visualizations

Several visualizations are created to help interpret the results.

Growth of $1 Invested

This chart shows how $1 invested in the portfolio would have grown over time.

Risk vs Return

Each point represents a simulated portfolio.

The optimal portfolio lies on the efficient frontier where expected return is highest for a given level of risk.

Correlation Matrix

The correlation heatmap shows how strongly each asset moves relative to the others.

Lower correlations improve diversification benefits.

Portfolio Simulation

This chart visualizes thousands of randomly generated portfolios and highlights the optimal allocation.

Optimal Portfolio Allocation

The optimal portfolio weights show how capital should be distributed across the ETFs to maximize the Sharpe ratio.

Tools Used

The project was implemented using the following tools and libraries:

• Python — core programming language
• Pandas — data manipulation and time series analysis
• NumPy — numerical computation
• Matplotlib — financial visualizations
• Seaborn — correlation heatmaps
• yfinance — historical financial market data

Development environment:

• Visual Studio Code
• Jupyter Notebook

Version control:

• Git
• GitHub

Key Concepts Demonstrated

This project demonstrates several concepts commonly used in quantitative finance and investment analysis.

• Portfolio diversification
• Risk-return tradeoff
• Sharpe ratio optimization
• Monte Carlo portfolio simulation
• Correlation analysis across asset classes

Notes

The portfolio optimization relies entirely on historical market data and does not incorporate transaction costs, taxes, or forward-looking return assumptions.

As a result, the findings should be interpreted as a demonstration of portfolio construction techniques rather than an investment recommendation.

Project Structure

finance-project-1  
│  
├── data  
├── notebooks  
│   └── portfolio_analysis.ipynb  
├── visualisations  
│   ├── growth_chart.png  
│   ├── risk_return_chart.png  
│   ├── correlation_heatmap.png  
│   ├── portfolio_simulation.png  
│   └── allocation_chart.png  
│  
├── requirements.txt  
└── README.md  

Future Improvements

Possible extensions to this analysis include:

• Adding additional asset classes such as commodities or cryptocurrencies
• Implementing portfolio rebalancing strategies
• Incorporating macroeconomic indicators
• Testing different optimization objectives (minimum volatility, maximum return)
• Using rolling windows to evaluate strategy stability over time


---




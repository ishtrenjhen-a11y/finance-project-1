# Portfolio Optimization with Python

This project analyzes ETF performance and constructs an optimized portfolio using Monte Carlo simulation and Sharpe ratio maximization.

## Assets Analyzed

* **SPY** – S&P 500
* **QQQ** – Nasdaq 100
* **VTI** – Total U.S. Market
* **EFA** – International Developed Markets
* **VNQ** – U.S. Real Estate
* **TLT** – Long-Term U.S. Treasury Bonds

## Methodology

The analysis follows a portfolio construction pipeline:

1. Download historical ETF price data using Yahoo Finance
2. Calculate daily returns
3. Analyze correlations between assets
4. Simulate 10,000 portfolios using random weights
5. Identify the portfolio with the highest Sharpe ratio

## Key Visualizations

### Growth of $1 Invested

![Growth Chart](visualisations/growth_chart.png)

### Risk vs Return

![Risk Return](visualisations/risk_return_chart.png)

### Correlation Matrix

![Correlation Matrix](visualisations/correlation_heatmap.png)

### Portfolio Simulation

![Portfolio Simulation](visualisations/portfolio_simulation.png)

### Optimal Portfolio Allocation

![Allocation](visualisations/allocation_chart.png)

## Tools Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* yfinance

## Notes

The portfolio optimization relies on historical data and does not incorporate constraints, forward-looking expectations, or transaction costs. Results should therefore be interpreted as a demonstration of portfolio optimization techniques rather than an investment recommendation.


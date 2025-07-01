# hrp_optimised
# Portfolio Optimization: Hierarchical Risk Parity (HRP) vs Mean-Variance Optimization (MVO)

## Project Overview

This project compares two prominent portfolio optimization techniques:

- **Mean-Variance Optimization (MVO)** — the classic optimization framework developed by Harry Markowitz.
- **Hierarchical Risk Parity (HRP)** — a modern alternative focused on robustness and risk diversification.

We apply both strategies to a portfolio of four tech and media stocks (AAPL, AMZN, DIS, TSLA) using historical data from 2015 to 2025.



## Data & Tools

- **Assets**: AAPL, AMZN, DIS, TSLA  
- **Date Range**: Jan 2015 – Jan 2025  
- **Data Source**: Yahoo Finance via `yfinance`  
- **Tools**: Python, Pandas, NumPy, Matplotlib  
- **Note**: RiskfolioLib was avoided due to compatibility issues in Colab — HRP was implemented manually.



## Strategy Breakdown

### Mean-Variance Optimization (MVO)

- Based on minimizing portfolio variance for a target return.
- Assumes known expected returns and covariances.
- Sensitive to inputs, but can deliver high returns when forecasts are accurate.

### Hierarchical Risk Parity (HRP)

- Relies on **correlation clustering** and **recursive risk allocation**.
- More robust to estimation errors.
- Emphasizes **risk-balanced** portfolios, not return maximization.

---

## In-Sample Results (2015–2025)
[Dendogram](plot/dendogram.png)

[HRP Cumulative Returns](plot/hrp_cum.png)

[MVO HRP Cumulative Returns](plot/mvo_hrp_cum.png)

[Metric MVO HRP](plot/metrics.png)

| Metric                | MVO        | HRP        |
|-----------------------|------------|------------|
| **Cumulative Return** | 25.65×      | 3.09×       |
| **CAGR**              | 38.95%      | 15.15%      |
| **Annual Volatility** | 31.95%      | 23.67%      |
| **Sharpe Ratio**      | 1.22        | 0.64        |
| **Max Drawdown**      | 65.52%      | 42.61%      |

 MVO dominated in returns, but at the cost of significantly higher drawdowns and volatility.



## Interpretation

Despite the strong performance of MVO in this specific dataset, real-world investors must consider the trade-offs:

### Why HRP Might Be Better in Practice:

- **Stability**: HRP doesn't depend on forecasting expected returns.
- **Diversification**: Built-in clustering prevents overweighting.
- **Robustness**: Performs better under noisy, uncertain conditions.

### Why MVO Looks Better Here:

- The market conditions during this period heavily favored high-growth stocks (e.g., AAPL, TSLA).
- MVO capitalized on return momentum but with **higher risk** exposure.

---

## Portfolio Weights Snapshot
[Weights MVO HRP](plot/weights_mvo_hrp.png)

| Asset | MVO Weight | HRP Weight |
|-------|------------|------------|
| AAPL  | ~41%       | ~50%       |
| AMZN  | ~40%       | 0%         |
| DIS   | 0%         | ~50%       |
| TSLA  | ~20%       | 0%         |

- MVO heavily concentrated in high-return stocks (AAPL, AMZN).
- HRP split risk between uncorrelated clusters — AAPL and DIS.



## Final Takeaway

While MVO appears superior **on paper** for this dataset, it's **more vulnerable** to shocks and misestimations.

 **Conclusion**:  
> “MVO can win battles, but HRP is better for long-term survival in uncertain markets.”



## Files Included

- `hrp_optimised.ipynb` — Implementation notebook   
- `plot/` — Performance and weight visuals  
- `README_hrp_optimised.md` — This file


## ⏭️ What's Next?

See [`README_hrp_Out_of_Sample.md`](README_hrp_Out_of_Sample.md) to evaluate how these models behave on **future (unseen) data**.

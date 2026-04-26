# Spark Spread Mean-Reversion Research
### European Energy Markets | 2021-2026 | Python

## Research Question
> Does spark spread mean-reversion survive a 15x gas price shock?

This project investigates whether the theoretical profit margin of a gas-fired
power plant (the spark spread) reverts to its mean across five distinct European
energy market regimes, including the 2021-2023 gas crisis and the ongoing 2026
Iran conflict.

## Dataset

| Asset | Source | Frequency | Period |
|---|---|---|---|
| German Day-Ahead Power | Ember Climate | Hourly | Jan 2021 - Apr 2026 |
| Dutch TTF Natural Gas | Investing.com / Kaggle | Daily | Jan 2021 - Apr 2026 |
| EU ETS Carbon Credits | Investing.com | Daily | Jan 2021 - Apr 2026 |

46,536 hourly rows. Zero missing values after cleaning.

## Spark Spread Formula
S = P - (G / eta) - (E x C)

Where P = Power price, G = Gas price, eta = Plant efficiency (0.50),
E = Carbon intensity (0.35 t CO2/MWh), C = Carbon price.

## Five Market Regimes

| Regime | Period | Mean Spread | Half-Life | Cointegration |
|---|---|---|---|---|
| A - Pre-Crisis | Jan-Aug 2021 | -7.23 EUR/MWh | 11.8 hrs | Rank 1 |
| B - Crisis | Sep 2021-Dec 2022 | -50.04 EUR/MWh | 14.7 hrs | Rank 1 |
| C - Recovery | Jan-Dec 2023 | -17.39 EUR/MWh | 12.4 hrs | Spurious |
| D - New Normal | Jan 2024-Feb 2026 | -10.41 EUR/MWh | 8.5 hrs | Rank 1 |
| E - Iran Shock | Feb-Apr 2026 | -29.43 EUR/MWh | 8.6 hrs | Rank 2 |

## Statistical Validation

- ADF Test: Mean reversion confirmed in all five regimes (p < 0.05)
- Johansen Cointegration: Rank 1 confirmed in A, B, D. Rank 2 in E (crisis-induced)
- Ornstein-Uhlenbeck Half-Life: 8.5-14.7 hours across regimes
- Parameter Sensitivity: 31 of 36 combinations produce Sharpe above 2.0

## Key Findings

1. Mean reversion survived both the 2022 gas crisis and the 2026 Iran shock
2. Economic anchor (cointegration rank 1) confirmed before, during and after 2022 crisis
3. New Normal (2024-2026) shows fastest reversion at 8.5 hours - more efficient market
4. Iran Shock created first-ever Gas/Carbon cointegration (rank 2) - crisis-induced, not fundamental
5. Returns 6-10x higher in high-volatility periods - vol-scaling is the wrong risk tool
6. Drawdown stop at -300 EUR/MWh achieves Sharpe 4.31 vs 3.77 for vol-scaling

## Strategy Performance

| Regime | Total Return | Sharpe | Max Drawdown | Win Rate |
|---|---|---|---|---|
| A - Pre-Crisis | 951 EUR/MWh | 2.85 | -219 EUR/MWh | 53.8% |
| B - Crisis | 8,053 EUR/MWh | 4.79 | -480 EUR/MWh | 55.2% |
| C - Recovery | 3,657 EUR/MWh | 4.43 | -354 EUR/MWh | 57.1% |
| D - New Normal | 8,593 EUR/MWh | 2.95 | -616 EUR/MWh | 59.1% |
| ALL | 21,254 EUR/MWh | 3.58 | -616 EUR/MWh | 57.0% |

Returns expressed per MWh. Position size scales linearly.

## Notebooks

| Notebook | Contents |
|---|---|
| 01_data_pipeline.ipynb | Data loading, cleaning, merging |
| 02_spread_analysis.ipynb | Spark spread, ADF test, distributions |
| 03_backtester.ipynb | Signal generation, returns, risk metrics |
| 04_risk_report.ipynb | Convexity, cointegration, half-life, risk management |
| 05_extension_2026.ipynb | Extended dataset, Regime D and E analysis |

## How to Run

Clone the repo, install dependencies, download data files, run notebooks in order.

pip install pandas numpy matplotlib statsmodels pyarrow

Data sources listed in each notebook. Download instructions included.

## Honest Caveats

- Returns assume mid-price execution with no delay
- Regime E findings are preliminary - only 55 days of data
- Iran Shock Gas/Carbon cointegration is crisis-induced, not fundamental
- Sharpe ratios computed on hourly returns - daily Sharpe would be lower
- 30-day rolling window may be suboptimal for Regime D given 8.5hr half-life

## Author
George P Babu | April 2026

Built with Python, pandas, statsmodels, matplotlib.
Data: Ember Climate, Investing.com, Kaggle.

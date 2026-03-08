# Portfolio Value at Risk (VaR) Model

## Overview
This project implements a quantitative risk model that estimates the Value at Risk (VaR) 
of a 5-stock equally weighted portfolio using two methodologies — Historical Simulation 
and Parametric VaR.

## Portfolio
| Ticker | Company | Weight |
|--------|---------|--------|
| AAPL | Apple Inc | 20% |
| JPM | JPMorgan Chase | 20% |
| XOM | Exxon Mobil | 20% |
| JNJ | Johnson & Johnson | 20% |
| SPY | S&P 500 ETF | 20% |

## Methodology

### Historical Simulation VaR
Sorts actual historical returns and finds the 5th percentile — no assumptions 
about distribution shape. Captures real market events from 2020-01-01 to 2024-12-31 capturing the COVID crash and 
2022 rate hike selloff.

### Parametric VaR
Assumes returns follow a normal distribution and uses mean and standard deviation 
to mathematically calculate the loss threshold.

## Results
| Method | 95% Daily VaR |
|--------|--------------|
| Historical Simulation | -1.80% |
| Parametric | -2.14% |
| Difference | 0.34% |

## Interpretation
There is a 5% probability that this portfolio loses more than 1.80% of its value 
on any given trading day. The 0.34% gap between methods indicates slight fat tails 
in the return distribution which is consistent with real market stress events captured 
in the 2020-2024 period.

## Tools
- Python
- NumPy
- Pandas
- yfinance
- Matplotlib
- SciPy


## Author
Cynthia Wanjiru | MS Quantitative Finance | Washington University in St Louis

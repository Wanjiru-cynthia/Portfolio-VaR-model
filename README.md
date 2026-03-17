# Portfolio Value at Risk (VaR) Model

## Overview
This project implements a quantitative risk model that estimates the Value at Risk (VaR) 
of a 5-stock equally weighted portfolio using two methodologies, Historical Simulation 
and Parametric VaR.

## Portfolio
| Ticker | Company | Weight |
|--------|---------|--------|
| AAPL | Apple Inc | 20% |
| JPM | JPMorgan Chase | 20% |
| XOM | Exxon Mobil | 20% |
| JNJ | Johnson & Johnson | 20% |
| SPY | S&P 500 | 20% |

## Methodology

### Historical Simulation VaR
Sorts actual historical returns and finds the 5th percentile — no assumptions 
about distribution shape. Captures real market events from 2020-01-01 to 2024-12-31 capturing the COVID crash and 
2022 rate hike selloff.
### Correlation Analysis
Pearson correlation matrix computed across all 5 assets to assess 
diversification quality and understand pairwise return relationships.

### CVaR (Expected Shortfall)
Extends VaR by averaging all losses beyond the 95% threshold — 
capturing tail risk that VaR alone ignores. Implemented using both 
Historical Simulation and Parametric methods.

### Parametric VaR
Assumes returns follow a normal distribution and uses mean and standard deviation 
to mathematically calculate the loss threshold.

## Results
| Method | 95% Daily VaR |
|--------|--------------|
| Historical Simulation | -1.80% |
| Parametric | -2.14% |
| Difference | 0.34% |

### Correlation Matrix Key Findings
| Pair | Correlation | Interpretation |
|------|-------------|----------------|
| AAPL & SPY | 0.79 | High — AAPL is a major SPY constituent |
| JPM & SPY | 0.71 | High — financials track broad market |
| JNJ & XOM | 0.30 | Low — best diversification pair |
| AAPL & XOM | 0.28 | Low — tech and energy independent |

### CVaR Results
| Method | VaR (95%) | CVaR (95%) |
|--------|-----------|------------|
| Historical | -1.80% | -3.16% |
| Parametric | -2.14% | -2.71% |

## Interpretation

There is a 5% probability that this portfolio loses more than 1.80% 
of its value on any given trading day. The 0.34% gap between methods 
indicates slight fat tails in the return distribution, consistent with 
real market stress events captured in the 2020-2024 period.

The correlation matrix reveals that genuine diversification in this 
portfolio comes from JNJ and XOM — healthcare and energy respond to 
completely different economic drivers. AAPL, SPY and JPM form a highly 
correlated cluster at 0.71 to 0.79, meaning a broad market selloff 
would hit all three simultaneously, offering limited protection.

The CVaR analysis exposes what VaR conceals. Once losses breach the 
1.80% threshold, the average loss on those worst days is 3.16% — 
nearly double the VaR estimate. This tail risk is precisely why 
regulators moved toward Expected Shortfall under Basel III.

## Recommendations

On a $1,000,000 portfolio the daily tail loss threshold is approximately 
$31,600 based on Historical CVaR — nearly double what VaR alone would suggest.

The high correlation between AAPL, SPY and JPM suggests the portfolio 
carries significant concentration risk despite holding five assets. 
Reducing exposure to this cluster and increasing allocation toward 
JNJ and XOM would lower portfolio variance and improve the Sharpe Ratio.

The 0.34% gap between Historical and Parametric VaR signals fat tails 
in the return distribution. Stressed VaR incorporating a dedicated 
crisis period such as 2008 would provide a more conservative and 
regulatory compliant risk estimate.

## Tools
- Python
- NumPy
- Pandas
- yfinance
- Matplotlib
- SciPy
- Seaborn


## Author
Cynthia Wanjiru | MS Quantitative Finance | Washington University in St Louis

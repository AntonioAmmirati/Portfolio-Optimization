# Geopolitical Resilience Portfolio

**A systematic, multi-asset allocation built to profit from geopolitical shocks**  
(Ukraine, Middle East, tariff wars). The strategy blends safe-havens, defence, energy and “bunker” staples, optimised via Markowitz with **Ledoit-Wolf shrinkage covariance** and strict sector / liquidity caps.

| Metric *(2021-01-01 → 2025-06-13)* | Portfolio | MSCI World | S&P 500 | NASDAQ 100 |
| --- | --- | --- | --- | --- |
| CAGR | **25 %** | 11 % | 13 % | 13 % |
| Vol σ | **9.6 %** | 16.7 % | 17.7 % | 23.7 % |
| Sharpe | **2.23** | 0.47 | 0.57 | 0.42 |
| Max DD | **-9.1 %** | -26 % | -24 % | -36 % |

---

## Quick Start
```bash
pip install -r requirements.txt      # pandas, numpy, yfinance, sklearn …
python run_pipeline.py               # downloads data & optimises
Needs a free FRED API key → export FRED_KEY=….

Universe & Buckets

Bucket	Tickers	Thesis
Safe-havens	GLD, FXF, TIP	Inflation + flight-to-quality
Energy	URA, CVX, LNG, 2222.SR	Supply security, dividend cushion
Defence	LMT, RHM.DE, HO.PA	NATO 2 % GDP, hypersonic tech
Bunker staples	NVO, PG, JNJ, DE	Crisis-resilient cash-flows
Tech edge	MSFT, CRWD	Cyber & cloud backbone
Optimiser

Returns – daily arithmetic
Covariance – Ledoit-Wolf shrinkage × 252
Objective – max Sharpe
Constraints
• Defence ≤ 25 % • Energy ≤ 15 % • Safe-havens ≥ 20 %
• CHF ≥ 5 % • Asset-cap ≤ 8 %
Walk-Forward Validation

Train → Test       CumRet  Sharpe  Sortino
2021-22 → 2022-24   12.8%   0.48     0.76
2022-24 → 2024-25   32.8%   2.63     4.92
Crisis Snapshots

Ukraine (Feb–Jun ’22) +9.6 % (S&P –14 %)
US Bank stress (Mar–Apr ’23) +7.1 % (DD -1.2 %)
Tariffs (Apr–Jun ’25) +7.6 % (DD -1.1 %)
Jensen α (2024-01 → 2025-06)

Benchmark	α ann.	β
MSCI World	+18.3 %	0.32
S&P 500	+19.1 %	0.25
NASDAQ 100	+19.4 %	0.19
(α = intercept of excess-return OLS, daily RF = 3-m T-Bill / 252)

Files

data/                # auto-downloaded prices
src/                 # optimiser, risk, plotting
notebooks/           # step-by-step analysis
run_pipeline.py      # end-to-end script
Limitations / Next Steps

No FX hedge on CHF/€ legs – overlay TBD
Turnover ≈ 18 % p.a.; include 10 bp slippage in live trading
Extend to factor model (FF-5, DEF, COM) for deeper attribution
License & Disclaimer

Research only — not investment advice. Past performance ≠ future results.



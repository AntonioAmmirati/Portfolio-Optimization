
This project implements a sophisticated portfolio optimization strategy designed to navigate volatile geopolitical environments while delivering strong risk-adjusted returns.

Key Features

Geopolitical resilience focus: Assets selected for crisis resistance
Constrained optimization: Sector caps for defense (≤25%), energy (≤15%), safe havens (≥20%)
Robust risk management: Liquidity requirements (≥5% in CHF) and strict diversification (max 8% per asset)
Comprehensive backtesting: Performance validation across multiple crisis periods
Portfolio Structure

Asset Allocation

Asset	Allocation
Gold (GLD)	8.00%
CHF (FXF)	8.00%
Saudi Aramco (2222.SR)	7.00%
Cheniere Energy (LNG)	8.00%
Rheinmetall (RHM.DE)	8.00%
Thales (HO.PA)	8.00%
TIPS USA (TIP)	8.00%
Indian Bonds (IGIL.L)	8.00%
Novo Nordisk (NVO)	8.00%
Microsoft (MSFT)	8.00%
Procter & Gamble (PG)	8.00%
Johnson & Johnson (JNJ)	8.00%
Other diversified assets	Balanced
Sector Allocation

Sector	Allocation	Constraint
Safe-Haven	24.00%	≥20%
Defense	16.94%	≤25%
Energy	15.00%	≤15%
Technology	11.12%	-
Consumer	16.00%	-
Other	16.94%	-
Performance Metrics (2021-2025)

Metric	Portfolio	MSCI World	S&P 500	NASDAQ 100
Annual Return	20.00%	10.67%	12.84%	12.59%
Volatility	9.33%	16.77%	17.80%	23.82%
Sharpe Ratio	1.81	0.45	0.55	0.40
Max Drawdown	-10.23%	-26.05%	-24.50%	-35.56%
Sortino Ratio	3.10	-	-	-
Crisis Performance

Crisis Period	Return	Max Drawdown
2022 Ukraine War	+6.73%	-0.43%
2023 Bank Crisis	+6.38%	-0.68%
2025 Trump Tariffs	+5.24%	0.00%
Implementation

python
# Core optimization workflow
def optimize_portfolio():
    # 1. Download and preprocess asset data
    assets = download_assets(start_date, end_date)
    
    # 2. Calculate returns and covariance matrix
    log_returns = calculate_log_returns(assets)
    cov_matrix = calculate_annualized_covariance(log_returns)
    
    # 3. Define optimization constraints
    constraints = [
        TotalWeightConstraint(1.0),
        SectorConstraint('Defense', MAX_DEFENSE),
        SectorConstraint('Energy', MAX_ENERGY),
        SectorConstraint('SafeHaven', MIN_SAFE_HAVEN),
        LiquidityConstraint(MIN_LIQUIDITY),
        DiversificationConstraint(MAX_SINGLE_ASSET)
    ]
    
    # 4. Maximize Sharpe ratio
    optimized_weights = maximize_sharpe(
        returns=log_returns.mean(),
        cov_matrix=cov_matrix,
        risk_free_rate=annualized_rf,
        constraints=constraints
    )
    
    return optimized_weights

# 5. Backtest and analyze performance
portfolio = backtest(optimized_weights)
analyze_performance(portfolio, benchmarks)
Requirements

Python 3.8+
pandas
numpy
scipy
matplotlib
yfinance

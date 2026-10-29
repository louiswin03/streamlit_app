# Portfolio Risk Engine — Streamlit app

Interactive risk engine for a multi-asset portfolio valued in euros, built for the
*Portfolio Risk Management with Python* project (MSc Finance & Big Data, NEOMA).

## Run it

```bash
pip install -r requirements.txt
streamlit run app.py
```

The app opens at http://localhost:8501. It starts from the saved Yahoo Finance dataset in `data/`
(2 Jan 2019 – 8 Oct 2026). Tickers or dates outside that file are downloaded automatically with
`yfinance`; switch on **Download fresh prices from Yahoo Finance** in the sidebar to refresh everything.

## What is in it

| Tab | Content |
|---|---|
| Overview | Holdings, capital vs risk allocation, prices in EUR |
| Data | Source, calendar alignment, currency conversion, CSV downloads |
| Performance | Return, volatility, Sharpe, skewness, kurtosis, drawdown, rolling volatility |
| Correlation | Correlation matrix by regime (calm 2019, Covid, 2022, 2025), rolling correlation, diversification ratio |
| VaR & ES | Historical, parametric and Monte Carlo VaR/ES at 1 day and N days, fat-tail variants, MC convergence, risk contributions |
| Backtesting | Rolling out-of-sample backtest, Kupiec, Christoffersen, Basel traffic light, exception list |
| Stress tests | Historical episodes (+ custom), editable per-asset shocks, beta-driven market shock, correlation and volatility stress, reverse stress test |
| Concentration | VaR/ES as the portfolio is moved into one asset; comparison with equal weights |
| Findings & export | Answers to the 8 project questions (computed live) and an Excel export of every table |

All inputs are validated: weights must be non-negative and sum to 100 % (or be rescaled on request),
tickers must be unique, the start date must precede the end date, at least one confidence level is
required, and the estimation window must fit in the available history.

## Files

- `app.py` — Streamlit interface
- `risk_engine.py` — calculations (no Streamlit), reusable from a notebook
- `data/yahoo_adj_close.csv` + `data/yahoo_adj_close_meta.json` — Yahoo Finance adjusted closes and source metadata
- `.streamlit/config.toml` — theme

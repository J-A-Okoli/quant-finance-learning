# Quant Projects

A collection of small quantitative finance projects I've built while learning options pricing, technical analysis, and backtesting in Python. I'm a sixth form student (Year 12, studying Maths, Further Maths, Physics and Computer Science) with an interest in quantitative development.

## Projects

### `binomial_model.ipynb`
A binomial tree option pricer, implemented in Cython for speed. Prices European and American options (both calls and puts) using backward induction, comparing early-exercise value against continuation value at each node for American options.

**What it does:** builds a full price tree from the initial spot price using up/down factors derived from volatility, computes payoffs at maturity, then works backward through the tree applying risk-neutral valuation.

**Limitations:** doesn't yet compare against a closed-form benchmark (e.g. Black-Scholes for the European case) to validate pricing accuracy — a natural next step.

### `sma_backtest.ipynb`
A simple moving average crossover strategy, backtested on historical price data (via `yfinance`). Goes long when a short-period SMA is above a long-period SMA, short when the reverse holds.

**What it does:** computes two rolling SMAs, generates a signal from their relative position, shifts the signal by one period to avoid lookahead bias, then computes and plots strategy returns against buy-and-hold.

**Limitations:** no transaction costs or slippage; single asset (AAPL) and a single parameter pair, not yet optimised or tested out-of-sample.

### `boliinger_bands.ipynb`
Visualises Bollinger Bands (20-day moving average ± 2 standard deviations) on a candlestick chart using live data.

**Note:** this is a visualisation, not a trading strategy — there's no signal generation or backtest here yet. A natural extension of `sma_backtest.ipynb`.

### `Chapter_8_financial_time_series.ipynb`
Study notes working through data I/O in Python for financial data — serialisation with `pickle`, CSV read/write, SQLite, and PyTables/HDF5 for larger datasets. Following exercises from *Python for Finance* (Hilpisch). Not original analysis — included as a record of what I've learned about handling financial data at scale.

## Setup

```bash
pip install numpy pandas matplotlib yfinance plotly cython
```

`binomial_model.ipynb` requires a working C compiler for the Cython cell to build.

## Notes

This is an active learning repo — expect gaps and rough edges. Next planned addition: a pairs trading strategy using cointegration testing.

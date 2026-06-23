# Momentum Strategy Backtest

A cross-sectional momentum strategy on large-cap US stocks, backtested with the parts that usually get skipped: trading costs, no lookahead, and fair benchmarks. Each month it ranks the stocks by their recent trend, buys the top fifth, holds for a month, and repeats.

The strategy is deliberately simple. The work is in testing it honestly, since that's where most backtests quietly cheat.

## How it's kept honest

- Signals use only past prices (a one-month shift), so the backtest never trades on information it wouldn't have had at the time.
- Trading costs (10 bps) are charged on turnover, and momentum turns over a lot.
- It's measured against an equal-weight basket of the same stocks and against SPY, not judged on its own return.

## Results

Over the backtest window the strategy beats SPY on both return and Sharpe. Against an equal-weight basket of the same stocks, though, the risk-adjusted edge is small: momentum earned more mostly by taking more risk and trading more. Performance is reported as annualized Sharpe, maximum drawdown, and CAGR. The exact numbers are in the notebook and shift a little as new price data comes in.

One limitation worth stating up front: the universe is today's large-caps, so the whole thing carries survivorship bias that flatters every result, benchmarks included. A point-in-time universe would be the honest fix.

## Running it

One notebook, `Momentum_Backtest.ipynb`. It pulls prices from Yahoo Finance through yfinance, so there's no account or API key to set up. To run locally:

```
pip install -r requirements.txt
```

then open the notebook and run it top to bottom.

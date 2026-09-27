# Backtest run template

Copy this file to `backtests/<variant-id>.md` when a variant has fixed mechanical rules.
Keep earlier runs as rows; do not replace them with a later optimization.

## Variant

- Pattern ID / variant ID:
- Hypothesis and baseline to compare:
- Exact detection rules (only information available at entry):
- Entry, stop, take profit, position sizing and invalidation:
- Session and time zone (include DST behavior):
- Instrument, broker data, timeframe and execution platform:
- Spread, commission, swap and slippage assumptions:
- Parameters frozen on:

## Runs

| Run date | Data period | In-sample / OOS / forward | Trades | Net (currency) | PF | Win % | Max DD % | Avg R | Recovery | Costs / caveats |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---|

## Decision

Describe what changed relative to the baseline, whether the unseen period agreed,
and which parameter choices were tried. Mark inconclusive samples explicitly.

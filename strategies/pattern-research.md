# Pattern Research / Combination Lab

The full searchable catalogue is in the **Pattern Library** section of the dashboard. Its entries are ideas, not validated trading strategies. Elliott structures have their own research family.

## Testing sequence

1. Define the shape numerically (pivots, symmetry, tolerance, confirmation and invalidation).
2. Test the pattern on its own, with known spread, fees and slippage.
3. Compare one extra filter at a time: PDL/PDH sweep, NY open, MSS, HTF direction or session.
4. Keep instrument, timeframe, period and risk model identical across comparisons; reserve unseen dates for out-of-sample validation.

First combination candidates: PDL sweep + Double Bottom + MSS; PDH sweep + Double Top + MSS; NY open + SFP; HTF sweep + Quasimodo.

## External research to replicate

- [Foundations of Technical Analysis](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=228099): use mechanical pattern detection instead of visual hindsight.
- [Predictive Power of Head-and-Shoulders Price Patterns](https://academic.oup.com/jfec/article-abstract/5/2/243/785044): keep Head and Shoulders as its own detector and compare it with sweep-filtered variants. Neither source measures our setup.

## Backtest log

| Date | Pattern / variant | Instrument / timeframe | Period | Trades | PF | Max DD | Avg R | OOS / forward | Notes |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-09-27 | Catalogue created | — | — | — | — | — | — | — | No measured results supplied. |

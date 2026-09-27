# Elliott Wave + Fibonacci + RSI

**Stage:** idea / specification. Existing EA logic needs its own measured test record before a performance claim.

## Structure catalogue

- Impulse 1–2–3–4–5; leading and ending diagonal.
- ABC corrections: zigzag, flat, expanded flat, running flat, triangle, double three and triple three.

## First testable variants

1. ZigZag wave structure + Fibonacci retracement entry; fixed stop and extension target.
2. Same rules with RSI confirmation on M1/M5.
3. Same rules after an HTF or previous daily high/low sweep and MSS.

Freeze ZigZag parameters, confirmed pivot timing, invalidation rules, fib levels, costs and time zone before testing. Avoid using pivots that become visible only after future candles: evaluate signals at the time an EA could actually place an order. Keep every parameter change as a separate variant.

## External research to replicate

- [Algorithm for Elliott Waves pattern detection](https://journals.sagepub.com/doi/10.3233/IDT-170319): compare confirmed pivot recognition against retrospective chart labels.
- [Algorithmic Fibonacci retracement zones](https://doi.org/10.1016/j.eswa.2021.115893): compare selected Fibo bands against predefined control bands. Neither paper verifies this EA's returns.

## Backtest log

| Date | Variant | Instrument / timeframe | Period | Trades | PF | Max DD | Avg R | OOS / forward | Notes |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-09-27 | Specification | — | — | — | — | — | — | — | No measured results supplied. |

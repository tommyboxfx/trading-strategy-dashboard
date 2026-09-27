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

## Backtest log

| Date | Variant | Instrument / timeframe | Period | Trades | PF | Max DD | Avg R | OOS / forward | Notes |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-09-27 | Specification | — | — | — | — | — | — | — | No measured results supplied. |

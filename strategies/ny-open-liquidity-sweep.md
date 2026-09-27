# NY Open Liquidity Sweep

## Core hypothesis
Price frequently takes nearby liquidity around the New York open before the directional move. Test the sweep as the event; do not assume every sweep is a reversal.

## Base sequence
1. Define pre-NY liquidity / relevant session high-low.
2. Liquidity sweep around NY open.
3. Require lower-timeframe displacement + MSS/CHOCH confirmation.
4. Wait for retracement rather than chasing the displacement.
5. Entry variants: FVG, valid Order Block, or defined retracement zone.
6. Test TP variants separately: next/opposite liquidity, HTF level, fixed 1:2 and 1:3 RR.
7. Test BE/partial rules separately.

## Research priority
**Priority #1.** Already observed as a promising family. Split tests by instrument, exact NY time window, direction, weekday and volatility regime.

## Metrics to record
PF, Max DD, trades, win rate, average R/trade, net profit, recovery factor, tested years, costs/slippage, in-sample vs out-of-sample/forward results.

## External research to replicate

- [Opening range breakout on selected US equities](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4729284): compare a breakout baseline with our sweep-reversal logic on identical days.
- [Pre-registered ORB cost study](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7428398): stress-test spreads, fees and slippage. Its reported conclusion differs from the selected-equity study; neither is our result.
- [Market intraday momentum](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2440866): investigate whether the direction of the opening move affects the closing window on US500.

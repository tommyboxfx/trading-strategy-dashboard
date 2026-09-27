# Previous Daily High / Low Sweep

## Core hypothesis
Previous Daily High (PDH) and Previous Daily Low (PDL) are major daily liquidity references. Test reactions only after an actual sweep and confirmation.

## Base sequence
1. Mark PDH and PDL before the session.
2. Detect sweep beyond the level and return/rejection conditions.
3. Require LTF displacement + MSS.
4. Test retracement entry via FVG / valid OB / defined percentage zone.
5. Separate long-from-PDL and short-from-PDH statistics.

## Research priority
**Priority #2.** Treat PDH/PDL as HTF liquidity. Compare London vs New York executions and confluence with session highs/lows.

## Robustness splits
Instrument, weekday, session, distance from daily open, sweep depth, HTF bias, news/no-news, costs and slippage.

## External research to replicate

- [Currency orders and exchange-rate dynamics](https://www.newyorkfed.org/research/staff_reports/sr125.html) and [stop-loss price cascades](https://www.newyorkfed.org/research/staff_reports/sr150.html) suggest testing both rejection and continuation after a level is crossed. They study FX order clustering, not specifically PDH/PDL or our EA.

# ICT Sweep + MSS + FVG / OB Confluence

## Purpose
A controlled research bucket for filters added to the sweep edge. The goal is to determine which filters improve robustness rather than stacking ICT concepts without measurement.

## Components to test independently
Liquidity sweep → MSS/CHOCH → displacement → FVG → valid Order Block → OTE → Killzone → SMT divergence / PO3 context.

## Order Block definition for testing
Use an objective rule: last opposing candle/group before displacement, associated with a relevant structure break (BOS/MSS), preferably leaving imbalance/FVG. Track first mitigation separately.

## Rule
Add one filter at a time and compare against the base sweep model. Keep a filter only if it improves out-of-sample robustness, not merely historical net profit.

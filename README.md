# Trading Strategy Dashboard

Live page: https://tommyboxfx.github.io/trading-strategy-dashboard/

A static dashboard of trading strategies. Data lives in `data/strategies.json`, one Markdown note per strategy
in `strategies/`. Click a row on the page to open its note; `#<id>` in the URL links straight to one strategy.

## How to add or update a strategy
Edit `data/strategies.json` and `strategies/<id>.md` (GitHub web editor, ChatGPT/Codex, or git).
The exact format and the rules for AI assistants are in [AGENTS.md](AGENTS.md).

## Research catalogue and score
`data/patterns.json` contains the searchable Pattern Library. Patterns are research ideas,
not backtested strategies. Elliott Wave is tracked separately in `strategies/elliott-wave-fibo-rsi.md`.
Every catalogue item has a stable `id` and a lifecycle `status` (`idea`, `testing`,
`live`, `paused`, `retired`). `data/variants.json` holds concrete combinations and
references a pattern by `pattern_id`. Keep metrics `null` until actual results exist.
When a variant becomes testable, specify its exact entry, invalidation, stop, exit,
session time zone, instrument, timeframe and costs. Record each run in a separate
backtest note using [the run template](BACKTEST_TEMPLATE.md); link that note from
the variant before promoting its status.

The dashboard sorts measured strategies by a provisional 0–100 score, then unscored
ideas by research priority. A score requires status `testing` or `live`, at least 100
trades, and numeric profit factor, maximum drawdown percentage and average R.
Weights: PF 40, drawdown 30, average R 20, trade count 10. These are comparison
weights, not proof of a trading edge. Leave missing metrics as `null`; record test
period, costs and out-of-sample results in each strategy note.

**This repository is public** - no account numbers, keys, tokens or private details.

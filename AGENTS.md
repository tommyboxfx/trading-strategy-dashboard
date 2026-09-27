# Instructions for AI assistants (ChatGPT / Codex / Claude)

This repository is a PUBLIC static dashboard (GitHub Pages). The page `index.html` reads
`data/strategies.json` and shows each strategy's note from `strategies/<id>.md`. No build step.

## What you may change
- `data/strategies.json` - add/update strategy entries (format below). Also set the top-level `"updated"` date.
- `strategies/<id>.md` - one Markdown note per strategy (idea, rules, backtest log, open questions).
- Do NOT edit `index.html` unless the owner explicitly asks for a dashboard change.

## Entry format (one object in `strategies`)
```json
{
  "id": "lowercase-with-dashes (unique, also the note file name)",
  "name": "Human readable name",
  "instrument": "BTCUSD",
  "timeframe": "M5",
  "platform": "MT5",
  "status": "idea | testing | live | paused | retired",
  "tags": ["short", "labels"],
  "summary": "One or two sentences.",
  "metrics": {
    "period": "YYYY-MM-DD .. YYYY-MM-DD",
    "net_profit": 1234.5,
    "profit_factor": 1.42,
    "win_rate_pct": 55.3,
    "max_drawdown_pct": 12.8,
    "trades": 311
  },
  "notes": "strategies/<id>.md",
  "updated": "YYYY-MM-DD"
}
```
Unknown metrics = `null` (never invent numbers). Numbers are plain JSON numbers (no `%`, no currency sign).

## Rules
1. The file must stay VALID JSON (double quotes, no trailing commas, no comments).
2. Never delete another strategy unless asked; change only the entries you were asked about.
3. Append new backtest results as a new row in the note's "Backtest log" table instead of overwriting old ones.
4. PUBLIC REPO: never write account numbers, broker logins, API keys, tokens, passwords, personal data,
   or anything the owner marked private.
5. Commit message: `strategy: <id> - <what changed>` (e.g. `strategy: lawa-btc - add Sep backtest`).

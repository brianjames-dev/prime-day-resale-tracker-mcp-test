# Prime Day Resale / Price Timing Tracker (MCP Test)

Bounded multi-MCP exercise: capture Prime Day buy costs, log ongoing prices, and surface sell-timing / margin signals when market prices rise above the Prime Day cost.

## Spreadsheet (existing — do not recreate)

[Prime-Day-Grok-Test](https://docs.google.com/spreadsheets/d/1j-dRfrY7ZK0mpwTy0RsmyQOeQhs9XGxp5sHjaoHcZhk/edit)  
Shared with service account: `grok-sheets-sa@grok-sheets-500518.iam.gserviceaccount.com`

| Tab | Purpose |
|-----|---------|
| **Items** | Candidate deals: SKU identity, Prime Day buy cost, list-at-capture, source URL |
| **Price History** | Time-series logs (`prime_day_buy`, later `market_check` / `resale_ask`) |
| **Summary** | Lowest-price flag, proxy resale, profit margin $, %, sell timing signal |

## Goal

1. Buy (or record) during Prime Day when price is cheap.
2. Append new price checks after Prime Day.
3. Know when current price is at its **lowest logged** vs not.
4. Estimate **profit margin** = later market/resale price − Prime Day buy cost (before fees).

## MCP stack (MCP-first)

| Capability | MCP |
|------------|-----|
| Public deal pages | Firecrawl (`search`, `scrape`) |
| Spreadsheet | Google Sheets MCP |
| Docs + issues | GitHub MCP |

No custom scrapers; no direct Sheets/GitHub HTTP unless MCP cannot complete a step.

## Bounds (this test)

- ≤5 source URLs scraped, ≤10 items, one spreadsheet, one repo, ≤3 issues
- Public editorial deal pages only (not Amazon product pages)

## Docs in this repo

- [docs/SCHEMA.md](docs/SCHEMA.md) — column definitions
- [docs/METHOD.md](docs/METHOD.md) — capture + signal rules
- [docs/SOURCES.md](docs/SOURCES.md) — URLs crawled
- [docs/MCP_USAGE_LOG.md](docs/MCP_USAGE_LOG.md) — tools used / blocked

## Status

Seeded **8 items** on 2026-06-26 from WIRED, Consumer Reports, and NBC Select. List prices are stored as `list_at_capture_proxy` until real post-Prime-Day rechecks are appended to **Price History**.

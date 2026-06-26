# Prime Day Resale / Price Timing Tracker (MCP Test)

Capture **Amazon buy-box** prices during Prime Day, log ongoing Amazon rechecks, and surface sell-timing / margin signals when market prices rise above cost.

## Spreadsheet

[Prime-Day-Grok-Test](https://docs.google.com/spreadsheets/d/1j-dRfrY7ZK0mpwTy0RsmyQOeQhs9XGxp5sHjaoHcZhk/edit)  
Service account: `grok-sheets-sa@grok-sheets-500518.iam.gserviceaccount.com`

| Tab | Purpose |
|-----|---------|
| **Items** | ASIN, Amazon URL, buy box cost, Amazon list, deal badge |
| **Price History** | `amazon_buy_box` / `amazon_list_price` (+ later rechecks) |
| **Summary** | Lowest logged, margin vs list proxy, sell timing signal |

## Price source policy

**Amazon product pages only** for cost and list (Firecrawl scrape of `/dp/ASIN`).  
Editorial sites may suggest search terms; they are not authoritative for pricing.

## MCP stack

Firecrawl (search + scrape Amazon PDPs) → Google Sheets MCP → GitHub MCP for docs/issues.

## Docs

- [docs/SCHEMA.md](docs/SCHEMA.md)
- [docs/METHOD.md](docs/METHOD.md)
- [docs/SOURCES.md](docs/SOURCES.md) — Amazon ASINs + URLs + prices
- [docs/MCP_USAGE_LOG.md](docs/MCP_USAGE_LOG.md)

# MCP usage log (incl. Amazon correction)

## Correction pass (2026-06-26)

User feedback: prices must come from **Amazon**, not editorial recaps.

### Firecrawl

| Tool | Purpose | Outcome |
|------|---------|---------|
| `firecrawl_search` | Resolve Amazon `/dp/` URLs by product name | OK |
| `firecrawl_scrape` | Amazon PDPs (JSON: price, list, ASIN, badge) | OK for 8 ASINs |

Amazon PDPs scraped successfully (buy box + list). Some jobs throttled on concurrency; still returned prices.

### Google Sheets

| Tool | Purpose | Outcome |
|------|---------|---------|
| `sheets_clear_values` | Clear prior editorial-sourced rows | OK |
| `sheets_batch_update_values` | Rewrite Items / Price History / Summary from Amazon | OK |

### GitHub

| Tool | Purpose | Outcome |
|------|---------|---------|
| `push_files` | Update SOURCES, METHOD, SCHEMA, MCP log, README | OK |

## First pass (superseded for pricing)

Editorial WIRED/CR/NBC scrapes used only for candidate discovery; PCMag blocked. Sheet no longer treats those as price sources.

## Blocked / limitations

- Amazon prices are **point-in-time** Firecrawl extracts (cache possible).
- Coupons (e.g. Airwrap “Save $50”) may not reduce `current_price` field.
- AirPods Pro 2 and Airwrap Origin showed **buy box = list** on Amazon at scrape → SKIP/WATCH.
- No secret key files opened.

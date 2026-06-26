# Schema

## Items

| Column | Type | Notes |
|--------|------|-------|
| item_id | string | Stable id (`PD-00N`) |
| name | string | Product title from source |
| brand | string | |
| category | string | Headphones, Tablets, etc. |
| source_name | string | Editorial outlet |
| source_url | url | Public deal page |
| prime_day_buy_cost | number USD | Cost basis for margin |
| list_price_at_capture | number USD | Was/list on source page |
| status | string | `tracking` / `sold` / `dropped` |
| notes | string | |
| captured_at | date | ISO date |

## Price History

| Column | Type | Notes |
|--------|------|-------|
| history_id | string | `PH-00N` |
| item_id | string | FK → Items |
| check_date | date | When price was observed |
| price | number USD | |
| price_type | enum | `prime_day_buy`, `list_at_capture_proxy`, `market_check`, `resale_ask` |
| source_name | string | |
| source_url | url | |
| notes | string | |

**Ongoing use:** append new rows with `market_check` or `resale_ask` after Prime Day; never overwrite history.

## Summary

| Column | Type | Notes |
|--------|------|-------|
| item_id | string | |
| name | string | |
| prime_day_buy_cost | number | From Items |
| latest_market_proxy | number | Highest non-buy reference for demo; replace with latest `market_check` |
| lowest_logged_price | number | MIN of all Price History prices for item |
| is_at_lowest | YES/NO | Whether latest check equals lowest_logged |
| potential_resale_proxy | number | Sell-side estimate (proxy or `resale_ask`) |
| profit_margin_usd | number | potential_resale − prime_day_buy_cost |
| profit_margin_pct | number | margin / prime_day_buy_cost |
| sell_timing_signal | enum | See METHOD.md |
| signal_notes | string | |

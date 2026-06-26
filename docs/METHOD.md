# Method

## Capture

1. Discover public Prime Day deal roundups via Firecrawl **search** (editorial sites).
2. **Scrape** ≤5 URLs with JSON extraction (name, current_price, list_price, category, brand).
3. Curate 5–10 resale-friendly candidates (electronics / appliances / wearables).
4. Write **Items** once with `prime_day_buy_cost` = observed deal price.
5. Seed **Price History** with `prime_day_buy` and optional `list_at_capture_proxy` (was/list price).
6. Refresh **Summary** signals from history.

## Ongoing price checks (post Prime Day)

1. Re-scrape the same editorial pages or other public market signals.
2. Append `market_check` rows (do not mutate prior rows).
3. Optionally append `resale_ask` from public resale listings when available.
4. Recompute Summary: lowest price, is_at_lowest, margins.

## Sell timing / margin signals

| Signal | Rule (v0) |
|--------|-----------|
| **HOLD_FOR_RESALE** | Prime Day cost is lowest logged **and** proxy/resale margin ≥ ~25% of cost |
| **WATCH** | Margin positive but < 25%, or insufficient history |
| **SELL_WINDOW** | Latest market/resale ≥ potential target and not at lowest (market already rising; consider selling) |
| **SKIP** | Margin ≤ 0 after fees (fees not modeled in v0) |

**Profit margin (gross, pre-fee):**

```
profit_margin_usd = potential_resale_proxy - prime_day_buy_cost
profit_margin_pct = profit_margin_usd / prime_day_buy_cost
```

**Lowest price:** MIN(price) over Price History for that `item_id`.

**Caveats:** Editorial prices lag Amazon; list proxies are not realized resale; platform fees/shipping/tax not included; this is an MCP integration test, not investment advice.

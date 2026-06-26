# Method

## Capture (Amazon-first)

1. Discover candidate ASINs via Firecrawl **search** on `amazon.com` (product queries).
2. **Scrape each Amazon PDP** (`/dp/ASIN`) with Firecrawl JSON extraction:
   - `title`, `asin`, `current_price` (buy box), `list_price`, `deal_badge`, `availability`
3. Write **Items** with `prime_day_buy_cost` = Amazon buy box; `list_price_on_amazon` = Amazon list/was; `amazon_product_url` + `asin`.
4. Seed **Price History** with `amazon_buy_box` and `amazon_list_price` rows (source = Amazon PDP URL).
5. Build **Summary** margins vs Amazon list as recovery proxy until post-event **Amazon rechecks** are appended.

Editorial sites may inform *what* to search, never replace Amazon pricing for cost basis.

## Ongoing price checks (post Prime Day)

1. Re-scrape the **same Amazon PDP URLs** (same ASIN).
2. Append `amazon_buy_box` (or `market_check`) rows — never overwrite history.
3. Recompute lowest price, is_at_lowest, margins.
4. Optional: public resale `resale_ask` rows later for realized sell price.

## Sell timing / margin signals

| Signal | Rule (v0) |
|--------|-----------|
| **HOLD_FOR_RESALE** | Buy box &lt; list on Amazon **and** margin ≥ ~25% of cost |
| **WATCH** | Thin/ambiguous discount (e.g. coupon only) |
| **SELL_WINDOW** | Later Amazon/market price rises while cost basis was PD low |
| **SKIP** | Buy box ≈ list (no arb entry on this scrape) |

```
profit_margin_usd = potential_resale_proxy - amazon_buy_box
profit_margin_pct = profit_margin_usd / amazon_buy_box
```

**Caveats:** Firecrawl may cache PDPs; prices are point-in-time; coupons may not be in buy box field; fees not modeled.

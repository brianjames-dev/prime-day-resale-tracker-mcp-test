# Schema (Amazon-sourced)

## Items

| Column | Notes |
|--------|-------|
| item_id | `PD-00N` |
| asin | Amazon ASIN |
| name | Title from Amazon PDP |
| brand, category | |
| source_name | `Amazon PDP` |
| amazon_product_url | Canonical `/dp/` URL |
| prime_day_buy_cost | Amazon **buy box** at capture |
| list_price_on_amazon | Amazon list/was |
| deal_badge | e.g. 50% off, Amazon's Choice |
| availability | In Stock, etc. |
| status | tracking / sold / dropped |
| notes | |
| captured_at | date |

## Price History

| Column | Notes |
|--------|-------|
| history_id | `PH-00N` |
| item_id, asin | |
| check_date | |
| price | USD |
| price_type | `amazon_buy_box`, `amazon_list_price`, later `market_check`, `resale_ask` |
| source_name | `Amazon PDP` |
| amazon_product_url | |
| notes | |

## Summary

Margins use Amazon buy box as cost and Amazon list (or later checks) as resale proxy until real post-PD Amazon rechecks.

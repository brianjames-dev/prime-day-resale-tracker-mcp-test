# Sources (corrected — Amazon PDPs)

**Primary source of truth:** Amazon product detail pages (`amazon.com/.../dp/ASIN`), scraped with Firecrawl.

Editorial roundups (WIRED / CR / NBC) were used only in the first pass for candidate *discovery*; prices and titles in the sheet were **rewritten** from live Amazon buy box + list fields.

## Amazon product pages scraped (Firecrawl `firecrawl_scrape`)

| item_id | ASIN | Amazon URL | Buy box | List on Amazon | Deal badge |
|---------|------|------------|---------|----------------|------------|
| PD-001 | B0FQFB8FMG | https://www.amazon.com/Apple-Cancellation-Translation-Headphones-High-Fidelity/dp/B0FQFB8FMG | 179.00 | 249.00 | Amazon's Choice |
| PD-002 | B0D7WZV5LV | https://www.amazon.com/Dyson-OnTracTM-Over-Wireless-Headphones/dp/B0D7WZV5LV | 249.99 | 499.00 | 50% off |
| PD-003 | B0DVZYQT3T | https://www.amazon.com/Samsung-Processor-Note-Taking-Manufacturer-Warranty/dp/B0DVZYQT3T | 334.99 | 549.99 | 39% off |
| PD-004 | B091G68F8C | https://www.amazon.com/Amazon-eero-Wi-Fi-router-newest/dp/B091G68F8C | 239.99 | 329.99 | 27% off |
| PD-005 | B0CC62ZG1M | https://www.amazon.com/Fitbit-Charge-Fitness-Tracker-Google/dp/B0CC62ZG1M | 85.45 | 159.95 | Amazon's Choice |
| PD-006 | B0DMYQ32SC | https://www.amazon.com/JBL-Flip-Waterproof-Interchangeable-Accessories/dp/B0DMYQ32SC | 94.95 | 149.95 | Amazon's Choice |
| PD-007 | B0CHWRXH8B | https://www.amazon.com/Apple-Generation-Cancelling-Transparency-Personalized/dp/B0CHWRXH8B | 269.29 | 269.29 | (none) |
| PD-008 | B0DMXJXWH3 | https://www.amazon.com/Dyson-Airwrap-Multi-Styler-Flyaway-Attachment/dp/B0DMXJXWH3 | 549.99 | 549.99 | Save $50 coupon |

URLs resolved via Firecrawl **search** (`site:amazon.com` / product queries), then **scrape** with JSON extraction (title, ASIN, current_price, list_price, deal_badge, availability).

## Why not editorial alone

Editorial prices lag and can misstate list/deal depth (e.g. Tab S10 FE list **$549.99** on Amazon vs **$499.99** on one CR extraction). Resale timing requires **Amazon buy box** as cost basis and Amazon list (or later Amazon rechecks) for recovery signals.

## Discovery (non-authoritative)

Earlier Firecrawl search also hit WIRED / CR / NBC / PCMag for idea generation only. PCMag scrape was blocked. Those pages are **not** price sources in the sheet after this correction.

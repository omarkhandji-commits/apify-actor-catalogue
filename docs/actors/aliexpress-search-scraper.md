---
title: "AliExpress Product Search Scraper - Real Prices, Units Sold"
description: "AliExpress product search scraper: search results with the seller's real price, not the new-shopper teaser: list price, discount, rating, units sold, photos, free shipping, delivery estimate, ads flagged. Tested: 0 teaser prices vs 19 of 48 for a rival. $1.50 per 1,000."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# AliExpress Product Search Scraper - Real Prices, Units Sold

AliExpress product search scraper: search results with the seller's real price, not the new-shopper teaser: list price, discount, rating, units sold, photos, free shipping, delivery estimate, ads flagged. Tested: 0 teaser prices vs 19 of 48 for a rival. $1.50 per 1,000.

**Run it on Apify:** [https://apify.com/om_kh/aliexpress-search-scraper](https://apify.com/om_kh/aliexpress-search-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Search words (`phone case`) or AliExpress search links |
| **We do** | Read AliExpress search results, logged out, with your price, rating and order filters |
| **You get** | One row per product (up to 3,000 per search): the seller's real price, list price, discount, rating, units sold, Choice flag, delivery estimate and badges, with ads flagged |
| **It costs** | $1.50 per 1,000 products (since 21 Nov 2026; was $3), + $0.001 per run. The first 10 products of every run are free; searches with no product and AliExpress outages are not charged |
| **It does not** | Open product pages, so there are no variants and no reviews |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchTerms` | array | What you would type in the AliExpress search box, one per line. Default: `["phone case", "led strip"]`. |
| `searchUrls` | array | Paste AliExpress search links (aliexpress.com/w/wholesale-...html); the search words are read from the link. |
| `maxProductsPerSearch` | integer | Unique products per search (repeats removed). Default: `100`. |
| `sortBy` | string | The AliExpress sort orders. Default: `"best_match"`. |
| `minPrice` | number | Only products whose seller price is at or above this. |
| `maxPrice` | number | Only products whose seller price is at or below this. |
| `minRating` | number | Only products rated at least this (0 to 5). |
| `minOrders` | integer | Only products sold at least this many times. |
| `includeSponsored` | boolean | Keep the products AliExpress shows as ads. Default: `true`. |
| `maxTotalChargeUsd` | number | The run stops delivering once this amount is reached; you are never charged more. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "productId": "1005013148549041",
  "title": "Night Light Liquid Quicksand TPU Soft Case for IPhone Air 17 16 15 13 12 11 Pro Max 14 Plus 17Pro I Phone Bling Glitter Cover",
  "url": "https://www.aliexpress.com/item/1005013148549041.html",
  "price": 4.88,
  "originalPrice": 4.96,
  "discountPercent": 2,
  "currency": "USD",
  "rating": 4.9,
  "soldCount": 307,
  "soldText": "307 sold",
  "isChoice": true,
  "isSponsored": false,
  "deliveryEstimate": "Fastest delivery in 6 days",
  "badges": [
    "Extra 2% off with coins"
  ],
  "listedAt": "2026-09-09",
  "categoryIds": [
    "202192403",
    "202228401"
  ],
  "imageUrl": "https://ae-pic-a1.aliexpress-media.com/kf/Sd82fe984877c4bc6b0afb388d5e031e0J.jpg",
  "images": [
    "https://ae-pic-a1.aliexpress-media.com/kf/Sd82fe984877c4bc6b0afb388d5e031e0J.jpg",
    "https://ae-pic-a1.aliexpress-media.com/kf/S0d3c5a0909954128946ba94043eb5ba93.jpg"
  ],
  "freeShipping": false,
  "localWarehouse": false,
  "position": 9,
  "page": 1,
  "searchTerm": "phone case",
  "sortBy": "best_match",
  "type": "product"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/aliexpress-search-scraper").call(run_input={
    "searchTerms": [
        "phone case",
        "led strip"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~aliexpress-search-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["phone case", "led strip"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/aliexpress-search-scraper` as a tool.

Full documentation, pricing and the latest changes: [AliExpress Product Search Scraper - Real Prices, Units Sold](https://apify.com/om_kh/aliexpress-search-scraper).

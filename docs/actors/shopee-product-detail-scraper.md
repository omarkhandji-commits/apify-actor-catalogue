---
title: "Shopee Price Tracker - Exact Price, Variants, Units Sold"
description: "Shopee price tracker by product URL: exact price included, rating, SKU variants, description, images and the seller profile (followers, response rate). price_verified flag. Our fee $4 per 1,000 products, $3 from Nov 28, 2026, + supplier (~$4.20). All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Shopee Price Tracker - Exact Price, Variants, Units Sold

Shopee price tracker by product URL: exact price included, rating, SKU variants, description, images and the seller profile (followers, response rate). price_verified flag. Our fee $4 per 1,000 products, $3 from Nov 28, 2026, + supplier (~$4.20). All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/shopee-product-detail-scraper](https://apify.com/om_kh/shopee-product-detail-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Shopee product links or item IDs |
| **We do** | Read each product's page |
| **You get** | One row per product: title, exact price, rating, SKU variants, description, category, images, specifications, option lists (colours, sizes), ship-from location, delivery estimate, units sold, favourites and the seller's profile (rating, followers, response rate, official shop), plus every field the supplier returns (`source_data`) |
| **It costs** | $0.004 per product ($0.003 from Nov 28, 2026, 12:00 UTC) + $0.002 per priced SKU variant, + $0.001 per run. Apify also bills the supplier Actor `lergassy/shopee-scraper` that this robot runs for you, at its own price (about $3.20 per 1,000 products + $0.005 per batch of up to 5). An item that returns an error is never charged |
| **It does not** | Sign in to Shopee or place orders |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `productUrls` | array | Shopee product URLs to fetch. Default: `["https://shopee.sg/-SG-STOCK-Logitech-M331-SILENT-PLUS-Wire`. |
| `itemIds` | array | Shopee item IDs, if you have them instead of URLs. |
| `countries` | array | Shopee marketplace country codes to match against a URL, e.g. sg, my, th, ph, vn, id, tw. |
| `includeVariants` | boolean | Include each SKU variant (id and name; price and stock when the backup supplier gives them). Default: `true`. |
| `includeReviews` | boolean | Include a review count summary where available. Default: `false`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only products not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "input_ref": "https://shopee.sg/product-i.131198971.6646421738",
  "item_id": "6646421738",
  "shop_id": "131198971",
  "product_url": "https://shopee.sg/product-i.131198971.6646421738",
  "title": "Baseus WM01 TWS Bluetooth Earphones Stereo Wireless 5.3 Bluetooth Headphones Touch Control Noise Cancelling Gaming Headset For i 13 12 mini pro max",
  "brand": "BASEUS",
  "description": "Hey~ Welcome to Baseus Official Store!!! Please read the product description cle...",
  "category_path": [
    "Mobile & Gadgets",
    "Audio",
    "Earphones"
  ],
  "image_urls": [
    "https://down-sg.img.susercontent.com/file/cn-11134207-7r98o-lt3ijo9b9xwde3",
    "https://down-sg.img.susercontent.com/file/cn-11134207-820l4-mu77or6cjll4da"
  ],
  "condition": "NewCondition",
  "listed_at": "2020-08-13T07:07:52.000Z",
  "list_price": 11.44,
  "exact_price": 11.44,
  "price_verified": true,
  "price_verification_reason": null,
  "discount_percent": 74,
  "currency": "SGD",
  "variants": [
    {
      "sku_id": "411327162463",
      "attrs": "WM02S Black",
      "price": null,
      "stock": null
    },
    {
      "sku_id": "50598177672",
      "attrs": "Green",
      "price": null,
      "stock": null
    }
  ],
  "stock_total": null,
  "rating": 4.9,
  "seller": {
    "name": "(hidden here)",
    "rating": 4.89,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/shopee-product-detail-scraper").call(run_input={
    "productUrls": [
        "https://shopee.sg/-SG-STOCK-Logitech-M331-SILENT-PLUS-Wireless-Mouse-2.4GHz-with-USB-Receiver-Optical-Tracking-1-YEAR-LOCAL-WARRANTY-i.12496837.29695565289"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~shopee-product-detail-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"productUrls": ["https://shopee.sg/-SG-STOCK-Logitech-M331-SILENT-PLUS-Wireless-Mouse-2.4GHz-with-USB-Receiver-Optical-Tracking-1-YEAR-LOCAL-WARRANTY-i.12496837.29695565289"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/shopee-product-detail-scraper` as a tool.

Full documentation, pricing and the latest changes: [Shopee Price Tracker - Exact Price, Variants, Units Sold](https://apify.com/om_kh/shopee-product-detail-scraper).

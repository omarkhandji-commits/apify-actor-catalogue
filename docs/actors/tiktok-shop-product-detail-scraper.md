---
title: "TikTok Shop Product Detail Scraper"
description: "TikTok Shop product detail with verified price, exact SKU variants, stock and seller — every value carries its source URL and a verification flag. Our fee $0.0125 per product + supplier. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# TikTok Shop Product Detail Scraper

TikTok Shop product detail with verified price, exact SKU variants, stock and seller — every value carries its source URL and a verification flag. Our fee $0.0125 per product + supplier. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/tiktok-shop-product-detail-scraper](https://apify.com/om_kh/tiktok-shop-product-detail-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | TikTok Shop product links |
| **We do** | Read each product and verify its price |
| **You get** | One row per product: title, verified price, named SKU variants (e.g. `Color: Red`), stock and seller, description, photos, category, rating and review count, original price and discount, shipping price, units sold, sales in the last 30 days, total sales value (GMV), creator videos and affiliate creators, every value with its source link and a verification flag, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.0125 per product + $0.002 per SKU variant, + $0.001 per run from Nov 26, 2026 (no start fee before). Apify also bills the supplier Actor `pratikdani/tiktok-shop-scraper` that this robot runs for you, at its own price (about $0.025 per product on the free plan, $0.015 on paid plans), so about **$0.0375 per product in total**. An item that returns an error is never charged |
| **It does not** | Sign in to TikTok or place orders |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `productUrls` | array | TikTok Shop product URLs to fetch. Default: `["https://shop.tiktok.com/view/product/1732417183133045688"]`. |
| `productIds` | array | TikTok Shop product IDs, if you have them instead of URLs. |
| `regions` | array | TikTok Shop region of the products, e.g. US, GB, ID, TH, VN. Default: `["US"]`. |
| `includeVariants` | boolean | Include per-SKU price, stock, and attributes. Default: `true`. |
| `includeSeller` | boolean | Include seller name and shop URL. Default: `true`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only products not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "product_id": "1732417183133045688",
  "product_url": "https://www.tiktok.com/shop/pdp/1732417183133045688",
  "title": "5-1 FreshHood Apparel fast shipping 100% cotton T-shirts",
  "price": 25.99,
  "price_verified": true,
  "currency": "USD",
  "variants": [
    {
      "sku_id": "1732417196783539128",
      "price": 25.99,
      "stock": 961501
    },
    {
      "sku_id": "1732417196783473592",
      "price": 25.99,
      "stock": 961501
    }
  ],
  "stock_total": "4.81M",
  "sold_count": "192.98K",
  "description": "Thank you for trusting and shopping at our shop
Product information: ...",
  "images": ["https://cdn-image.hdnet.workers.dev/.../1732417183133045688_0.webp"],
  "category_path": "Menswear & Underwear/Men's Tops/T-shirts",
  "rating": null,
  "review_count": 0,
  "sold_count_number": 192980,
  "gmv_total_usd": 5600000,
  "seller_type": "Local",
  "listed_at": "2026-06-09T02:54:52+00:00",
  "seller": {
    "name": "(hidden here)",
    "url": "https://www.tiktok.com/shop/store/freshhood-apparel/7494495282633476024"
  }
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/tiktok-shop-product-detail-scraper").call(run_input={
    "productUrls": [
        "https://shop.tiktok.com/view/product/1732417183133045688"
    ],
    "regions": [
        "US"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~tiktok-shop-product-detail-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"productUrls": ["https://shop.tiktok.com/view/product/1732417183133045688"], "regions": ["US"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/tiktok-shop-product-detail-scraper` as a tool.

Full documentation, pricing and the latest changes: [TikTok Shop Product Detail Scraper](https://apify.com/om_kh/tiktok-shop-product-detail-scraper).

---
title: "Amazon Search Results Scraper - Price, Rating, Listing"
description: "Scrape Amazon search results or category pages for any keyword: title, ASIN, price, rating, review count, image and product URL. No login needed. Built for price research, product discovery and competitor analysis. $10 per 1,000 products. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Amazon Search Results Scraper - Price, Rating, Listing

Scrape Amazon search results or category pages for any keyword: title, ASIN, price, rating, review count, image and product URL. No login needed. Built for price research, product discovery and competitor analysis. $10 per 1,000 products. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/amazon-product-search-scraper](https://apify.com/om_kh/amazon-product-search-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords or Amazon category links |
| **We do** | Read Amazon's search results |
| **You get** | One row per product: title, ASIN, brand, rating, review count, monthly sales, Amazon's Choice, stock, fastest delivery, category path, features, the product's spec table as columns (`productOverview_Brand`, `attributes_Color`...), its best-seller rank in each category (`bestsellerRanks_<category>`), link and image, plus every field the supplier returns (`source_data`) |
| **It costs** | $10 per 1,000 products + $0.001 per run. Optional scheduled monitoring: +$0.12 per check (one-off runs never pay it). Apify also bills the supplier Actor `junglee/Amazon-crawler` that this robot runs for you, at its own price (about $5 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Amazon or buy anything |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchUrls` | array | Amazon search or category URLs to monitor for new products. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "https://www.amazon.com/dp/B0HL938SDP",
  "query_id": "https://www.amazon.com/s?k=standing+desk",
  "title": "DUMOS OverBed Table with Wheels Height Adjustable Rolling Desk, White",
  "url": "https://www.amazon.com/dp/B0HL938SDP",
  "score": 4.6,
  "asin": "B0HL938SDP",
  "inStock": true,
  "inStockText": "In Stock",
  "brand": "DUMOS",
  "reviewsCount": 92,
  "breadCrumbs": "Office Products > Office Furniture & Lighting > Desks & Workstations > Computer Workstations",
  "videosCount": 2,
  "thumbnailImage": "https://m.media-amazon.com/images/I/51Bd-QOhQlL._AC_SY300_SX300_QL70_FMwebp_.jpg",
  "galleryThumbnails": [
    "https://m.media-amazon.com/images/I/31kHUoMOjPL._AC_US.jpg",
    "https://m.media-amazon.com/images/I/41s9-LF8EcL._AC_US.jpg"
  ],
  "highResolutionImages": [
    "https://m.media-amazon.com/images/I/51Bd-QOhQlL._AC_SL1500_.jpg",
    "https://m.media-amazon.com/images/I/71inm1Q+uDL._AC_SL1500_.jpg"
  ],
  "features": [
    "Easy Height Adjustment: The rolling table features a built-in pneumatic lift system that allows you to easily adjust the table height fro...",
    "Hidden Casters for Easy Mobility: This over bed table is equipped with hidden 360° swivel casters, allowing the desk to move easily where..."
  ],
  "variantAsins": [
    "B0HL8R93CB",
    "B0HL938SDP"
  ],
  "reviewsLink": "https://www.amazon.com/product-reviews/B0HL938SDP",
  "hasReviews": true,
  "delivery": "Thursday, October 29",
  "fastestDelivery": "Wednesday, October 28",
  "isAmazonChoice": false,
  "locationText": "Delivering to Long Beach 90804 Update location",
  "loadedCountryCode": "US",
  "unNormalizedProductUrl": "https://www.amazon.com/s?k=standing+desk&s=popularity-rank",
  "price_value": 47.99,
  "price_currency": "$",
  "listPrice_value": 64.99,
  "starsBreakdown_5star": 0.75,
  "starsBreakdown_4star": 0.15,
  "starsBreakdown_3star": 0.06,
  "starsBreakdown_2star": 0.02,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/amazon-product-search-scraper").call(run_input={
    "searchUrls": [
        "https://www.amazon.com/s?k=standing+desk"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~amazon-product-search-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchUrls": ["https://www.amazon.com/s?k=standing+desk"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/amazon-product-search-scraper` as a tool.

Full documentation, pricing and the latest changes: [Amazon Search Results Scraper - Price, Rating, Listing](https://apify.com/om_kh/amazon-product-search-scraper).

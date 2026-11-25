---
title: "Amazon Bestsellers Scraper - Best Sellers Rank, Price, Prime"
description: "Scrape any Amazon Best Sellers category: rank, title, ASIN, price, star rating, review count, Prime and Amazon's Choice flags, deal badge, category path, image and URL. No login. For product research, trends, dropshipping and competitor analysis. $10/1K best sellers, $0.50/1K from 16 Dec."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Amazon Bestsellers Scraper - Best Sellers Rank, Price, Prime

Scrape any Amazon Best Sellers category: rank, title, ASIN, price, star rating, review count, Prime and Amazon's Choice flags, deal badge, category path, image and URL. No login. For product research, trends, dropshipping and competitor analysis. $10/1K best sellers, $0.50/1K from 16 Dec.

**Run it on Apify:** [https://apify.com/om_kh/amazon-best-sellers-scraper](https://apify.com/om_kh/amazon-best-sellers-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Amazon Best Sellers category links |
| **We do** | Read the category's best-seller list |
| **You get** | One row per product: rank, title, ASIN, price, stars, review count, Prime, Amazon's Choice and deal flags, category path, image and link, plus every field the supplier returns (`source_data`) |
| **It costs** | $10 per 1,000 products today, $0.50 per 1,000 from 16 December 2026 + $0.001 per run. Optional scheduled monitoring: +$0.20 per check today, $0.005 from 16 December 2026 (one-off runs never pay it). Apify also bills the supplier Actor `santamaria-automations/amazon-bestsellers-scraper` that this robot runs for you, at its own price (about $1 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Amazon or give sales numbers |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `categoryUrls` | array | Amazon Best Sellers category URLs to monitor for new entrants. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "https://www.amazon.com/dp/B08JHCVHTY",
  "query_id": "https://www.amazon.com/Best-Sellers-Electronics/zgbs/electronics",
  "title": "blink plus plan with monthly auto-renewal",
  "url": "https://www.amazon.com/dp/B08JHCVHTY",
  "score": 1,
  "asin": "B08JHCVHTY",
  "marketplace": "US",
  "categoryName": "Best Sellers in Electronics",
  "categoryBreadCrumbs": [
    "Electronics"
  ],
  "listType": "bestseller",
  "thumbnailImage": "https://images-na.ssl-images-amazon.com/images/I/31YHGbJsldL._AC_UL300_SR300,200_.png",
  "stars": 4.4,
  "reviewsCount": 281429,
  "isAmazonChoice": false,
  "isPrime": false,
  "isLimitedDeal": false,
  "scrapedAt": "2026-10-24T18:59:26Z",
  "price_value": 11.99,
  "price_currency": "$",
  "price_raw": "$11.99"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/amazon-best-sellers-scraper").call(run_input={
    "categoryUrls": [
        "https://www.amazon.com/Best-Sellers-Electronics/zgbs/electronics"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~amazon-best-sellers-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"categoryUrls": ["https://www.amazon.com/Best-Sellers-Electronics/zgbs/electronics"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/amazon-best-sellers-scraper` as a tool.

Full documentation, pricing and the latest changes: [Amazon Bestsellers Scraper - Best Sellers Rank, Price, Prime](https://apify.com/om_kh/amazon-best-sellers-scraper).

---
title: "Amazon Price & Stock Scraper - Price, Stock, Drops"
description: "Get the current price and stock status for a list of Amazon ASINs or Shopify products: price, availability, store and product URL. Run it on a schedule to build a price history and catch drops and restocks. For sellers and deal hunters. $10 per 1,000 products, $0.50 from 30 Nov 2026."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Amazon Price & Stock Scraper - Price, Stock, Drops

Get the current price and stock status for a list of Amazon ASINs or Shopify products: price, availability, store and product URL. Run it on a schedule to build a price history and catch drops and restocks. For sellers and deal hunters. $10 per 1,000 products, $0.50 from 30 Nov 2026.

**Run it on Apify:** [https://apify.com/om_kh/amazon-price-stock-tracker](https://apify.com/om_kh/amazon-price-stock-tracker) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Amazon ASINs or Shopify product links |
| **We do** | Read each product's current price and stock, and compare with your last run |
| **You get** | One row per product: name, price, in stock or not, store, link, and what changed (price drop, restock), plus every field the supplier returns (`source_data`) |
| **It costs** | **$10 per 1,000 products** ($0.01 each) until 29 November 2026, **$0.50 per 1,000 from 30 November 2026** ($0.0005 each), no start fee. Optional scheduled monitoring: +$0.30 per check until 29 November, +$0.005 from 30 November (one-off runs never pay it). Apify also bills the supplier Actor `delicious_zebu/amazon-product-details-scraper` that this robot runs for you, at its own price ($2.50 per 1,000 products on the free plan, $1.50 on paid plans). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Amazon or buy anything. A price history builds up only if you run it on a schedule |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `productUrls` | array | Public product page URLs to read. |
| `shopifyStores` | array | Shopify store domains (e.g. https://shop.example). |
| `amazonAsins` | array | Amazon product ASINs to track (price, stock and Best Sellers Rank). |
| `previousProducts` | array | Products from the prior run; used to return only what changed. |
| `currentProducts` | array | Products you supply directly (product_id, name, price, in_stock). |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Public product page", "authorization": "public_st`. |

## Example output

A row as shown in the Actor's README:

```json
{
  "product_id": "allbirds-slipper:41268090306640",
  "name": "(hidden here)",
  "price": 75,
  "in_stock": true,
  "source_url": "https://allbirds.com/products/allbirds-slipper",
  "source": "shopify",
  "record_id": "allbirds-slipper:41268090306640",
  "change_type": "new",
  "why_it_matters": "A tracked item changed."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/amazon-price-stock-tracker").call(run_input={
    "shopifyStores": [
        "allbirds.com"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~amazon-price-stock-tracker/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"shopifyStores": ["allbirds.com"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/amazon-price-stock-tracker` as a tool.

Full documentation, pricing and the latest changes: [Amazon Price & Stock Scraper - Price, Stock, Drops](https://apify.com/om_kh/amazon-price-stock-tracker).

---
title: "Etsy Listings Scraper - Price, Stock, Ratings"
description: "Scrape Etsy shops and listings: title, price range, currency, stock, rating, review count, variants, category, description, images and shop. Export to JSON, CSV or Excel, or use the API, n8n or Make. No login. For pricing research and product ideas. $7 per 1,000 listings, $1.75 from 16 Dec 2026."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Etsy Listings Scraper - Price, Stock, Ratings

Scrape Etsy shops and listings: title, price range, currency, stock, rating, review count, variants, category, description, images and shop. Export to JSON, CSV or Excel, or use the API, n8n or Make. No login. For pricing research and product ideas. $7 per 1,000 listings, $1.75 from 16 Dec 2026.

**Run it on Apify:** [https://apify.com/om_kh/etsy-listings-scraper](https://apify.com/om_kh/etsy-listings-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Etsy shop or listing links |
| **We do** | Read each listing, and compare with your last run |
| **You get** | One row per listing: title, price range, currency, stock, rating, review count, variants, category, description, images and shop, plus every field the supplier returns (`source_data`) |
| **It costs** | $7 per 1,000 listings today, $1.75 per 1,000 from 16 December 2026 + $0.001 per run. Optional scheduled monitoring: +$0.35 per check today, $0.005 from 16 December 2026 (one-off runs never pay it). Apify also bills the supplier Actor `cirkit/etsy-shop-product-scraper` that this robot runs for you, at its own price (about $3.50 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Etsy or buy anything |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `shopNames` | array | Etsy shop names (as they appear in the shop URL) to monitor. |
| `currentProducts` | array | Skip the chained Etsy fetch and pass listing data directly. |
| `previousProducts` | array | Listings from the prior run; used to identify changes when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum this run may charge for listing alerts. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Etsy Open API actor", "authorization": "p`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "shop_rating": 5,
  "shop_review_count": 753206,
  "shop_owner": "Kate",
  "shop_slogan": "Custom Jewelry & More, Crafted with Love ♡",
  "shop_logo": "https://i.etsystatic.com/10204022/r/isla/883ac2/88813489/isla_500x500.88813489_7nbtt4gg.jpg",
  "shop_total_listings": 2479,
  "shop_description": "Shop Custom Jewelry & More, Crafted with Love ♡ by CaitlynMinimalist located in Los Angeles, California.",
  "product_id": "1016875279",
  "name": "(hidden here)",
  "price": 31.5,
  "currency": "USD",
  "in_stock": true,
  "source_url": "https://www.etsy.com/listing/1016875279/duo-bead-chain-bracelet-perfect-birthday",
  "source": "etsy",
  "shop_name": "CaitlynMinimalist",
  "recordType": "listing",
  "sourceUrl": "https://www.etsy.com/listing/1016875279/duo-bead-chain-bracelet-perfect-birthday",
  "listingId": "1016875279",
  "title": "Duo Bead Chain Bracelet by Caitlyn Minimalist • Dainty Gold Bracelet • Fine Beaded Chain Bracelet • Birthday Gifts for Women • BR016",
  "description": "D U O • B E A D • C H A I N • B R A C E L E T\n\nCelebrate her style with our perfectly boho Duo Bead Chain Bracelet – an ideal birthday gi...",
  "priceLow": 31.5,
  "priceHigh": 31.5,
  "priceCurrency": "USD",
  "availability": "https://schema.org/InStock",
  "variantCount": 1,
  "ratingValue": 4.8,
  "reviewCount": 2120,
  "images": [
    "https://i.etsystatic.com/10204022/r/il/0feaed/8286972144/il_fullxfull.8286972144_egg0.jpg",
    "https://i.etsystatic.com/10204022/r/il/e6d66c/8333520929/il_fullxfull.8333520929_1x90.jpg"
  ],
  "category": "Jewelry < Bracelets < Chain & Link Bracelets",
  "breadcrumbs": [
    "Jewelry",
    "Bracelets"
  ],
  "shopId": "10204022",
  "shopName": "CaitlynMinimalist",
  "shopUrl": "https://www.etsy.com/shop/CaitlynMinimalist",
  "scrapedAt": "2026-10-26T18:12:33Z",
  "record_id": "1016875279",
  "change_type": "new",
  "why_it_matters": "A tracked item changed."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/etsy-listings-scraper").call(run_input={
    "shopNames": [
        "CaitlynMinimalist",
        "ModParty"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~etsy-listings-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"shopNames": ["CaitlynMinimalist", "ModParty"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/etsy-listings-scraper` as a tool.

Full documentation, pricing and the latest changes: [Etsy Listings Scraper - Price, Stock, Ratings](https://apify.com/om_kh/etsy-listings-scraper).

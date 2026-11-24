---
title: "Coles Scraper - Australia Prices, Specials, Barcodes"
description: "Scrape Coles supermarket (Australia): shelf price, was-price, specials, unit price, availability, aisle. Search, aisles, specials page, links, per-store prices, barcode, ingredients, nutrition. No login. $1 per 1,000 products ($3 from Dec 10), no start fee."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Coles Scraper - Australia Prices, Specials, Barcodes

Scrape Coles supermarket (Australia): shelf price, was-price, specials, unit price, availability, aisle. Search, aisles, specials page, links, per-store prices, barcode, ingredients, nutrition. No login. $1 per 1,000 products ($3 from Dec 10), no start fee.

**Run it on Apify:** [https://apify.com/om_kh/coles-australia-scraper](https://apify.com/om_kh/coles-australia-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Searches, aisles, Coles links, product IDs, or the whole specials page |
| **We do** | Read Coles (Australia) for the store you choose |
| **You get** | One row per product: shelf price, was-price, special, unit price, availability and aisle; option: barcode (EAN), ingredients, allergens and nutrition |
| **It costs** | $1 per 1,000 products, $3 per 1,000 with details, no start fee. From 10 December 2026: $3 per 1,000 with or without details. The first 10 products of every run are free; a page that still fails after retries is never charged. No supplier fee |
| **It does not** | Search by barcode, or return more than 4,800 products per search or aisle (use sub-aisles or the whole-catalogue option) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchTerms` | array | What you would type in the Coles search box, one per line (milk, vegemite, dog food...). Default: `["milk", "vegemite"]`. |
| `categories` | array | Aisle paths or links, for example dairy-eggs-fridge/milk or https://www.coles.com.au/browse/pantry. |
| `urls` | array | Paste any coles.com.au link: a product, a search, an aisle or the specials page. |
| `productIds` | array | Coles product numbers, one per line. |
| `specials` | string | 'none' returns normal listings. 'all' returns only products on special; half price, multi-buy and online-only narrow it. Default: `"none"`. |
| `wholeCatalogue` | boolean | Reads every main aisle (about 30,000 products). Default: `false`. |
| `listCategories` | boolean | Also returns the full aisle tree (about 1,500 aisles with their paths and product counts). Default: `false`. |
| `maxProductsPerInput` | integer | Per search, aisle or link. 1 to 100,000. Default: `100`. |
| `storeId` | string | Prices and specials of one store. |
| `sortBy` | string | Order of the results inside each search or aisle. Default: `"relevance"`. |
| `brands` | array | Keep only these brands, for example Cadbury. |
| `dietary` | array | For example Vegan, Vegetarian, Halal, GMO Free. |
| `allergens` | array | For example Gluten Free, Dairy Free, Egg Free. |
| `minPrice` | number | Keep products at or above this shelf price. |
| `maxPrice` | number | Keep products at or below this shelf price. |
| `minDiscountPercent` | number | Keep only products at least this much below their was-price (50 = half price or better). |
| `inStockOnly` | boolean | Skip products Coles marks as unavailable. Default: `false`. |
| `includeSponsored` | boolean | Coles mixes paid placements into search results. Default: `true`. |
| `includeDetails` | boolean | Opens every product page for its barcode (EAN), ingredients, allergens, dietary tags, storage, country of origin, dimensions and the full nutrition table. Default: `false`. |
| `maxTotalChargeUsd` | number | The run stops before it would spend more than this. Default: `1`. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "productId": "1902465",
  "name": "(hidden here)",
  "brand": "Pauls",
  "size": "2L",
  "description": "PAULS ZYMIL LACTOSE FREE LOW FAT MILK 2L",
  "url": "https://www.coles.com.au/product/pauls-zymil-lactose-free-low-fat-milk-2l-1902465",
  "imageUrl": "https://cdn.productimages.coles.com.au/productimages/1/1902465.jpg",
  "price": 5.95,
  "wasPrice": 6.9,
  "savings": 0.95,
  "savingsPercent": 13.8,
  "unitPrice": 2.98,
  "unitMeasure": "1l",
  "unitPriceText": "$2.98/ 1L",
  "isWeighted": false,
  "isOnSpecial": true,
  "promotionType": "SPECIAL",
  "onlineOnlySpecial": false,
  "isAvailable": true,
  "availabilityType": "InStoreAndOnline",
  "availableQuantity": 147,
  "purchaseLimit": 20,
  "promotionalLimit": 12,
  "ageRestricted": false,
  "isSponsored": true,
  "isFeatured": true,
  "category": "Milk",
  "department": "Dairy, Eggs & Fridge",
  "aisle": "Specialty Milk",
  "categoryId": "8881800",
  "categories": [
    {
      "department": "Dairy, Eggs & Fridge",
      "category": "Milk",
      "aisle": "Specialty Milk",
      "categoryId": "8881800",
      "aisleId": "8881805"
    },
    {
      "department": "Health & Dietary",
      "category": "Free From",
      "aisle": "Dairy & Lactose Free",
      "categoryId": "674114623",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/coles-australia-scraper").call(run_input={
    "searchTerms": [
        "milk",
        "vegemite"
    ],
    "maxProductsPerInput": 100,
    "maxTotalChargeUsd": 0.5
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~coles-australia-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["milk", "vegemite"], "maxProductsPerInput": 100, "maxTotalChargeUsd": 0.5}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/coles-australia-scraper` as a tool.

Full documentation, pricing and the latest changes: [Coles Scraper - Australia Prices, Specials, Barcodes](https://apify.com/om_kh/coles-australia-scraper).

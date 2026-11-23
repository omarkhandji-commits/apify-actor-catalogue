---
title: "11st (11번가) Korea Product Scraper - Prices, Sales $0.90/1K"
description: "Scrape 11st (11번가), a top South Korean marketplace: price in won, list price, discount, brand, seller, sales count, rating, delivery, sold-out and lowest-price flags. Search in Korean or English. No login. $0.90 per 1,000 products."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# 11st (11번가) Korea Product Scraper - Prices, Sales $0.90/1K

Scrape 11st (11번가), a top South Korean marketplace: price in won, list price, discount, brand, seller, sales count, rating, delivery, sold-out and lowest-price flags. Search in Korean or English. No login. $0.90 per 1,000 products.

**Run it on Apify:** [https://apify.com/om_kh/11st-korea-product-scraper](https://apify.com/om_kh/11st-korea-product-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Search words in Korean or English, or 11st search links |
| **We do** | Read 11st (11번가) search results, logged out |
| **You get** | One row per product: price in won, list price, discount, brand, seller, sales count, rating, review count, delivery, sold-out and lowest-price flags |
| **It costs** | $0.90 per 1,000 products + $0.001 per run. The first 10 products of every run are free; searches with no product and 11st outages are not charged. No supplier fee |
| **It does not** | Include card or membership discounts, or open product pages |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchTerms` | array | What you would type in the 11st search box, one per line. Default: `["노트북", "선크림"]`. |
| `searchUrls` | array | Paste 11st search result links (search.11st.co.kr/...?kwd=...); the search words are read from the link. |
| `maxProductsPerSearch` | integer | Unique products per search (ads and repeats removed). 11st serves about 100 new products per page. Default: `100`. |
| `sortBy` | string | The same orders as the 11st sort menu. Default: `"ranking"`. |
| `minPrice` | integer | Only products at or above this price in won. |
| `maxPrice` | integer | Only products at or below this price in won. |
| `includeSponsored` | boolean | Keep products 11st shows as ads. Default: `true`. |
| `maxTotalChargeUsd` | number | The run stops delivering once this amount is reached; you are never charged more. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "productId": "8891421723",
  "title": "[최종134만]삼성 갤럭시북5 NT750XHW-A51A 16GB 256GB 가성비노트북 대학생 추천노트북",
  "url": "https://www.11st.co.kr/products/8891421723",
  "price": 1499000,
  "originalPrice": 1594680,
  "discountPercent": 5,
  "currency": "KRW",
  "brand": "삼성전자",
  "sellerName": "삼성Mall",
  "sellerUrl": "https://shop.11st.co.kr/stores/1188",
  "isOfficialSeller": true,
  "salesCount": 1458,
  "rating": 4.6,
  "reviewCount": 66,
  "deliveryText": "무료",
  "shipsToday": false,
  "isSoldOut": false,
  "isLowestPrice11st": true,
  "isLowestPrice30Days": false,
  "isSponsored": true,
  "listingType": "OFFICIAL_SELLER_AD",
  "imageUrl": "https://cdn.011st.com/11dims/resize/248/11src/product/8891421723/B.webp",
  "position": 6,
  "searchTerm": "노트북",
  "sortBy": "ranking",
  "type": "product"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/11st-korea-product-scraper").call(run_input={
    "searchTerms": [
        "노트북",
        "선크림"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~11st-korea-product-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["노트북", "선크림"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/11st-korea-product-scraper` as a tool.

Full documentation, pricing and the latest changes: [11st (11번가) Korea Product Scraper - Prices, Sales $0.90/1K](https://apify.com/om_kh/11st-korea-product-scraper).

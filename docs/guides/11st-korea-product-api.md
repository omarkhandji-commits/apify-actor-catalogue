---
title: "11st (11번가) Korea Product Prices API — Sellers, Sales, Ratings"
description: "Get product prices, sellers, sales counts and ratings from 11st, a top South Korean marketplace, as JSON or CSV for any search. No login."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# 11st (11번가) Korea Product Prices API — Sellers, Sales, Ratings

## How do I get 11st (11번가) Korea product prices with an API?

Use the **11st Korea Product Scraper**. Give it search words in Korean or English (노트북, 선크림, dyson), pick a sort
(ranking, popular, lowest price, highest price, best selling, most reviews, newest) and an optional price range in won.
It returns one row per unique product: price in won, list price, discount, brand, seller, sales count, rating, review
count, delivery text, sold-out, "11st lowest price" and "30-day low" flags, image and link. Ads are flagged or removed.
$4 per 1,000 products, the first 10 of every run free. No login, no Korean proxy to set up.

**Try it:** [11st Korea Product Scraper on Apify](https://apify.com/om_kh/11st-korea-product-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [11st Korea Product Scraper](https://apify.com/om_kh/11st-korea-product-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "searchTerms": ["선크림", "dyson"],
  "maxProductsPerSearch": 200,
  "sortBy": "best_selling",
  "includeSponsored": false
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/11st-korea-product-scraper").call(run_input={
    "searchTerms": ["선크림", "dyson"],
    "maxProductsPerSearch": 200,
    "sortBy": "best_selling",
    "includeSponsored": False,
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item["title"], item["price"], item.get("salesCount"), item.get("rating"))
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~11st-korea-product-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>"   -H "Content-Type: application/json"   -d '{"searchTerms": ["노트북"], "maxProductsPerSearch": 50, "sortBy": "lowest_price"}'
```

## What one row looks like

Real row, read on 15 October 2026 (search 선크림, sort best selling):

```json
{
  "productId": "1085982197",
  "title": "본트리 베리 에센스 선 블럭 50ml(SPF50+) 3개",
  "url": "https://www.11st.co.kr/products/1085982197",
  "price": 22900,
  "originalPrice": 24000,
  "discountPercent": 4,
  "currency": "KRW",
  "brand": "본트리",
  "isOfficialSeller": true,
  "salesCount": 18060,
  "rating": 4.5,
  "reviewCount": 3952,
  "deliveryText": "무료",
  "shipsToday": true,
  "isLowestPrice11st": true,
  "isSponsored": false,
  "position": 1
}
```

## What people use it for

- Price monitoring of products sold in Korea, yours and your competitors'.
- Market research before entering Korea: price bands, best sellers, official brand stores.
- Cross-border sourcing: compare 11st with Naver Shopping, Coupang or your own shop.
- Brand protection: who sells your brand on 11st and at what price.

## Price

$0.004 per product ($4 per 1,000), no start fee, first 10 products of every run free. Searches with no product and 11st
outages are never charged. Paid Apify plans get lower tier prices.

## Questions

**Do I need a Korean account or proxy?** No. It reads 11st's public search results, logged out.

**Can I search in English?** Yes for brands and models; Korean words return far more for generic products.

**Can an AI agent use it?** Yes, through the Apify MCP server (`https://mcp.apify.com`) as `om_kh/11st-korea-product-scraper`.

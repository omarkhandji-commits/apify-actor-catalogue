---
title: "AliExpress (速卖通) Image Search - Find Products by Photo"
description: "AliExpress product finder by photo: upload a product image, get matching AliExpress listings with title, price, seller and product link. Each match comes with its source URL. One bad image never kills the batch, zero matches are never billed. Our fee $0.003 per match + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# AliExpress (速卖通) Image Search - Find Products by Photo

AliExpress product finder by photo: upload a product image, get matching AliExpress listings with title, price, seller and product link. Each match comes with its source URL. One bad image never kills the batch, zero matches are never billed. Our fee $0.003 per match + supplier.

**Run it on Apify:** [https://apify.com/om_kh/visual-product-matcher](https://apify.com/om_kh/visual-product-matcher) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Links to product photos |
| **We do** | Search AliExpress by image and keep the matching listings |
| **You get** | One row per match: product title, link, price, currency, seller and why it matched, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.003 per match (since 21 Nov 2026; was $0.015) + $0.002 per image + $0.001 per run. Apify also bills the supplier Actor `freecamp008/aliexpress-search-by-image-actor` that this robot runs for you, at its own price (about $1.50 per 1,000 results). An item that returns an error is never charged |
| **It does not** | Sign in to AliExpress, open product pages for variants or reviews, or place orders |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `imageUrls` | array | Public image URLs to search for matching products. Default: `["https://ae-pic-a1.aliexpress-media.com/kf/S5533347f600b47f`. |
| `marketplaces` | array | Only 'aliexpress' is implemented right now. Default: `["aliexpress"]`. |
| `maxMatchesPerImage` | integer | Stop after this many matches per image. Default: `10`. |
| `maxImages` | integer | Stop after this many images. Default: `20`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only images not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "input_image_url": "https://ae-pic-a1.aliexpress-media.com/kf/S5533347f600b47ff9ae5abbd74255026M.jpg_220x220q75.jpg_.avif",
  "matches": [
    {
      "title": "Men's New USB Chest Bag Portable Large Capacity Charging Casual Crossbody Bag Outdoor Sports PU Chest Bag",
      "product_url": "https://imagesearchaliexpress.com/product?token=1ba2ad0ba5fdc002f62d3b87323c63f87fc720252c47df459cd65a33367357df78a9bc32253703b54adc555eb...",
      "marketplace": "aliexpress",
      "price": 4.79,
      "currency": "CNY",
      "seller": "1105418430",
      "match_basis": "visually_similar",
      "image_url": "https://ae-pic-a1.aliexpress-media.com/kf/Sdc00fbd20aac4525becd6a319200a122g.jpg",
      "images": [
        "https://ae-pic-a1.aliexpress-media.com/kf/Sdc00fbd20aac4525becd6a319200a122g.jpg",
        "https://ae-pic-a1.aliexpress-media.com/kf/S99442aa2da8941f6a475906815a547eck.jpg"
      ],
      "original_price": 16.58,
      "sale_price": 4.79,
      "discount_pct": 71.1,
      "orders": "1",
      "wishlist_adds": 0,
      "category_id": "1524"
    },
    {
      "title": "Simple and Fashionable Casual Solid Color PU Multifunctional USB Charging Zipper MEN'S Chest Bag Crossbody Bag for Commuting",
      "product_url": "https://imagesearchaliexpress.com/product?token=1ba2ad0ba5fdc002f62d3b87323c63f87fc720252c47df459cd65a33367357df8815b3fae1bcf441d5f0c10cc...",
      "marketplace": "aliexpress",
      "price": 1.86,
      "currency": "CNY",
      "seller": "1105369212",
      "match_basis": "visually_similar",
      "image_url": "https://ae-pic-a1.aliexpress-media.com/kf/S8df78d5ca6334ed2a5716cdd6204f482x.jpg",
      "images": [
        "https://ae-pic-a1.aliexpress-media.com/kf/S8df78d5ca6334ed2a5716cdd6204f482x.jpg",
        "https://ae-pic-a1.aliexpress-media.com/kf/S18a12fae1aeb46a7a04da697c6ffe130v.jpg"
      ],
      "original_price": 15.65,
      "sale_price": 1.86,
      "discount_pct": 88.1,
      "rating": 2.5,
      "orders": "14",
      "wishlist_adds": 0
    }
  ]
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/visual-product-matcher").call(run_input={
    "imageUrls": [
        "https://ae-pic-a1.aliexpress-media.com/kf/S5533347f600b47ff9ae5abbd74255026M.jpg_220x220q75.jpg_.avif"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~visual-product-matcher/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"imageUrls": ["https://ae-pic-a1.aliexpress-media.com/kf/S5533347f600b47ff9ae5abbd74255026M.jpg_220x220q75.jpg_.avif"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/visual-product-matcher` as a tool.

Full documentation, pricing and the latest changes: [AliExpress (速卖通) Image Search - Find Products by Photo](https://apify.com/om_kh/visual-product-matcher).

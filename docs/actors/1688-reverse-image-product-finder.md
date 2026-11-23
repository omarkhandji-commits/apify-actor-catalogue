---
title: "1688 Reverse Image Search (阿里巴巴) - Find Suppliers by Photo"
description: "1688 reverse image search: 1688 supplier finder by product photo: upload an image, get matching 1688 listings with SKU, variant price, MOQ and supplier shop. One bad photo never kills the batch, and zero matches are never billed. Our fee $0.012 per match + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# 1688 Reverse Image Search (阿里巴巴) - Find Suppliers by Photo

1688 reverse image search: 1688 supplier finder by product photo: upload an image, get matching 1688 listings with SKU, variant price, MOQ and supplier shop. One bad photo never kills the batch, and zero matches are never billed. Our fee $0.012 per match + supplier.

**Run it on Apify:** [https://apify.com/om_kh/1688-reverse-image-product-finder](https://apify.com/om_kh/1688-reverse-image-product-finder) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Links to product photos |
| **We do** | Search 1688 by image and check each matching supplier |
| **You get** | One row per match (the Matches table view lists each product on its own line): price range in CNY and USD, minimum order quantity (MOQ), price per quantity tier, units sold, repeat-buyer rate, supplier name, type, city, province, years on 1688, score and factory audit, the factory link and the source page behind every match, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.012 per match (**$0.0035 from 3 December 2026**) + $0.002 per image + $0.001 per supplier check, + $0.001 per run. Apify also bills the supplier Actor this robot runs for you, at its own price (about $1.40 per 1,000 matches with 10 matches per photo, read on 2026-11-10; **about $2.35 from 25 November 2026**, when it starts billing the English title). The first 3 results of every run are free of this robot's fee; an item that returns an error is never charged |
| **It does not** | Sign in to 1688, place orders or contact sellers |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `imageUrls` | array | Public product photo URLs to search on 1688. Default: `["https://ae-pic-a1.aliexpress-media.com/kf/S5533347f600b47f`. |
| `maxMatchesPerImage` | integer | Stop after this many matches per image. Default: `10`. |
| `includeSupplier` | boolean | Include shop name, years on 1688, business type, factory inspection, shop score and location. Default: `true`. |
| `includeVariants` | boolean | Include min/max variant price and MOQ. Default: `true`. |
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
      "product_url": "https://detail.1688.com/offer/1008770205481.html",
      "title": "跨境热销亚马逊热卖USB充电胸包休闲时尚单肩背包PU男士胸包批发",
      "title_en": "Cross-border hot selling Amazon hot selling USB charging chest bag casual fashion shoulder bag PU men's chest bag wholesale",
      "image_url": "https://cbu01.alicdn.com/img/ibank/O1CN01C957yT1HsrVos6eUd_!!2220848340814-0-cib.jpg",
      "units_sold": 5620,
      "repurchase_rate": 53,
      "is_ad": false,
      "price_range": {
        "price_min": 7,
        "price_max": 8,
        "currency": "CNY",
        "price_min_usd": 1.05,
        "price_max_usd": 1.2,
        "usd_rate": 0.14992,
        "moq": 1,
        "price_tiers": [
          {
            "minQuantity": 1,
            "maxQuantity": 19,
            "price": 8,
            "priceUsd": 1.2
          },
          {
            "minQuantity": 20,
            "maxQuantity": 4999,
            "price": 7.5,
            "priceUsd": 1.12
          }
        ]
      },
      "supplier": {
        "name": "(hidden here)",
        "years_active": 2,
        "url": "https://m.1688.com/winport/b2b-222084834081487a3e.html",
        "type": "manufacturer",
        "province": "河北",
        "city": "保定市",
        "score": 4,
        "factory_audited": false
      },
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/1688-reverse-image-product-finder").call(run_input={
    "imageUrls": [
        "https://ae-pic-a1.aliexpress-media.com/kf/S5533347f600b47ff9ae5abbd74255026M.jpg_220x220q75.jpg_.avif"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~1688-reverse-image-product-finder/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"imageUrls": ["https://ae-pic-a1.aliexpress-media.com/kf/S5533347f600b47ff9ae5abbd74255026M.jpg_220x220q75.jpg_.avif"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/1688-reverse-image-product-finder` as a tool.

Full documentation, pricing and the latest changes: [1688 Reverse Image Search (阿里巴巴) - Find Suppliers by Photo](https://apify.com/om_kh/1688-reverse-image-product-finder).

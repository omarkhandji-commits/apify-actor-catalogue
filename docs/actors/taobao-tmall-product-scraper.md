---
title: "Taobao 淘宝 & Tmall 天猫 Product Detail Scraper - Real Price"
description: "Taobao and Tmall product detail scraper: price, every SKU variant with stock, photos and shop, in a cheaper Fast mode or a Full mode with the verified post-coupon price, units sold and specs. Our fee $5 per 1,000 products + supplier. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Taobao 淘宝 & Tmall 天猫 Product Detail Scraper - Real Price

Taobao and Tmall product detail scraper: price, every SKU variant with stock, photos and shop, in a cheaper Fast mode or a Full mode with the verified post-coupon price, units sold and specs. Our fee $5 per 1,000 products + supplier. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/taobao-tmall-product-scraper](https://apify.com/om_kh/taobao-tmall-product-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Taobao or Tmall product links or item IDs |
| **We do** | Read each product, in Fast mode (default, cheaper) or Full mode (also checks the real price after coupons) |
| **You get** | One row per product. Fast: title, price, every SKU (variant) with its price and stock, total stock, photos and description images, shop name. Full adds the real post-coupon price (or an honest `price_verified: false`), brand, Tmall flag, specifications, category, units sold, ship-from city, shipping fee, seller and shop ids. Every row also has every field the supplier returns (`source_data`) |
| **It costs** | $0.005 per product + $0.002 per SKU variant + $0.001 per verified coupon price, + $0.001 per run from Nov 26, 2026 (no start fee before). Apify also bills the supplier Actor this robot runs for you, at its own price: `memo23/taobao-scraper` in Fast mode (about $4 per 1,000 products + $0.005 per batch of up to 20), `zen-studio/taobao-detail-scraper` in Full mode (about $9.99 per 1,000 + $0.009 per batch). An item that returns an error is never charged |
| **It does not** | Pass the list price off as the final price, sign in, or place orders |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `productUrls` | array | Taobao or Tmall product URLs to verify. Default: `["https://item.taobao.com/item.htm?id=1022020209623"]`. |
| `itemIds` | array | Numeric Taobao/Tmall item IDs, if you have them instead of URLs. |
| `detailLevel` | string | Fast (default) reads the product through memo23/taobao-scraper, about $4 per 1,000 products on your Apify account. Default: `"fast"`. |
| `includeVariants` | boolean | Include per-SKU price, stock, and attributes. Default: `true`. |
| `includeReviews` | boolean | Include a review count summary where available. Default: `false`. |
| `resolveCouponPrice` | boolean | Full detail level only: attempt to resolve the real post-coupon price. Default: `true`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only products not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "item_id": "1022020209623",
  "product_url": "https://item.taobao.com/item.htm?id=1022020209623",
  "title": "影视飓风Luna Case光层手机保护壳Pan's iPhone17Pro Max苹果17防摔壳",
  "list_price": "111.97",
  "coupon_price": "70.88",
  "price_verified": true,
  "currency": "CNY",
  "variants": [
    {
      "sku_id": "6149580248924",
      "attrs": "228680323:44406893537:适用手机型号:iPhone 18 Pro;1627207:42382854961:颜色分类:清透几何",
      "price": "111.97",
      "stock": 200
    },
    {
      "sku_id": "6149580248929",
      "attrs": "228680323:44406893537:适用手机型号:iPhone 18 Pro;1627207:44732969302:颜色分类:立体蓝图-白透",
      "price": "111.97",
      "stock": 200
    }
  ],
  "seller": {
    "name": "(hidden here)",
    "url": "https://shop446768788.taobao.com/"
  },
  "shop_url": "https://shop446768788.taobao.com/",
  "stock": 1200
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/taobao-tmall-product-scraper").call(run_input={
    "productUrls": [
        "https://item.taobao.com/item.htm?id=1022020209623"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~taobao-tmall-product-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"productUrls": ["https://item.taobao.com/item.htm?id=1022020209623"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/taobao-tmall-product-scraper` as a tool.

Full documentation, pricing and the latest changes: [Taobao 淘宝 & Tmall 天猫 Product Detail Scraper - Real Price](https://apify.com/om_kh/taobao-tmall-product-scraper).

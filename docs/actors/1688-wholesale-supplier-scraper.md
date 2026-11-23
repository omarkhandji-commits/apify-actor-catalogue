---
title: "1688 (阿里巴巴) Wholesale Supplier Scraper - Factory or Trader"
description: "Scrape 1688 wholesale products by keyword or URL: real MOQ price tiers, supplier details and a factory-or-trader verdict, each backed by its source URL. Export to JSON, CSV or Excel, or call it as an API. Our fee $0.0028 per product + supplier. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# 1688 (阿里巴巴) Wholesale Supplier Scraper - Factory or Trader

Scrape 1688 wholesale products by keyword or URL: real MOQ price tiers, supplier details and a factory-or-trader verdict, each backed by its source URL. Export to JSON, CSV or Excel, or call it as an API. Our fee $0.0028 per product + supplier. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/1688-wholesale-supplier-scraper](https://apify.com/om_kh/1688-wholesale-supplier-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | 1688 product links, or product keywords such as `phone case` |
| **We do** | Read each product's wholesale offer and check the seller with evidence, never a guess |
| **You get** | One row per product: the real price for each minimum order quantity (MOQ) and whether the seller is a factory or a trader, with the proof, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.0028 per product (since 21 Nov 2026; was $0.012) + $0.002 per verified supplier + $0.0008 per price tier, + $0.001 per run. Apify also bills the supplier Actor this robot runs for you, at its own price (about $4.99 per 1,000 results). The first 3 results of every run are free of this robot's fee; an item that returns an error is never charged |
| **It does not** | Sign in to 1688, place orders or contact sellers |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `productUrls` | array | 1688 product URLs to fetch. |
| `keywords` | array | Product or supplier keywords, if you don't have exact URLs. Default: `["phone case"]`. |
| `supplierUrls` | array | 1688 supplier/shop URLs, if you have them. |
| `includePriceTiers` | boolean | Include minimum-order-quantity price tiers. Default: `true`. |
| `includeSupplierType` | boolean | Include a factory-or-trader verdict with its evidence basis. Default: `true`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only products not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/1688-wholesale-supplier-scraper").call(run_input={
    "keywords": [
        "phone case"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~1688-wholesale-supplier-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["phone case"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/1688-wholesale-supplier-scraper` as a tool.

Full documentation, pricing and the latest changes: [1688 (阿里巴巴) Wholesale Supplier Scraper - Factory or Trader](https://apify.com/om_kh/1688-wholesale-supplier-scraper).

---
title: "eBay Sold Listing Prices Scraper - Sold Price, Date, Title"
description: "eBay sold listing prices scraper: scrape completed eBay sales for any search: sold price, shipping, condition, sale date, listing type and URL. Real transaction prices, not asking prices. No login needed. For resellers, pricing research and market valuation. $10 per 1,000 listings."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# eBay Sold Listing Prices Scraper - Sold Price, Date, Title

eBay sold listing prices scraper: scrape completed eBay sales for any search: sold price, shipping, condition, sale date, listing type and URL. Real transaction prices, not asking prices. No login needed. For resellers, pricing research and market valuation. $10 per 1,000 listings.

**Run it on Apify:** [https://apify.com/om_kh/ebay-sold-listings-scraper](https://apify.com/om_kh/ebay-sold-listings-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | eBay searches |
| **We do** | Read eBay's completed (sold) listings, and compare with your last run |
| **You get** | One row per sale: title, sold price, shipping, total, sale date, condition, listing type, best offer accepted, seller and feedback, item ID and link |
| **It costs** | $10 per 1,000 sold listings + $0.001 per run. Optional scheduled monitoring: +$0.30 per check (one-off runs never pay it). Apify also bills the supplier Actor `caffein.dev/ebay-sold-listings` that this robot runs for you, at its own price (about $4 per 1,000 results)., so about **$14 per 1,000 in total**. The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to eBay, buy or bid. These are real sale prices, not asking prices |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchKeywords` | array | Search keywords (e.g. a product name) to monitor eBay sold listings for. |
| `currentProducts` | array | Skip the chained fetch and pass listing data directly. |
| `previousProducts` | array | Prior-run records; used to compute changes when not in persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained eBay sold-listings actor", "authorization`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |

## Example output

A row as shown in the Actor's README:

```json
{
  "product_id": "117473877410",
  "name": "(hidden here)",
  "price": 365,
  "currency": "USD",
  "in_stock": true,
  "source_url": "https://www.ebay.com/itm/117473877410?nordt=true",
  "source": "ebay",
  "search_query": "nintendo switch oled",
  "title": "Nintendo Switch Mario Red OLED 64gb Console Bundle with 9 Games 256mb SD Card",
  "soldPrice": "365.00",
  "soldCurrency": "USD",
  "shippingPrice": "9.89",
  "shippingCurrency": "USD",
  "totalPrice": "374.89",
  "endedAt": "2026-10-23",
  "itemId": "117473877410",
  "url": "https://www.ebay.com/itm/117473877410?nordt=true",
  "keyword": "nintendo switch oled",
  "categoryId": "0",
  "shippingType": "paid",
  "condition": "Pre-Owned",
  "conditionId": 3000,
  "sellerUsername": "(hidden here)",
  "sellerPositivePercent": 100,
  "sellerFeedbackPercent": 100,
  "sellerFeedbackScore": 2100,
  "scrapedAt": "2026-10-24T21:35:08.137Z",
  "updatedAt": "2026-10-24T21:35:08.194Z",
  "listingType": "auction",
  "isBestOfferAccepted": false,
  "thumbnailUrl": "https://i.ebayimg.com/images/g/avgAAeSwe8tq1WM8/s-l140.webp",
  "fullResThumbnailUrl": "https://i.ebayimg.com/images/g/avgAAeSwe8tq1WM8/s-l1600.webp",
  "buyingFormat": "auction",
  "bidCount": 14,
  "record_id": "117473877410",
  "change_type": "new",
  "why_it_matters": "A tracked item changed."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/ebay-sold-listings-scraper").call(run_input={
    "searchKeywords": [
        "nintendo switch oled",
        "dyson v15"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~ebay-sold-listings-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchKeywords": ["nintendo switch oled", "dyson v15"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/ebay-sold-listings-scraper` as a tool.

Full documentation, pricing and the latest changes: [eBay Sold Listing Prices Scraper - Sold Price, Date, Title](https://apify.com/om_kh/ebay-sold-listings-scraper).

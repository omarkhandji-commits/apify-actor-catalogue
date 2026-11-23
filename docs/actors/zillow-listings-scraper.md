---
title: "Zillow Scraper API - Listings, Zestimate, Price Cuts, ZIP"
description: "Scrape Zillow listings by search URL, ZIP code or city: address, price, beds, baths, area, lot size, status, days on Zillow, Zestimate, rent Zestimate, tax value, open house, broker and photos, with new listings and price cuts flagged. No login. $5 per 1,000 listings. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Zillow Scraper API - Listings, Zestimate, Price Cuts, ZIP

Scrape Zillow listings by search URL, ZIP code or city: address, price, beds, baths, area, lot size, status, days on Zillow, Zestimate, rent Zestimate, tax value, open house, broker and photos, with new listings and price cuts flagged. No login. $5 per 1,000 listings. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/zillow-listings-scraper](https://apify.com/om_kh/zillow-listings-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Zillow search links, ZIP codes or cities |
| **We do** | Read the listings, and compare with your last run |
| **You get** | One row per listing: address, price, beds, baths, area, lot size, status, days on Zillow, Zestimate, rent Zestimate, tax value, open house, broker and photos, with new listings and price cuts flagged, plus every field the supplier returns (`source_data`) |
| **It costs** | $5 per 1,000 listings + $0.001 per run. Optional scheduled monitoring: +$0.18 per check (one-off runs never pay it). Apify also bills the supplier Actor `scrapesmith/zillow-scraper` that this robot runs for you, at its own price (about $0.60 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Zillow or contact agents |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchUrls` | array | Paste a Zillow search URL (filters and map area included), or simply type a ZIP code (78701) or a city (Austin, TX). |
| `currentProducts` | array | Skip the chained fetch and pass listing data directly. |
| `previousProducts` | array | Prior-run listings; used to compute changes when not in persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Zillow actor", "authorization": "public_s`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "product_id": "29435237",
  "name": "(hidden here)",
  "currency": "USD",
  "in_stock": true,
  "home_status": "FOR_SALE",
  "source_url": "https://www.zillow.com/homedetails/1117-Gatehouse-Dr-Austin-TX-78753/29435237_zpid/",
  "source": "zillow",
  "zip_query": "https://www.zillow.com/homes/for_sale/?searchQueryState=%7B%22isMapVisible%22%3Atrue%2C%22mapBounds%22%3A%7B%22west%22%3A-98.0%2C%22east%...",
  "zpid": "29435237",
  "address": "1117 Gatehouse Dr, Austin, TX 78753",
  "addressStreet": "1117 Gatehouse Dr",
  "addressCity": "Austin",
  "addressState": "TX",
  "addressZipcode": "78753",
  "unformattedPrice": 361000,
  "zestimate": 366000,
  "rentZestimate": 2453,
  "beds": 3,
  "baths": 2,
  "area": 1387,
  "homeType": "SINGLE_FAMILY",
  "homeStatus": "FOR_SALE",
  "statusText": "Active",
  "daysOnZillow": 0,
  "isFeatured": false,
  "isForeclosure": false,
  "latitude": 30.385963,
  "longitude": -97.66011,
  "detailUrl": "https://www.zillow.com/homedetails/1117-Gatehouse-Dr-Austin-TX-78753/29435237_zpid/",
  "imgSrc": "https://photos.zillowstatic.com/fp/0b13c8e0ba3d8edc327ed404ffb9834a-p_e.jpg",
  "photos": [
    "https://photos.zillowstatic.com/fp/0b13c8e0ba3d8edc327ed404ffb9834a-p_e.jpg",
    "https://photos.zillowstatic.com/fp/db87942ec25692ef055906346fa19730-p_e.jpg"
  ],
  "brokerName": "Austin Bee Realty",
  "hasOpenHouse": true,
  "openHouseDate": "2026-10-25T13:00:00",
  "livingArea": 1387,
  "lotSize": 0.35109999999999997,
  "has3DModel": false,
  "hasVideo": false,
  "isZillowOwned": false,
  "isShowcaseListing": false,
  "isFeaturedListing": false,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/zillow-listings-scraper").call(run_input={
    "searchUrls": [
        "https://www.zillow.com/homes/for_sale/?searchQueryState=%7B%22isMapVisible%22%3Atrue%2C%22mapBounds%22%3A%7B%22west%22%3A-98.0%2C%22east%22%3A-97.5%2C%22south%22%3A30.1%2C%22north%22%3A30.5%7D%2C%22filterState%22%3A%7B%22sort%22%3A%7B%22value%22%3A%22days%22%7D%7D%2C%22isListVisible%22%3Atrue%7D"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~zillow-listings-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchUrls": ["https://www.zillow.com/homes/for_sale/?searchQueryState=%7B%22isMapVisible%22%3Atrue%2C%22mapBounds%22%3A%7B%22west%22%3A-98.0%2C%22east%22%3A-97.5%2C%22south%22%3A30.1%2C%22north%22%3A30.5%7D%2C%22filterState%22%3A%7B%22sort%22%3A%7B%22value%22%3A%22days%22%7D%7D%2C%22isListVisible%22%3Atrue%7D"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/zillow-listings-scraper` as a tool.

Full documentation, pricing and the latest changes: [Zillow Scraper API - Listings, Zestimate, Price Cuts, ZIP](https://apify.com/om_kh/zillow-listings-scraper).

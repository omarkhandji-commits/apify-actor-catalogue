---
title: "Redfin Search Scraper - Homes for Sale, Prices, Photos"
description: "Redfin search scraper: every home for sale in a city, county or neighborhood: price, beds, baths, sq ft, price per sq ft vs the area median, HOA, days on market, open houses, features, agent, GPS and photos. Price, size, ZIP and keyword filters. No login. $0.40 per 1,000 homes."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Redfin Search Scraper - Homes for Sale, Prices, Photos

Redfin search scraper: every home for sale in a city, county or neighborhood: price, beds, baths, sq ft, price per sq ft vs the area median, HOA, days on market, open houses, features, agent, GPS and photos. Price, size, ZIP and keyword filters. No login. $0.40 per 1,000 homes.

**Run it on Apify:** [https://apify.com/om_kh/redfin-scraper](https://apify.com/om_kh/redfin-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A Redfin city, county or neighborhood link, or home links |
| **We do** | Read every home for sale in that area, not just the first page |
| **You get** | One row per home: price, beds, baths, square feet, price per square foot against the area median, HOA, days on market, open houses, facts, description, broker, GPS and photos |
| **It costs** | **$0.40 per 1,000 homes**, + $0.001 per run from Nov 24, 2026 (no start fee before). Links that fail and homes your filters drop are never charged |
| **It does not** | Sign in to Redfin or contact agents |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchUrls` | array | Open Redfin, search a city, county, neighborhood or ZIP code and paste the link, for example https://www.redfin.com/city/30818/TX/Austin or https://www.redfin.com/zipcode/78701. Default: `["https://www.redfin.com/city/30818/TX/Austin"]`. |
| `maxHomesPerSearch` | integer | Stops after this many homes per link (after your filters). Default: `200`. |
| `maxResults` | integer | Alias of 'Max homes per search' for people coming from other Redfin scrapers. |
| `maxPhotos` | integer | How many full-size photo links to return for each home, 0 to 100. Default: `5`. |
| `sort` | string | Order Redfin returns the homes in. Default: `"recommended"`. |
| `minPrice` | integer | Leave empty for no minimum. |
| `maxPrice` | integer | Leave empty for no maximum. |
| `minBeds` | integer | Leave empty for any number of bedrooms. |
| `minBaths` | integer | Leave empty for any number of bathrooms. |
| `minSqFt` | integer | Leave empty for any size. |
| `maxHoaPerMonth` | integer | Homes without HOA always pass. |
| `maxDaysOnMarket` | integer | For example 7 to keep only fresh listings. |
| `homeTypes` | array | Leave empty for every type. |
| `zipCodes` | array | Keep only homes in these ZIP codes (inside the areas of your links). |
| `mustInclude` | array | Keep only homes whose description, features or key facts mention every word, for example pool or garage. |
| `belowMedianOnly` | boolean | Keep only homes cheaper per sq ft than the median of the area you searched: a quick list of possible deals. Default: `false`. |
| `maxTotalChargeUsd` | number | The run stops before it spends more than this. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "home",
  "propertyId": 203587557,
  "listingId": 223427520,
  "mlsNumber": "4685752",
  "address": "802 Alexia Ln",
  "city": "Austin",
  "state": "TX",
  "zip": "78746",
  "neighborhood": "Addie Condos Ph 5",
  "price": 1699900,
  "beds": 4,
  "baths": 4.5,
  "sqFt": 3740,
  "pricePerSqFt": 455,
  "lotSizeSqFt": 15803,
  "yearBuilt": 2024,
  "hoaPerMonth": 805,
  "homeType": "house",
  "listingStatus": "Active",
  "daysOnMarket": 1,
  "daysOnRedfin": 0,
  "isNewConstruction": false,
  "isHotHome": false,
  "openHouse": "OPEN SUN, 12:30PM TO 3PM",
  "badges": [
    "Open House"
  ],
  "keyFacts": [
    "Designer upgrades",
    "Lock-and-leave home"
  ],
  "features": [
    "PRIVATE COURTYARD",
    "DESIGNER UPGRADES"
  ],
  "description": "Experience sophisticated luxury living near the heart of Westlake. Rare, swimming pool in your own private courtyard. $200k+ in designer...",
  "has3DTour": false,
  "hasVideoTour": false,
  "photoCount": 39,
  "latitude": 30.3120693,
  "longitude": -97.8284701,
  "areaMedianPrice": 537000,
  "areaMedianPricePerSqFt": 310,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/redfin-scraper").call(run_input={
    "searchUrls": [
        "https://www.redfin.com/city/30818/TX/Austin"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~redfin-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchUrls": ["https://www.redfin.com/city/30818/TX/Austin"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/redfin-scraper` as a tool.

Full documentation, pricing and the latest changes: [Redfin Search Scraper - Homes for Sale, Prices, Photos](https://apify.com/om_kh/redfin-scraper).

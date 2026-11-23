---
title: "New Business Leads - New Google Maps Listings by City"
description: "New business leads from Google Maps: give a city and category, get the businesses newly listed since your last check, with name, address and rating. For local sales and lead generation. $10 per 1,000 new businesses."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# New Business Leads - New Google Maps Listings by City

New business leads from Google Maps: give a city and category, get the businesses newly listed since your last check, with name, address and rating. For local sales and lead generation. $10 per 1,000 new businesses.

**Run it on Apify:** [https://apify.com/om_kh/google-maps-new-business-scraper](https://apify.com/om_kh/google-maps-new-business-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A city and a business category |
| **We do** | Search Google Maps and compare with your previous check |
| **You get** | One row per business newly listed since your last check: name, category, address, phone, website, rating, review count, coordinates and link |
| **It costs** | $10 per 1,000 new businesses + $0.001 per run. Optional scheduled monitoring: +$0.08 per check (one-off runs never pay it). The first 10 results of every run are free. |
| **It does not** | Prove a business just opened: "new" means it was not in the results at your previous check |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searches` | array | A category and area to watch on Google Maps, e.g. 'coffee shops in Austin, TX'. |
| `maxPlacesPerSearch` | integer | Upper bound on how many listings are read per search per run. Default: `10`. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Google Maps places actor", "authorization`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline of everything currently found (no alerts yet). Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate searches never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "ChIJ0QbsjcW1RIYRJxQSKO9kl8A",
  "query_id": "coffee shops in Austin, TX",
  "place_id": "ChIJ0QbsjcW1RIYRJxQSKO9kl8A",
  "business_name": "Café Crème - Downtown",
  "category": "Coffee shop",
  "categories": [
    "Breakfast restaurant",
    "Brunch restaurant"
  ],
  "address": "710 W Cesar Chavez St, Austin, TX 78701",
  "city": "Austin",
  "state": "Texas",
  "country": "US",
  "latitude": 30.27,
  "longitude": -97.75,
  "rating": 4.7,
  "review_count": 345,
  "phone": "(hidden here)",
  "website": "https://cafecremeaustin.com/locations/downtown",
  "google_maps_url": "https://www.google.com/maps/search/?api=1&query=Caf%C3%A9%20Cr%C3%A8me%20-%20Downtown&query_place_id=ChIJ0QbsjcW1RIYRJxQSKO9kl8A",
  "title": "Café Crème - Downtown",
  "categoryName": "Coffee shop",
  "neighborhood": "Seaholm District",
  "street": "710 W Cesar Chavez St",
  "postalCode": "78701",
  "countryCode": "US",
  "phoneUnformatted": "(hidden here)",
  "claimThisBusiness": false,
  "totalScore": 4.7,
  "permanentlyClosed": false,
  "temporarilyClosed": false,
  "placeId": "ChIJ0QbsjcW1RIYRJxQSKO9kl8A",
  "fid": "0x8644b5c58dec06d1:0xc09764ef28121427",
  "cid": "13877671755097707559",
  "reviewsCount": 345,
  "imagesCount": 600,
  "scrapedAt": "2026-10-24T21:36:53.391Z",
  "wasOpenAtScrapeTime": true,
  "url": "https://www.google.com/maps/search/?api=1&query=Caf%C3%A9%20Cr%C3%A8me%20-%20Downtown&query_place_id=ChIJ0QbsjcW1RIYRJxQSKO9kl8A",
  "searchPageUrl": "https://www.google.com/maps/search/coffee%20shops%20in%20Austin,%20TX?hl=en",
  "searchString": "coffee shops in Austin, TX",
  "language": "en",
  "rank": 4,
  "isAdvertisement": false,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-maps-new-business-scraper").call(run_input={
    "searches": [
        "coffee shops in Austin, TX"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-maps-new-business-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searches": ["coffee shops in Austin, TX"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-maps-new-business-scraper` as a tool.

Full documentation, pricing and the latest changes: [New Business Leads - New Google Maps Listings by City](https://apify.com/om_kh/google-maps-new-business-scraper).

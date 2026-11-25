---
title: "Google Maps Business Scraper API - Name, Rating, Phone"
description: "Google Maps business scraper API: businesses for any search and location: name, address, phone, website, category, rating, review count and coordinates. No login or Google API key needed. For lead generation and local-market research. $9/1K places, $0.92/1K from 16 Dec. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Google Maps Business Scraper API - Name, Rating, Phone

Google Maps business scraper API: businesses for any search and location: name, address, phone, website, category, rating, review count and coordinates. No login or Google API key needed. For lead generation and local-market research. $9/1K places, $0.92/1K from 16 Dec. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/google-maps-business-scraper](https://apify.com/om_kh/google-maps-business-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A search and a place, such as `dentist` in `Montreal` |
| **We do** | Search Google Maps and read each business, and compare with your last run |
| **You get** | One row per place: name, category, rating, review count, address, phone, website, opening status, coordinates, place ID and link, plus every field the supplier returns (`source_data`) |
| **It costs** | $9 per 1,000 places today, $0.92 per 1,000 from 16 December 2026 + $0.001 per run. Optional scheduled monitoring: +$0.10 per check today, $0.005 from 16 December 2026 (one-off runs never pay it). Apify also bills the supplier Actor `kaix/google-maps-places-scraper` that this robot runs for you, at its own price (about $0.08 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Need a Google API key or sign in to Google |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `placeUrls` | array | Google Maps URLs for the business(es) or competitors to track. |
| `searchQueries` | array | Alternative to placeUrls: search terms, e.g. "coffee shop" combined with a location. |
| `locationQuery` | string | City/region to search in, e.g. "Montreal, Canada". |
| `currentPlaces` | array | Bring your own place records (e.g. from a prior Google Maps scraper run) instead of Vigia fetching them. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run's own change events may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Google Maps place data (via compass/crawler-googl`. |

## Example output

A row as shown in the Actor's README:

```json
{
  "place_id": "ChIJN1t_tDeuEmsRUsoyG83frY4",
  "title": "Google Sydney - Pirrama Road",
  "rating": 4.1,
  "reviews_count": 1220,
  "address": "Ground Floor/48 Pirrama Rd, Pyrmont NSW 2009, Australia",
  "categories": [
    "Corporate office",
    "Software company"
  ],
  "hours_fingerprint": "v2:1d946720afe77823",
  "permanently_closed": false,
  "temporarily_closed": false,
  "formattedAddress": "Ground Floor/48 Pirrama Rd, Pyrmont NSW 2009, Australia",
  "shortAddress": "Google Sydney - Pirrama Road, Ground Floor/48 Pirrama Rd, Pyrmont",
  "street": "Ground Floor/48 Pirrama Rd",
  "city": "Pyrmont",
  "postalCode": "2009",
  "state": "NSW",
  "countryCode": "AU",
  "latitude": -33.866489,
  "longitude": 151.1958561,
  "timezone": "Australia/Sydney",
  "area": "Pyrmont NSW, Australia",
  "entranceLatitude": -33.866489,
  "entranceLongitude": 151.1958561,
  "plusCode": "4RRH45MW+C8",
  "utcOffsetMinutes": 660,
  "adrFormatAddress": "Ground Floor/<span class=\"street-address\">48 Pirrama Rd</span>, <span class=\"locality\">Pyrmont</span> <span class=\"region\">NSW</span> <sp...",
  "placeId": "ChIJN1t_tDeuEmsRUsoyG83frY4",
  "dataId": "0x6b12ae37b47f5b37:0x8eaddfcd1b32ca52",
  "website": "http://google.com/",
  "phone": "(hidden here)",
  "phoneIntl": "(hidden here)",
  "phone2": "(hidden here)",
  "phoneIntl2": "(hidden here)",
  "hoursStatus": "Closed · Opens 8:30 AM Mon",
  "isOpenNow": false,
  "googleMapsUri": "https://www.google.com/maps/place/Google+Sydney+-+Pirrama+Road,+Ground+Floor%2F48+Pirrama+Rd,+Pyrmont+NSW+2009,+Australia/@-33.866489,151...",
  "profileImageUrl": "https://lh6.googleusercontent.com/-G07I17q8WY8/AAAAAAAAAAI/AAAAAAAAAAA/vCgGhXTAdKc/s44-p-k-no-ns-nd/photo.jpg",
  "ownerId": "(hidden here)",
  "cid": "10281119596374313554",
  "knowledgeGraphId": "/g/1td76qvq",
  "businessType": "corporate_office",
  "primaryType": "corporate_office",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-maps-business-scraper").call(run_input={
    "placeUrls": [
        "https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-maps-business-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"placeUrls": ["https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-maps-business-scraper` as a tool.

Full documentation, pricing and the latest changes: [Google Maps Business Scraper API - Name, Rating, Phone](https://apify.com/om_kh/google-maps-business-scraper).

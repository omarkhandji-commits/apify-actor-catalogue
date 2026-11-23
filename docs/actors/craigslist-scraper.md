---
title: "Craigslist Classifieds Scraper - Listings, Prices, Photos"
description: "Craigslist classifieds scraper by search or posting link, any city: title, price, GPS, photos; option: description, attributes, city/state/ZIP, emails and phones. Filters: keyword, price, condition, photo, today. Beyond the 360-result limit. $1 per 1,000 listings, + $0.001 per run from Dec 4, 2026."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Craigslist Classifieds Scraper - Listings, Prices, Photos

Craigslist classifieds scraper by search or posting link, any city: title, price, GPS, photos; option: description, attributes, city/state/ZIP, emails and phones. Filters: keyword, price, condition, photo, today. Beyond the 360-result limit. $1 per 1,000 listings, + $0.001 per run from Dec 4, 2026.

**Run it on Apify:** [https://apify.com/om_kh/craigslist-scraper](https://apify.com/om_kh/craigslist-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Craigslist search links or single posting links, or cities with a category and keywords |
| **We do** | Read the listings, beyond Craigslist's 360-result limit |
| **You get** | One row per listing: title, price, currency, date, region, category name, GPS, photos and link; option: full description, attributes as a key → value map (bedrooms, condition, odometer, make...), city, state and ZIP code, subcategory, post ID and reply token |
| **It costs** | $1 per 1,000 listings, $1.50 per 1,000 with details, + $0.001 per run from Dec 4, 2026 (no start fee before). The first 20 listings of every run are free. No supplier fee |
| **It does not** | Reveal the poster's hidden contact (Craigslist relays it); emails and phone numbers written in the posting text are extracted |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchUrls` | array | Paste search links from Craigslist with your filters, e.g. https://newyork.craigslist.org/search/brk/apa?max_price=3000, or single posting links (up to 50). Default: `["https://sfbay.craigslist.org/search/sss?query=bike"]`. |
| `cities` | array | Or build searches: Craigslist city hostnames such as newyork, losangeles, sfbay, chicago, london, paris, toronto. |
| `category` | string | Category used with Cities. Default: `"sss"`. |
| `keywords` | array | Keywords used with Cities; one search per city and keyword. |
| `priceMin` | integer | Only postings priced at or above this amount. |
| `priceMax` | integer | Only postings priced at or below this amount. |
| `condition` | string | Craigslist's own condition filter. |
| `hasImage` | boolean | Only postings that have at least one photo. Default: `false`. |
| `postedToday` | boolean | Only postings published in the last 24 hours. Default: `false`. |
| `sort` | string | Order of the results. Default: `"date"`. |
| `maxItemsPerSearch` | integer | Newest first, 1 to 10,000. Default: `100`. |
| `postedAfter` | string | Only listings posted on or after this date (YYYY-MM-DD). |
| `includeDetails` | boolean | Open each listing: description, attributes as a key → value map, city, state and ZIP code, subcategory, post ID, reply token, address, plus emails and phone numbers written in the text. Default: `true`. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "input_ref": "https://sfbay.craigslist.org/nby/bik/d/kentfield-trek-superfly-carbon-mtb/7993444368.html",
  "postingId": 7993444368,
  "title": "Trek Superfly carbon mtb",
  "price": 800,
  "priceText": "$800",
  "url": "https://www.craigslist.org/view/d/kentfield-trek-superfly-carbon-mtb/s6f7MvkeZT7hzcbtCpkg8v",
  "postedAt": "2026-11-01T06:31:54-0800",
  "category": "bik",
  "categoryLabel": "bicycles - by owner",
  "region": "sfbay",
  "latitude": 37.984668,
  "longitude": -122.535657,
  "imageUrls": [
    "https://images.craigslist.org/00R0R_7cXWWDz4q3S_0x20oM_600x450.jpg",
    "https://images.craigslist.org/00x0x_6e8Gpfk8FHn_0x20oM_600x450.jpg"
  ],
  "imageCount": 7,
  "postId": "7993444368",
  "subcategorySlug": "bik",
  "subcategoryLabel": "bicycles - by owner",
  "sectionSlug": "sso",
  "attributesMap": {
    "bicycle_type": "mountain",
    "bicycle_frame_size_freeform": "Large",
    "bicycle_wheel_size": "29 in",
    "bicycle_frame_material": "carbon fiber"
  },
  "city": "Kentfield",
  "state": "CA",
  "postalCode": "94914",
  "countryCode": "US",
  "currency": "USD",
  "replyToken": "sfo/bik/7993444368",
  "contactAvailable": true,
  "isDeleted": false,
  "description": "Trek Superfly carbon hardtail mountain bike\n\nIn good condition, no issues\n\nFrame: Trek Sup...",
  "condition": "good",
  "emails": [],
  "phoneNumbers": [],
  "attributes": [
    "bicycle type: mountain",
    "frame size: Large",
    "wheel size: 29 in"
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/craigslist-scraper").call(run_input={
    "searchUrls": [
        "https://sfbay.craigslist.org/search/sss?query=bike"
    ],
    "maxItemsPerSearch": 50
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~craigslist-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchUrls": ["https://sfbay.craigslist.org/search/sss?query=bike"], "maxItemsPerSearch": 50}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/craigslist-scraper` as a tool.

Full documentation, pricing and the latest changes: [Craigslist Classifieds Scraper - Listings, Prices, Photos](https://apify.com/om_kh/craigslist-scraper).

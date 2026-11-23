---
title: "App Store Reviews Scraper API - Ratings, Text, $0.10/1K"
description: "App Store reviews scraper API: Apple reviews for any app, several countries per run, with rating, title, text, author, version and date. $0.10 per 1,000 reviews, first 50 per run free. No API key, no login. JSON, CSV, Excel, API, MCP."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# App Store Reviews Scraper API - Ratings, Text, $0.10/1K

App Store reviews scraper API: Apple reviews for any app, several countries per run, with rating, title, text, author, version and date. $0.10 per 1,000 reviews, first 50 per run free. No API key, no login. JSON, CSV, Excel, API, MCP.

**Run it on Apify:** [https://apify.com/om_kh/appstore-reviews-api](https://apify.com/om_kh/appstore-reviews-api) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Apple App Store app IDs or links, and countries |
| **We do** | Read the apps' customer reviews |
| **You get** | One row per review: rating, title, text, app version, helpful votes, date and link, with the app's name, developer, average rating and rating count |
| **It costs** | **$0.10 per 1,000 reviews**, + $0.001 per run. Private, deleted or invalid inputs are never charged. No supplier fee |
| **It does not** | Need an API key or cookies, or read Google Play (for both stores, see our App Store & Google Play Reviews Scraper) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `apps` | array | App Store URLs or numeric app IDs. |
| `countries` | array | Two-letter country codes. Default: `["us"]`. |
| `maxReviewsPerApp` | integer | Apple serves at most 500 recent reviews per storefront (10 pages of 50). Default: `200`. |
| `includeAppMetadata` | boolean | Attach the app name, developer and lifetime average rating to every row. Default: `true`. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |

## Example output

A row as shown in the Actor's README:

```json
{
  "review_id": "14698595204",
  "app_id": "310633997",
  "country": "us",
  "rating": 1,
  "title": "Spam restrictions",
  "text": "I have no idea what I did wrong, I got restricted for no reasons please get that fixed immediately check before you restrict people don’t...",
  "author": "(hidden here)",
  "app_version": "26.41.75",
  "published_at": "2026-10-22T13:22:35-07:00",
  "helpful_votes": 0,
  "review_url": "https://itunes.apple.com/us/review?id=310633997&type=Purple%20Software",
  "source": "app_store",
  "app_name": "WhatsApp Messenger",
  "developer": "WhatsApp Inc.",
  "average_rating": 4.6832,
  "rating_count": 18827914,
  "app_url": "https://apps.apple.com/us/app/whatsapp-messenger/id310633997?uo=4"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/appstore-reviews-api").call(run_input={
    "apps": [
        "https://apps.apple.com/us/app/whatsapp-messenger/id310633997"
    ],
    "countries": [
        "us",
        "gb",
        "fr"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~appstore-reviews-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"apps": ["https://apps.apple.com/us/app/whatsapp-messenger/id310633997"], "countries": ["us", "gb", "fr"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/appstore-reviews-api` as a tool.

Full documentation, pricing and the latest changes: [App Store Reviews Scraper API - Ratings, Text, $0.10/1K](https://apify.com/om_kh/appstore-reviews-api).

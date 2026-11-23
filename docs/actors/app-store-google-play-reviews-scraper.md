---
title: "App Store & Google Play Reviews Scraper - Ratings"
description: "Bulk-download app reviews from the Apple App Store and Google Play in one run: rating, title, text, author, app version and date. Export to JSON, CSV or Excel, or call it as an API. No login needed. For app sentiment analysis, release-quality tracking and competitor research. $0.02 per review."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# App Store & Google Play Reviews Scraper - Ratings

Bulk-download app reviews from the Apple App Store and Google Play in one run: rating, title, text, author, app version and date. Export to JSON, CSV or Excel, or call it as an API. No login needed. For app sentiment analysis, release-quality tracking and competitor research. $0.02 per review.

**Run it on Apify:** [https://apify.com/om_kh/app-store-google-play-reviews-scraper](https://apify.com/om_kh/app-store-google-play-reviews-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Apple App Store and Google Play app IDs |
| **We do** | Read the reviews from both stores in one run |
| **You get** | One row per review: store, rating, title, text, author, app version, helpful votes, country and date, with a topic and severity |
| **It costs** | $0.02 per actionable review, $0.00019 ($0.19 per 1,000) from 2 December 2026, + $0.001 per run; other reviews are free. Optional scheduled monitoring: +$0.03 per check (one-off runs never pay it). The first 10 results of every run are free. For App Store reviews in bulk at $0.10 per 1,000, see our App Store Reviews API |
| **It does not** | Sign in to the stores or reply to reviews |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `appStoreApps` | array | iOS App Store apps to monitor. |
| `playStoreApps` | array | Google Play apps to monitor. |
| `currentReviews` | array | Skip the chained fetch and pass review data directly. |
| `previousReviews` | array | Reviews from the prior run; used to identify new reviews when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained App Store reviews actor", "authorization"`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |
| `maxReviewsPerApp` | integer | Newest reviews to read for each app and store (up to 500). Default: `50`. |

## Example output

A row as shown in the Actor's README:

```json
{
  "review_id": "04d9f75e-f910-449d-a896-729388e16b9d",
  "subject_id": "com.spotify.music",
  "author": "(hidden here)",
  "rating": 4,
  "text": "i hate ads",
  "published_at": "2026-10-23T20:56:01Z",
  "type": "review",
  "reviewId": "04d9f75e-f910-449d-a896-729388e16b9d",
  "appId": "com.spotify.music",
  "url": "https://play.google.com/store/apps/details?id=com.spotify.music&hl=en&gl=us&reviewId=04d9f75e-f910-449d-a896-729388e16b9d",
  "userName": "(hidden here)",
  "userImage": "(hidden here)",
  "score": 4,
  "thumbsUp": 0,
  "appVersion": "9.1.92.3058",
  "date": "2026-10-23T20:56:01Z",
  "replyText": "Hey. We hear you and we'll pass your feedback along to the Ads team. For an ad-free experience, we'd recommend checking out our Premium p...",
  "replyDate": "2026-10-23T21:06:06Z",
  "country": "us",
  "language": "en",
  "record_id": "04d9f75e-f910-449d-a896-729388e16b9d",
  "change_type": "new",
  "actionable": false,
  "topic": "other",
  "severity": "minor",
  "why_it_matters": "New positive review — no action needed."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/app-store-google-play-reviews-scraper").call(run_input={
    "appStoreApps": [
        "389801252"
    ],
    "playStoreApps": [
        "com.spotify.music"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~app-store-google-play-reviews-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"appStoreApps": ["389801252"], "playStoreApps": ["com.spotify.music"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/app-store-google-play-reviews-scraper` as a tool.

Full documentation, pricing and the latest changes: [App Store & Google Play Reviews Scraper - Ratings](https://apify.com/om_kh/app-store-google-play-reviews-scraper).

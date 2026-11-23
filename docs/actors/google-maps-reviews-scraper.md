---
title: "Google Maps Reviews Scraper API - Rating, Text, Reviewer"
description: "Google Maps reviews scraper API: bulk-download reviews for any business or place: rating, text, reviewer, owner response and date. Export to JSON, CSV or Excel, or call it from the API, n8n or Make. No login or Google API key needed. For reputation and local-market research. $0.0003 per review."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Google Maps Reviews Scraper API - Rating, Text, Reviewer

Google Maps reviews scraper API: bulk-download reviews for any business or place: rating, text, reviewer, owner response and date. Export to JSON, CSV or Excel, or call it from the API, n8n or Make. No login or Google API key needed. For reputation and local-market research. $0.0003 per review.

**Run it on Apify:** [https://apify.com/om_kh/google-maps-reviews-scraper](https://apify.com/om_kh/google-maps-reviews-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Google Maps places (business names or links) |
| **We do** | Read each place's Google Maps reviews |
| **You get** | One row per review: stars, text, date, likes, reviewer (Local Guide or not, number of reviews), the owner's reply, plus the place's score, review count, address and category, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.30 per 1,000 reviews, no start fee (lowered on 21 November 2026 from $0.80). Optional scheduled monitoring: +$0.005 per check (one-off runs never pay it). Apify also bills the supplier Actor `compass/Google-Maps-Reviews-Scraper` that this robot runs for you, at its own price (about $0.60 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Need a Google API key, sign in, or reply to reviews |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `placeUrls` | array | Google Maps place URLs (or place IDs) to monitor for new reviews. |
| `maxReviewsPerPlace` | integer | How many of the most recent reviews to read for each link, up to 1,000. Default: `50`. |
| `currentReviews` | array | Skip the chained fetch and pass review data directly, e.g. from your own export. |
| `previousReviews` | array | Reviews from the prior run; used to identify new feedback when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Google Maps reviews actor", "authorizatio`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "review_id": "Ci9DQUlRQUNvZENodHljRjlvT21sVGNqVlVhemhGZEhFMlJUTk5Ramh5Wm14cmNGRRAB",
  "subject_id": "https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4",
  "author": "(hidden here)",
  "rating": 1,
  "text": "perfecto",
  "published_at": "3 days ago",
  "searchString": "Direct Detail URL: https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4",
  "reviewerId": "(hidden here)",
  "reviewerUrl": "(hidden here)",
  "name": "(hidden here)",
  "reviewerNumberOfReviews": "(hidden here)",
  "isLocalGuide": false,
  "reviewerPhotoUrl": "(hidden here)",
  "textTranslated": "perfect",
  "publishAt": "3 days ago",
  "publishedAtDate": "2026-10-21T14:03:02.822Z",
  "likesCount": 0,
  "reviewId": "Ci9DQUlRQUNvZENodHljRjlvT21sVGNqVlVhemhGZEhFMlJUTk5Ramh5Wm14cmNGRRAB",
  "reviewUrl": "https://www.google.com/maps/reviews/data=!4m8!14m7!1m6!2m5!1sCi9DQUlRQUNvZENodHljRjlvT21sVGNqVlVhemhGZEhFMlJUTk5Ramh5Wm14cmNGRRAB!2m1!1s0...",
  "reviewOrigin": "Google",
  "stars": 1,
  "originalLanguage": "es",
  "translatedLanguage": "en",
  "isAdvertisement": false,
  "placeId": "ChIJN1t_tDeuEmsRUsoyG83frY4",
  "address": "Ground Floor/48 Pirrama Rd, Pyrmont NSW 2009, Australia",
  "street": "Ground Floor/48 Pirrama Rd",
  "city": "Pyrmont",
  "postalCode": "2009",
  "state": "New South Wales",
  "countryCode": "AU",
  "categoryName": "Corporate office",
  "categories": [
    "Corporate office",
    "Software company"
  ],
  "title": "Google Sydney - Pirrama Road",
  "totalScore": 4.1,
  "permanentlyClosed": false,
  "temporarilyClosed": false,
  "reviewsCount": 1220,
  "url": "https://www.google.com/maps/search/?api=1&query=Google%20Sydney%20-%20Pirrama%20Road&query_place_id=ChIJN1t_tDeuEmsRUsoyG83frY4",
  "cid": "10281119596374313554",
  "fid": "0x6b12ae37b47f5b37:0x8eaddfcd1b32ca52",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-maps-reviews-scraper").call(run_input={
    "placeUrls": [
        "https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-maps-reviews-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"placeUrls": ["https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-maps-reviews-scraper` as a tool.

Full documentation, pricing and the latest changes: [Google Maps Reviews Scraper API - Rating, Text, Reviewer](https://apify.com/om_kh/google-maps-reviews-scraper).

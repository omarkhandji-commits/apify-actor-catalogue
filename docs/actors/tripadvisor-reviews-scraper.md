---
title: "Tripadvisor Reviews Scraper API - Ratings, Owner Replies"
description: "Tripadvisor reviews scraper API: bulk-download reviews for any hotel, restaurant or attraction: rating, sub-ratings, title, text, trip type, visit date, owner reply, photos and reviewer profile. JSON, CSV, Excel or API. No login. For hospitality benchmarking. $0.00025 per review."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Tripadvisor Reviews Scraper API - Ratings, Owner Replies

Tripadvisor reviews scraper API: bulk-download reviews for any hotel, restaurant or attraction: rating, sub-ratings, title, text, trip type, visit date, owner reply, photos and reviewer profile. JSON, CSV, Excel or API. No login. For hospitality benchmarking. $0.00025 per review.

**Run it on Apify:** [https://apify.com/om_kh/tripadvisor-reviews-scraper](https://apify.com/om_kh/tripadvisor-reviews-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | TripAdvisor links of hotels, restaurants or attractions |
| **We do** | Read the place's most recent reviews |
| **You get** | One row per review: rating, title, text, trip type, travel date, helpful votes, photos, traveler location and the owner's reply, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.25 per 1,000 reviews, no start fee (lowered on 21 November 2026 from $2). Optional scheduled monitoring: +$0.005 per check (one-off runs never pay it). Apify also bills the supplier Actor `kaix/tripadvisor-reviews-scraper` that this robot runs for you, at its own price (about $0.05 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to TripAdvisor or reply to reviews |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `locationUrls` | array | TripAdvisor location URLs (hotel/restaurant/attraction) to monitor for new reviews. |
| `maxReviewsPerPlace` | integer | How many of the most recent reviews to read for each link, up to 1,000. Default: `20`. |
| `currentReviews` | array | Skip the chained fetch and pass review data directly, e.g. from your own export. |
| `previousReviews` | array | Reviews from the prior run; used to identify new feedback when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained TripAdvisor reviews actor", "authorizatio`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "review_id": "1080272805",
  "subject_id": "https://www.tripadvisor.com/Hotel_Review-g60763-d208453-Reviews-Hilton_New_York_Times_Square-New_York_City_New_York.html",
  "author": "(hidden here)",
  "rating": 5,
  "text": "Conveniently located in the heart of Times Square. A perfect “home base” for our 3 day stay where we could easily walk to theaters, resta...",
  "published_at": "October 2, 2026",
  "id": "1080272805",
  "locationId": 208453,
  "businessName": "Hilton New York Times Square",
  "businessUrl": "https://www.tripadvisor.com/Hotel_Review-g60763-d208453-Reviews-Hilton_New_York_Times_Square-New_York_City_New_York.html",
  "title": "Great Location in Times Square",
  "publishedDate": "October 2, 2026",
  "dateVisited": "July 2026",
  "tripType": "Family",
  "ownerResponse": "Dear Avemaria,\nThank you for choosing Hilton Times Square as your home base and for sharing such a thoughtful review. We are glad that ou...",
  "helpfulVotes": 0,
  "scrapedAt": "2026-10-24T19:00:23.873Z",
  "reviewUrl": "https://www.tripadvisor.com/ShowUserReviews-g60763-d208453-r1080272805-Hilton_New_York_Times_Square-New_York_City_New_York.html",
  "placeType": "ACCOMMODATION",
  "isTranslated": false,
  "isPinned": false,
  "tipText": "Buy water and snack items from Target (across the street) to avoid higher prices at the onsite sundry (a 1L bottle of Evian was $11!)",
  "createdDate": "2026-10-02",
  "publishedDateISO": "2026-10-02",
  "dateVisitedISO": "2026-07-01",
  "language": "en",
  "originalLanguage": "en",
  "status": "PUBLISHED",
  "author_displayName": "(hidden here)",
  "author_hometown": "(hidden here)",
  "author_totalContributions": "(hidden here)",
  "author_avatarUrl": "(hidden here)",
  "author_profileUrl": "(hidden here)",
  "author_userId": "(hidden here)",
  "author_isVerified": "(hidden here)",
  "author_username": "(hidden here)",
  "ownerResponseDetail_id": 1080754555,
  "ownerResponseDetail_text": "Dear Avemaria,\nThank you for choosing Hilton Times Square as your home base and for sharing such a thoughtful review. We are glad that ou...",
  "ownerResponseDetail_language": "en",
  "ownerResponseDetail_publishedDate": "2026-10-06",
  "ownerResponseDetail_connectionToSubject": "General Manager",
  "ownerResponseDetail_author_userId": "(hidden here)",
  "ownerResponseDetail_author_displayName": "(hidden here)",
  "ownerResponseDetail_author_profileUrl": "(hidden here)",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/tripadvisor-reviews-scraper").call(run_input={
    "locationUrls": [
        "https://www.tripadvisor.com/Hotel_Review-g60763-d208453-Reviews-Hilton_New_York_Times_Square-New_York_City_New_York.html"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~tripadvisor-reviews-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"locationUrls": ["https://www.tripadvisor.com/Hotel_Review-g60763-d208453-Reviews-Hilton_New_York_Times_Square-New_York_City_New_York.html"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/tripadvisor-reviews-scraper` as a tool.

Full documentation, pricing and the latest changes: [Tripadvisor Reviews Scraper API - Ratings, Owner Replies](https://apify.com/om_kh/tripadvisor-reviews-scraper).

---
title: "Booking.com Reviews Scraper - Score, Text, Guest Name"
description: "Booking.com reviews scraper for any hotel or stay. Give a hotel page URL and get its guest reviews back: score, review text, guest name and stay date for each, plus a fake-review velocity signal that flags sudden, suspicious spikes in review volume for that property. $0.001 per review."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Booking.com Reviews Scraper - Score, Text, Guest Name

Booking.com reviews scraper for any hotel or stay. Give a hotel page URL and get its guest reviews back: score, review text, guest name and stay date for each, plus a fake-review velocity signal that flags sudden, suspicious spikes in review volume for that property. $0.001 per review.

**Run it on Apify:** [https://apify.com/om_kh/booking-com-reviews-scraper](https://apify.com/om_kh/booking-com-reviews-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Booking.com hotel or stay links |
| **We do** | Read each property's most recent guest reviews |
| **You get** | One row per review: score, title, liked and disliked text, traveler type and country, room, nights, stay and review dates, language, the property's reply and its score per criterion (`hotelRatingScores_Staff`, `_Cleanliness`, `_Location`...), plus every field the supplier returns (`source_data`) |
| **It costs** | $1 per 1,000 reviews, no start fee (lowered on 21 November 2026 from $3). Optional scheduled monitoring: +$0.008 per check (one-off runs never pay it). Apify also bills the supplier Actor `voyager/booking-reviews-scraper` that this robot runs for you, at its own price (about $2 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Booking.com or give room prices |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `hotelUrls` | array | Booking.com hotel/property URLs to monitor for new reviews. |
| `maxReviewsPerPlace` | integer | How many of the most recent reviews to read for each link, up to 1,000. Default: `50`. |
| `currentReviews` | array | Skip the chained fetch and pass review data directly, e.g. from your own export. |
| `previousReviews` | array | Reviews from the prior run; used to identify new feedback when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Booking.com reviews actor", "authorizatio`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "review_id": "2ef684194b63fd68",
  "subject_id": "https://www.booking.com/hotel/us/new-york-hilton-midtown.html",
  "author": "(hidden here)",
  "rating": 9,
  "published_at": "2024-02-24T14:07:36.000Z",
  "likedText": "Good location close to Times Square and the park. Easy to get to and visit tourist attractions. The rooms were very clean and spacious. T...",
  "dislikedText": "No in room coffee maker. The prices for laundry and food and drinks is a little excessive but other stores are around.",
  "reviewTitle": "Another great stay at the Midtown Hilton.",
  "travelerType": "Family",
  "userLocation": "(hidden here)",
  "userName": "(hidden here)",
  "userAvatar": "(hidden here)",
  "propertyResponse": "Dear Andrew,\nThank you for your positive words about your recent stay at New York Hilton Midtown, highlighting our convenient location, c...",
  "checkInDate": "2024-02-16",
  "checkOutDate": "2024-02-20",
  "reviewDate": "2024-02-24T14:07:36.000Z",
  "images": [
    "https://q-xx.bstatic.com/xdata/images/xphoto/max1280x900/314069960.jpg?k=52d2e45ce266fc8a0647974a2145c2fbf0b84d67e9c0e877775d8a535557d18c&o="
  ],
  "id": "2ef684194b63fd68",
  "roomInfo": "City Room Two Double Beds",
  "numberOfNights": 4,
  "reviewLanguage": "xu",
  "stayRoomId": 5589024,
  "helpfulVotes": 0,
  "totalCategoryReviews": 1542,
  "hotelId": 55890,
  "reviewsScoreFilter": "ALL",
  "reviewPage": 1,
  "startUrl": "https://www.booking.com/hotel/us/new-york-hilton-midtown.html",
  "hotelRating": 7.2,
  "hotelReviews": 1542,
  "record_id": "2ef684194b63fd68",
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
run = client.actor("om_kh/booking-com-reviews-scraper").call(run_input={
    "hotelUrls": [
        "https://www.booking.com/hotel/us/new-york-hilton-midtown.html"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~booking-com-reviews-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"hotelUrls": ["https://www.booking.com/hotel/us/new-york-hilton-midtown.html"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/booking-com-reviews-scraper` as a tool.

Full documentation, pricing and the latest changes: [Booking.com Reviews Scraper - Score, Text, Guest Name](https://apify.com/om_kh/booking-com-reviews-scraper).

---
title: "Yelp Reviews Scraper API - Ratings, Owner Replies, Elite"
description: "Yelp reviews scraper API: bulk-download reviews for any business: rating, text, date, owner reply, useful/funny/cool votes, photos, and the reviewer's name, city, review count, friends and Elite status. Paste business URLs. Export to JSON, CSV or Excel, or use the API. No login. $0.00025 per review."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Yelp Reviews Scraper API - Ratings, Owner Replies, Elite

Yelp reviews scraper API: bulk-download reviews for any business: rating, text, date, owner reply, useful/funny/cool votes, photos, and the reviewer's name, city, review count, friends and Elite status. Paste business URLs. Export to JSON, CSV or Excel, or use the API. No login. $0.00025 per review.

**Run it on Apify:** [https://apify.com/om_kh/yelp-reviews-scraper](https://apify.com/om_kh/yelp-reviews-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Yelp business links |
| **We do** | Read each business's Yelp reviews |
| **You get** | One row per review: rating, text, date, owner reply, useful / funny / cool votes, photos, and the reviewer's name, city, review count and Elite status, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.25 per 1,000 reviews, no start fee (lowered on 21 November 2026 from $0.60). Optional scheduled monitoring: +$0.005 per check (one-off runs never pay it). Apify also bills the supplier Actor `kaix/yelp-reviews-scraper` that this robot runs for you, at its own price (about $0.05 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Yelp or reply to reviews |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `businessUrls` | array | Yelp business page URLs to monitor for new reviews. Default: `["https://www.yelp.com/biz/katzs-delicatessen-new-york"]`. |
| `maxReviewsPerPlace` | integer | How many of the most recent reviews to read for each link, up to 1,000. Default: `50`. |
| `currentReviews` | array | Skip the chained fetch and pass review data directly. |
| `previousReviews` | array | Reviews from the prior run; used to identify new feedback when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Yelp reviews actor", "authorization": "pu`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |

## Example output

A row as shown in the Actor's README:

```json
{
  "review_id": "PTaxWt3uCV1aePQ12F9fdg",
  "subject_id": "https://www.yelp.com/biz/katzs-delicatessen-new-york",
  "author": "(hidden here)",
  "rating": 5,
  "text": "Mind blowing! Pastrami Sandwich on Rye. Just order it how it normally comes. All they put on it is a special mustard spread. And that's a...",
  "published_at": "2026-10-09T17:03:17.000Z",
  "id": "PTaxWt3uCV1aePQ12F9fdg",
  "businessAlias": "katzs-delicatessen-new-york",
  "businessName": "Katz's Delicatessen",
  "businessEncId": "V7lXZKBDzScDeGB8JmnzSA",
  "language": "en",
  "createdAt": "2026-10-09T17:03:17.000Z",
  "localDateTime": "2026-10-09T13:03:17-04:00",
  "ownerReply": "We're so glad you enjoyed your first visit - and yes, we do like to let our pastrami be the star of the show! Hope to see you back again...",
  "scrapedAt": "2026-10-24T19:01:02.868Z",
  "author_id": "(hidden here)",
  "author_displayName": "(hidden here)",
  "author_displayLocation": "(hidden here)",
  "author_reviewCount": "(hidden here)",
  "author_friendCount": "(hidden here)",
  "author_photoCount": "(hidden here)",
  "author_eliteYear": "(hidden here)",
  "author_profilePhotoUrl": "(hidden here)",
  "author_isEliteAllStar": "(hidden here)",
  "feedback_usefulCount": 0,
  "feedback_funnyCount": 0,
  "feedback_coolCount": 0,
  "tags_checkInCount": 0,
  "tags_isFirstReviewer": "(hidden here)",
  "tags_hasPaidThroughYelp": false,
  "tags_hasPurchasedDeal": false,
  "tags_hasPlacedReservation": false,
  "tags_isReviewOfTheDay": false,
  "expertRecognition_displayName": "(hidden here)",
  "expertRecognition_reviewCount": 89,
  "record_id": "PTaxWt3uCV1aePQ12F9fdg",
  "change_type": "new",
  "actionable": false,
  "topic": "support",
  "severity": "minor",
  "why_it_matters": "New positive review — no action needed."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/yelp-reviews-scraper").call(run_input={
    "businessUrls": [
        "https://www.yelp.com/biz/katzs-delicatessen-new-york"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~yelp-reviews-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"businessUrls": ["https://www.yelp.com/biz/katzs-delicatessen-new-york"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/yelp-reviews-scraper` as a tool.

Full documentation, pricing and the latest changes: [Yelp Reviews Scraper API - Ratings, Owner Replies, Elite](https://apify.com/om_kh/yelp-reviews-scraper).

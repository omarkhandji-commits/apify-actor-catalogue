---
title: "G2 Software Reviews Scraper - Ratings, Pros, Cons"
description: "Bulk-download G2 reviews for any software product: rating, title, pros, cons, reviewer role and date. Export to JSON, CSV or Excel, or call it from the API, n8n or Make. No login needed. For competitive research, win-loss analysis and voice-of-customer work. Our fee $20 per 1,000 reviews + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# G2 Software Reviews Scraper - Ratings, Pros, Cons

Bulk-download G2 reviews for any software product: rating, title, pros, cons, reviewer role and date. Export to JSON, CSV or Excel, or call it from the API, n8n or Make. No login needed. For competitive research, win-loss analysis and voice-of-customer work. Our fee $20 per 1,000 reviews + supplier.

**Run it on Apify:** [https://apify.com/om_kh/g2-reviews-scraper](https://apify.com/om_kh/g2-reviews-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | G2 software product links |
| **We do** | Read the product's reviews |
| **You get** | One row per review: star rating, NPS, title, text, date, company size, industry and the sub-scores (ease of use, support...), plus every field the supplier returns (`source_data`) |
| **It costs** | $20 per 1,000 reviews, $1 per 1,000 from 7 December 2026, + $0.001 per run. Optional scheduled monitoring: +$0.15 per check ($0.005 from 7 December 2026) (one-off runs never pay it). Apify also bills the supplier Actor `automation-lab/g2-scraper` that this robot runs for you, at its own price (about $5.75 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to G2 or write reviews |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `productUrls` | array | G2 product page URLs to monitor for new reviews. |
| `currentReviews` | array | Skip the chained fetch and pass review data directly. |
| `previousReviews` | array | Reviews from the prior run; used to identify new feedback when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained G2 reviews actor", "authorization": "publ`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |

## Example output

A row as shown in the Actor's README:

```json
{
  "review_id": "13826181",
  "subject_id": "https://www.g2.com/products/notion/reviews",
  "author": "(hidden here)",
  "rating": 5,
  "text": "I use Notion to organize all my client tasks, portals, and to-dos, as well as to assign tasks to teammates and communicate with clients....",
  "published_at": "2026-10-20T23:50:05.027Z",
  "reviewId": "13826181",
  "title": "Notion Keeps Client Work, Team Tasks, and Calendars Perfectly Organized",
  "nps": 10,
  "starRating": 5,
  "reviewText": "I use Notion to organize all my client tasks, portals, and to-dos, as well as to assign tasks to teammates and communicate with clients....",
  "publishedAt": "2026-10-20T23:50:05.027Z",
  "submittedAt": "2026-10-20T21:50:08.218Z",
  "updatedAt": "2026-10-20T21:50:20.890Z",
  "reviewerName": "(hidden here)",
  "country": "United States",
  "region": "North America",
  "helpfulVotes": 0,
  "sourceType": "g2_incentivized",
  "responseType": "text",
  "easeOfUse": 7,
  "easeOfSetup": 7,
  "easeOfAdmin": 7,
  "qualityOfSupport": 7,
  "meetsRequirements": 7,
  "switchedFromOtherProduct": "no",
  "companySegment": 179,
  "industry": 333,
  "productId": 82623,
  "productName": "Notion",
  "productSlug": "notion",
  "url": "https://www.g2.com/products/notion/reviews/13826181",
  "record_id": "13826181",
  "change_type": "new",
  "actionable": true,
  "signals": [
    "response_needed"
  ],
  "topic": "other",
  "severity": "moderate",
  "why_it_matters": "New 5-star negative review needs attention. Worth a quick reply."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/g2-reviews-scraper").call(run_input={
    "productUrls": [
        "https://www.g2.com/products/slack/reviews",
        "https://www.g2.com/products/notion/reviews"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~g2-reviews-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"productUrls": ["https://www.g2.com/products/slack/reviews", "https://www.g2.com/products/notion/reviews"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/g2-reviews-scraper` as a tool.

Full documentation, pricing and the latest changes: [G2 Software Reviews Scraper - Ratings, Pros, Cons](https://apify.com/om_kh/g2-reviews-scraper).

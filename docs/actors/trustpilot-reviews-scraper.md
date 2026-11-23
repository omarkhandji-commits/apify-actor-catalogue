---
title: "Trustpilot Company Reviews Scraper - Rating, Text, Reviewer"
description: "Trustpilot company reviews scraper: bulk-download reviews for any company: rating, title, text, reviewer, country and date, plus the company's review count and average score. JSON, CSV or Excel, or call it as an API. No login needed. For competitor and reputation research. $0.00025 per review."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Trustpilot Company Reviews Scraper - Rating, Text, Reviewer

Trustpilot company reviews scraper: bulk-download reviews for any company: rating, title, text, reviewer, country and date, plus the company's review count and average score. JSON, CSV or Excel, or call it as an API. No login needed. For competitor and reputation research. $0.00025 per review.

**Run it on Apify:** [https://apify.com/om_kh/trustpilot-reviews-scraper](https://apify.com/om_kh/trustpilot-reviews-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Company names or Trustpilot links |
| **We do** | Read the company's Trustpilot reviews |
| **You get** | One row per review: rating, title, text, date, verified flag, reviewer country, company reply, plus the company's TrustScore, review count and reply rate, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.25 per 1,000 reviews, no start fee (lowered on 21 November 2026 from $0.60). Optional scheduled monitoring: +$0.005 per check (one-off runs never pay it). Apify also bills the supplier Actor `blackfalcondata/trustpilot-reviews-scraper` that this robot runs for you, at its own price (about $0.25 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Trustpilot or reply to reviews |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `companyUrls` | array | Trustpilot company/domain page URLs to monitor for new reviews. |
| `maxReviewsPerPlace` | integer | How many of the most recent reviews to read for each link, up to 1,000. Default: `50`. |
| `currentReviews` | array | Skip the chained fetch and pass review data directly. |
| `previousReviews` | array | Reviews from the prior run; used to identify new feedback when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Trustpilot reviews actor", "authorization`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |

## Example output

A row as shown in the Actor's README:

```json
{
  "review_id": "6acf775fc24902b85ef1000b",
  "subject_id": "https://www.trustpilot.com/review/www.nike.com",
  "author": "(hidden here)",
  "rating": 1,
  "text": "Super slecht, de kwaliteit gaat met het jaar achteruit, garantie service is vernieuwd, waardoor alles word afgewezen, zij bieden zogenaam...",
  "published_at": "2026-10-14T14:36:47.000Z",
  "type": "review",
  "reviewId": "6acf775fc24902b85ef1000b",
  "reviewUrl": "https://www.trustpilot.com/reviews/6acf775fc24902b85ef1000b",
  "companyDomain": "www.nike.com",
  "companyName": "Nike",
  "title": "Waardeloze kwaliteit, en garantie service! ",
  "contentHash": "90f825e4b7fe361df60060f1caffff5cc10c12a9e305b6f332ae8f287b261f5f",
  "language": "nl",
  "reviewSource": "Organic",
  "likes": 0,
  "publishedDate": "2026-10-14T14:36:47.000Z",
  "experiencedDate": "2026-10-12T00:00:00.000Z",
  "isVerified": false,
  "verificationLevel": "not-verified",
  "verificationSource": "invitation",
  "reviewSourceName": "Organic",
  "authorId": "(hidden here)",
  "reviewerName": "(hidden here)",
  "reviewerCountry": "(hidden here)",
  "reviewerTotalReviews": "(hidden here)",
  "reviewerIsVerified": "(hidden here)",
  "reviewerImageUrl": "(hidden here)",
  "reviewsOnSameDomain": 1,
  "hasCompanyReply": false,
  "isComplaint": true,
  "riskLevel": "high",
  "isFiltered": false,
  "isPending": false,
  "hasUnhandledReports": false,
  "companyTrustScore": 1.5,
  "companyStars": 1.5,
  "companyTotalReviews": 13181,
  "companyWebsite": "https://www.nike.com",
  "companyIsClaimed": false,
  "companyCategories": [
    "Activewear Store",
    "Shoe Store"
  ],
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/trustpilot-reviews-scraper").call(run_input={
    "companyUrls": [
        "https://www.trustpilot.com/review/www.nike.com"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~trustpilot-reviews-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"companyUrls": ["https://www.trustpilot.com/review/www.nike.com"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/trustpilot-reviews-scraper` as a tool.

Full documentation, pricing and the latest changes: [Trustpilot Company Reviews Scraper - Rating, Text, Reviewer](https://apify.com/om_kh/trustpilot-reviews-scraper).

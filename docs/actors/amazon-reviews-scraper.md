---
title: "Amazon Review Details Scraper - Ratings, Text, Verified"
description: "Amazon review details scraper: bulk-download product reviews with rating, title, text, author, verified-purchase flag and date, with a flag for unusual review spikes. Paste ASINs or product URLs; JSON, CSV, Excel or API. No login needed. Our fee $20 per 1,000 reviews + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Amazon Review Details Scraper - Ratings, Text, Verified

Amazon review details scraper: bulk-download product reviews with rating, title, text, author, verified-purchase flag and date, with a flag for unusual review spikes. Paste ASINs or product URLs; JSON, CSV, Excel or API. No login needed. Our fee $20 per 1,000 reviews + supplier.

**Run it on Apify:** [https://apify.com/om_kh/amazon-reviews-scraper](https://apify.com/om_kh/amazon-reviews-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Amazon ASINs or product links |
| **We do** | Read each product's reviews and flag unusual review spikes |
| **You get** | One row per review: rating, title, text, date, verified purchase, Vine, helpful votes and photos, plus the product's rating and review counts, plus every field the supplier returns (`source_data`) |
| **It costs** | $20 per 1,000 reviews, $0.45 per 1,000 from 2 December 2026, + $0.001 per run. Optional scheduled monitoring: +$0.45 per check ($0.008 from 2 December 2026) (one-off runs never pay it). Apify also bills the supplier Actor `axesso_data/amazon-reviews-scraper` that this robot runs for you, at its own price (about $0.90 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Amazon or write reviews |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `asins` | array | Amazon product IDs (ASINs) to monitor for new reviews. |
| `currentReviews` | array | Skip the chained Amazon fetch and pass review data directly, e.g. from your own export. |
| `previousReviews` | array | Reviews from the prior run; used to identify new feedback when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Amazon reviews actor", "authorization": "`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "review_id": "R10FATQKUW2H5Z",
  "asin": "B0BDHWDR12",
  "author": "(hidden here)",
  "rating": 5,
  "text": "Si ya has tenido uno de estos sabes que son lo máximo, si lo estás pensando COmPRALOs!",
  "published_at": "2026-10-05",
  "review_country": "United States",
  "statusCode": 200,
  "statusMessage": "FOUND",
  "productTitle": "Apple AirPods Pro (2nd Gen) Wireless Earbuds, Up to 2X More Active Noise Cancelling, Adaptive Transparency, Personalized Spatial Audio Ma...",
  "currentPage": 1,
  "sortStrategy": "recent",
  "countReviews": 6074,
  "domainCode": "com",
  "countRatings": 57974,
  "productRating": "4.7 out of 5",
  "reviewId": "R10FATQKUW2H5Z",
  "date": "Reviewed in the United States on October 5, 2026",
  "title": "Comrpalos",
  "userName": "(hidden here)",
  "numberOfHelpful": 0,
  "imageUrlList": [
    "https://m.media-amazon.com/images/I/71CroD+vt1L._SY88.jpg"
  ],
  "verified": true,
  "vine": false,
  "profilePath": "/gp/profile/amzn1.account.AFUAA7ALWFOUW5LZQTW5C3C5IBFA/ref=cm_cr_arp_d_gw_btm",
  "reviewSummary_fiveStar_percentage": 87,
  "reviewSummary_fourStar_percentage": 8,
  "reviewSummary_threeStar_percentage": 2,
  "reviewSummary_twoStar_percentage": 0,
  "reviewSummary_oneStar_percentage": 3,
  "locale_language": "es",
  "locale_country": "US",
  "record_id": "R10FATQKUW2H5Z",
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
run = client.actor("om_kh/amazon-reviews-scraper").call(run_input={
    "asins": [
        "B08N5WRWNW",
        "B0BDHWDR12"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~amazon-reviews-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"asins": ["B08N5WRWNW", "B0BDHWDR12"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/amazon-reviews-scraper` as a tool.

Full documentation, pricing and the latest changes: [Amazon Review Details Scraper - Ratings, Text, Verified](https://apify.com/om_kh/amazon-reviews-scraper).

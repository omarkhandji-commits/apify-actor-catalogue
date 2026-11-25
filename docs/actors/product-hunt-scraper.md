---
title: "Product Hunt Leaderboard Scraper - Daily Launches, Upvotes"
description: "Product Hunt leaderboard scraper: launches for any day or topic: name, tagline, description, URL, launch-day upvotes, daily/weekly/monthly rank, makers and launch date. Export to JSON, CSV, Excel or API. No login. For market research and startup lead lists. $7.50/1K launches, $1/1K from 16 Dec."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Product Hunt Leaderboard Scraper - Daily Launches, Upvotes

Product Hunt leaderboard scraper: launches for any day or topic: name, tagline, description, URL, launch-day upvotes, daily/weekly/monthly rank, makers and launch date. Export to JSON, CSV, Excel or API. No login. For market research and startup lead lists. $7.50/1K launches, $1/1K from 16 Dec.

**Run it on Apify:** [https://apify.com/om_kh/product-hunt-scraper](https://apify.com/om_kh/product-hunt-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A day or a topic on Product Hunt |
| **We do** | Read the launches of that day or topic |
| **You get** | One row per launch: name, tagline, description, link, launch-day upvotes, daily / weekly / monthly rank, makers and launch date, plus every field the supplier returns (`source_data`) |
| **It costs** | $7.50 per 1,000 launches today, $1 per 1,000 from 16 December 2026 + $0.001 per run. Optional scheduled monitoring: +$0.20 per check today, $0.006 from 16 December 2026 (one-off runs never pay it). Apify also bills the supplier Actor `logiover/product-hunt-daily-launches-scraper` that this robot runs for you, at its own price (about $3.50 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Product Hunt or upvote |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `targets` | array | Each target is either 'daily' (today's leaderboard) or a Product Hunt topic slug: artificial-intelligence, developer-tools, productivity, saas, marketing, design-tools, no-code, fintech, web3, social-media, e-commerce, analytics,…. Default: `["daily"]`. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "113249",
  "query_id": "daily",
  "title": "Tower – Git client for Mac and Windows",
  "url": "https://www.producthunt.com/products/tower",
  "text": "Over 100,000 developers and designers are more productive with Tower - the most powerful Git client for Mac and Windows.",
  "published_at": "2026-10-25T00:01:00-07:00",
  "score": 134,
  "slug": "tower",
  "tagline": "Build Better Software",
  "logoUuid": "f4448d0e-c748-49f7-ab3b-b686693f9f52.png",
  "websiteUrl": "https://www.git-tower.com",
  "cleanUrl": "git-tower.com",
  "twitterUrl": "https://x.com/gittower",
  "facebookUrl": "https://www.facebook.com/gittower",
  "instagramUrl": "https://www.instagram.com/gittower",
  "linkedinUrl": "https://www.linkedin.com/company/gittower",
  "reviewsCount": 16,
  "reviewsRating": 4.88,
  "followersCount": 452,
  "addonsCount": 0,
  "founderDetailedReviewsCount": 9,
  "categoriesCount": 4,
  "wasInYCombinator": false,
  "isNoLongerOnline": false,
  "isTopProduct": false,
  "firstLaunch": false,
  "rowType": "product",
  "launchDayScore": 132,
  "commentsCount": 2,
  "dailyRank": 5,
  "weeklyRank": 47,
  "monthlyRank": 160,
  "scrapedAt": "2026-10-26T16:45:50.282Z",
  "categories_name": [
    "Team collaboration software",
    "Git clients"
  ],
  "categories_id": [
    "37",
    "82"
  ],
  "latestLaunch_id": "1285452",
  "latestLaunch_slug": "git-flow-next",
  "latestLaunch_tagline": "Your favorite Git workflow. Reimagined.",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/product-hunt-scraper").call(run_input={
    "targets": [
        "daily",
        "artificial-intelligence"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~product-hunt-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"targets": ["daily", "artificial-intelligence"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/product-hunt-scraper` as a tool.

Full documentation, pricing and the latest changes: [Product Hunt Leaderboard Scraper - Daily Launches, Upvotes](https://apify.com/om_kh/product-hunt-scraper).

---
title: "Facebook Page Posts Scraper - Likes, Comments, Date"
description: "Scrape posts from any public Facebook page: post text, URL, publish date, reactions, comments and shares. Paste page URLs, export to JSON, CSV or Excel, or call it as an API. No login. Built for social listening, competitor research and reporting. $10/1K posts, $2.33/1K from 16 Dec."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Facebook Page Posts Scraper - Likes, Comments, Date

Scrape posts from any public Facebook page: post text, URL, publish date, reactions, comments and shares. Paste page URLs, export to JSON, CSV or Excel, or call it as an API. No login. Built for social listening, competitor research and reporting. $10/1K posts, $2.33/1K from 16 Dec.

**Run it on Apify:** [https://apify.com/om_kh/facebook-page-posts-scraper](https://apify.com/om_kh/facebook-page-posts-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Public Facebook page links |
| **We do** | Read the page's posts |
| **You get** | One row per post: text, link, date, reactions by type, comments, shares, video length, page followers and engagement rate, plus every field the supplier returns (`source_data`) |
| **It costs** | $10 per 1,000 posts today, $2.33 per 1,000 from 16 December 2026 + $0.001 per run. Optional scheduled monitoring: +$0.12 per check today, $0.005 from 16 December 2026 (one-off runs never pay it). Apify also bills the supplier Actor `memo23/facebook-page-posts-scraper` that this robot runs for you, at its own price (about $0.99 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Facebook or read private profiles and groups |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `pageUrls` | array | Full public Facebook page URLs to monitor for new posts. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "UzpfSTEwMDA0NDU0MTU0NDgyOToxMzkzNDYxMTE1NDgxOTI3OjEzOTM0NjExMTU0ODE5Mjc=",
  "query_id": "https://www.facebook.com/nike",
  "url": "https://www.facebook.com/nike/posts/1393461115481927",
  "text": "Leave your limits at the surface. #JustDoIt",
  "author": "(hidden here)",
  "published_at": "2025-09-15T16:01:59.000Z",
  "score": 8430,
  "pageId": "100044541544829",
  "isVideo": true,
  "captionsUrl": "https://scontent.fmaa2-1.fna.fbcdn.net/v/t39.2093-6/548271297_2166112247246706_6460886379719362365_n.srt?_nc_cat=103&_nc_map=urlgen_bucke...",
  "isSharedFromAnotherPage": false,
  "playableUrl": "https://video.fmaa14-1.fna.fbcdn.net/o1/v/t2/f2/m86/AQNrPdap6OftBP5OG6byX9Zra9AIeTlJgFFSnCnQtKX-YrtZwceyclf7S_s9vyochvQvd5rnHPfbDksk867Pa...",
  "videoDurationSeconds": 30,
  "legacyId": "1393461115481927",
  "feedbackId": "ZmVlZGJhY2s6MTM5MzQ2MTExNTQ4MTkyNw==",
  "commentsCount": 2699,
  "topReactionsCount": 7,
  "sharesCount": 1181,
  "timestamp": 1757952119,
  "timeSource": "story",
  "reactionLikeCount": 6966,
  "reactionLoveCount": 1209,
  "reactionCareCount": 138,
  "reactionHahaCount": 32,
  "reactionWowCount": 45,
  "reactionSadCount": 4,
  "reactionAngryCount": 36,
  "photoCount": 1,
  "additionalPhotoCount": 0,
  "isMarketplaceListing": false,
  "topLevelUrl": "https://www.facebook.com/100044541544829/posts/1393461115481927",
  "pageFollowers": 39496919,
  "pageTalkingAbout": 150441,
  "pageCheckins": 18604,
  "engagementRate": 0.0312,
  "pageAdLibrary_is_business_page_active": false,
  "pageAdLibrary_id": "15087023444",
  "user_profileUrl": "(hidden here)",
  "user_profilePic": "(hidden here)"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/facebook-page-posts-scraper").call(run_input={
    "pageUrls": [
        "https://www.facebook.com/nike"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~facebook-page-posts-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"pageUrls": ["https://www.facebook.com/nike"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/facebook-page-posts-scraper` as a tool.

Full documentation, pricing and the latest changes: [Facebook Page Posts Scraper - Likes, Comments, Date](https://apify.com/om_kh/facebook-page-posts-scraper).

---
title: "TikTok Influencer Search - Find Creators by Niche"
description: "TikTok influencer search: find creators by niche or username: followers, median views, engagement rate, posting cadence and a score with reasons. $1.60 per 1,000 creators, first 3 free. Last video included, for influencer marketing and outreach lists. No login. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# TikTok Influencer Search - Find Creators by Niche

TikTok influencer search: find creators by niche or username: followers, median views, engagement rate, posting cadence and a score with reasons. $1.60 per 1,000 creators, first 3 free. Last video included, for influencer marketing and outreach lists. No login. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/tiktok-creator-search-scraper](https://apify.com/om_kh/tiktok-creator-search-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A niche (`skincare routine`) or creators' usernames |
| **We do** | Find creators and measure their recent videos |
| **You get** | One row per creator: followers, median views of recent videos, engagement rate, how often they post, last video date, average views, likes, comments and shares per video, the hashtags they use most, their 5 latest videos found, their photo, and a score with its reasons, plus every field the supplier returns (`source_data`) |
| **It costs** | $1.60 per 1,000 qualified creators (since 21 Nov 2026; was $4) + $0.002 per verified business contact. Apify also bills the supplier Actor this robot runs for you, at its own price (about $0.30 per 1,000 results). The first 3 creators of every run are free of this robot's fee |
| **It does not** | Sign in to TikTok or send messages to creators |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Niches or hashtags to search for creators in, e.g. 'home coffee roasting'. Default: `["productivity apps"]`. |
| `usernames` | array | Creators you already have. Default: `["khaby.lame"]`. |
| `minFollowers` | integer | Skip creators below this follower count. |
| `maxFollowers` | integer | Skip creators above this follower count. |
| `minMedianRecentViews` | integer | Skip creators whose recent videos median below this view count. Default: `0`. |
| `languages` | array | Keep only creators in these languages, e.g. en, fr, es. |
| `activeWithinDays` | integer | Exclude creators with no video published in this many days. Default: `90`. |
| `requireContact` | boolean | Only deliver creators where a public business contact was found (TikTok bios rarely carry one — default off). Default: `false`. |
| `maxResults` | integer | Stop after this many qualified creators. Default: `100`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only creators not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "username": "(hidden here)",
  "profile_url": "https://www.tiktok.com/@khaby.lame",
  "nickname": "(hidden here)",
  "followers": 163000000,
  "follower_band": "mega",
  "following": "(hidden here)",
  "likes_total": -1594967296,
  "videos_count": 1357,
  "verified": true,
  "median_recent_views": 87500000,
  "engagement_rate": 0.0514,
  "posting_cadence_days": 385,
  "last_video_at": "2026-08-06T16:32:00Z",
  "videos_sampled": 5,
  "top_video_url": "https://www.tiktok.com/@khaby.lame/video/6965122051178892549",
  "qualification_score": 65,
  "score_reasons": [
    "median recent views 87,500,000 (30 pts)",
    "engagement rate 5.14% (20 pts)"
  ]
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/tiktok-creator-search-scraper").call(run_input={
    "keywords": [
        "productivity apps"
    ],
    "usernames": [
        "khaby.lame"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~tiktok-creator-search-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["productivity apps"], "usernames": ["khaby.lame"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/tiktok-creator-search-scraper` as a tool.

Full documentation, pricing and the latest changes: [TikTok Influencer Search - Find Creators by Niche](https://apify.com/om_kh/tiktok-creator-search-scraper).

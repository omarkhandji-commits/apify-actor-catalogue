---
title: "TikTok Keyword Search Scraper - Views, New Videos"
description: "TikTok keyword search scraper: scrape TikTok search results for any keyword: caption, video URL, author, views, likes, comments, shares and date, with a flag for fast-rising videos. No login needed. For trend research, UGC discovery and brand research. $5 per 1,000 videos."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# TikTok Keyword Search Scraper - Views, New Videos

TikTok keyword search scraper: scrape TikTok search results for any keyword: caption, video URL, author, views, likes, comments, shares and date, with a flag for fast-rising videos. No login needed. For trend research, UGC discovery and brand research. $5 per 1,000 videos.

**Run it on Apify:** [https://apify.com/om_kh/tiktok-search-scraper](https://apify.com/om_kh/tiktok-search-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords |
| **We do** | Search TikTok for each keyword |
| **You get** | One row per video: caption, link, author, followers, views, likes, comments, shares, saves, date, length, hashtags and music, with a flag for fast-rising videos, plus every field the supplier returns (`source_data`) |
| **It costs** | $5 per 1,000 videos + $0.001 per run. Optional scheduled monitoring: +$0.10 per check (one-off runs never pay it). Apify also bills the supplier Actor `deepmine/tiktok-search-api` that this robot runs for you, at its own price (about $0.25 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in, use your account, or read private content |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Brand, product or keyword phrases to monitor across TikTok search. Default: `["your brand", "competitor name"]`. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "7674665914113297685",
  "query_id": "your brand",
  "url": "https://www.tiktok.com/@rotartcreations12/video/7674665914113297685",
  "text": "Indoor signage with premium backlighting ✨🔥 Elegant, bold and designed to make your brand stand out beautifully. 💯 We don’t just do signa...",
  "author": "(hidden here)",
  "published_at": "2026-08-16T16:23:33Z",
  "score": 4766,
  "matchedKeywords": [
    "your brand"
  ],
  "embedUrl": "https://www.tiktok.com/embed/v2/7674665914113297685",
  "shortDesc": "Indoor signage with premium backlighting ✨🔥 Elegant, bold and designed to make your brand stand out beautifully. 💯 We do…",
  "captionLanguage": "en",
  "duration": 20,
  "width": 576,
  "height": 1024,
  "definition": "540p",
  "cover": "https://p19-common-sign.tiktokcdn-us.com/tos-alisg-p-0037/osDBWP9alVPE7oMiHUAw25Y5BBIaAiChxBYAI~tplv-tiktokx-origin.image?dr=9636&x-expir...",
  "dynamicCover": "https://p16-common-sign.tiktokcdn-us.com/tos-alisg-p-0037/o4eSoFD0jIDrwQAqCDEI5PEAxA9AeqAGAVfAXE~tplv-tiktokx-origin.image?dr=9636&x-expi...",
  "videoUrl": "https://www.tiktok.com/aweme/v1/play/?faid=1988&file_id=9db8f7a1cec74799a3b2a54a62896806&is_play_url=1&item_id=7674665914113297685&line=0...",
  "hasCaptions": true,
  "captionLanguages": [
    "eng-US"
  ],
  "isAiGenerated": false,
  "placeName": "Rot-art Creations",
  "placeAddress": "12 Dare St, Ikotun, 100265, Lagos, Nigeria",
  "authorId": "(hidden here)",
  "nickname": "(hidden here)",
  "verified": false,
  "avatar": "(hidden here)",
  "authorBio": "(hidden here)",
  "authorPrivate": "(hidden here)",
  "followers": 14300,
  "following": "(hidden here)",
  "plays": 154000,
  "comments": 211,
  "shares": 1165,
  "bookmarks": 2788,
  "reposts": 0,
  "hashtags": [
    "rotartcreations12",
    "indoorsignage"
  ],
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/tiktok-search-scraper").call(run_input={
    "keywords": [
        "your brand",
        "competitor name"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~tiktok-search-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["your brand", "competitor name"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/tiktok-search-scraper` as a tool.

Full documentation, pricing and the latest changes: [TikTok Keyword Search Scraper - Views, New Videos](https://apify.com/om_kh/tiktok-search-scraper).

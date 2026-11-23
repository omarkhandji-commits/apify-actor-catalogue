---
title: "YouTube Creator Lead Finder - Views, Niche, Email"
description: "Find YouTube creators by niche or keyword: subscribers, median recent views, language, posting cadence and public business contact, each backed by its source URL. Export to JSON, CSV or Excel, or call it as an API. No login needed. Our fee $4 per 1,000 creators + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# YouTube Creator Lead Finder - Views, Niche, Email

Find YouTube creators by niche or keyword: subscribers, median recent views, language, posting cadence and public business contact, each backed by its source URL. Export to JSON, CSV or Excel, or call it as an API. No login needed. Our fee $4 per 1,000 creators + supplier.

**Run it on Apify:** [https://apify.com/om_kh/youtube-creator-lead-finder](https://apify.com/om_kh/youtube-creator-lead-finder) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A niche or a list of YouTube channels |
| **We do** | Measure each creator and keep only the ones worth contacting |
| **You get** | One row per creator: exact subscribers, country, engagement rate, median recent views, posting cadence, last video, social links and a public business contact with its source link, plus a score with its reasons |
| **It costs** | $4 per 1,000 qualified creators + $0.002 per verified contact + $0.001 per run. Apify also bills the supplier Actor `streamers/youtube-channel-scraper` that this robot runs for you, at its own price (about $1.30 per 1,000 results). An item that returns an error is never charged |
| **It does not** | Read emails hidden behind YouTube's "View email address" button, or send messages |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Niches to search for creators in, e.g. 'home coffee roasting'. Default: `["productivity apps"]`. |
| `channelUrls` | array | Channels you already have. Default: `["https://www.youtube.com/@mkbhd"]`. |
| `minSubscribers` | integer | Skip channels below this subscriber count. |
| `maxSubscribers` | integer | Skip channels above this subscriber count. |
| `minMedianRecentViews` | integer | Skip channels whose recent videos median below this view count. Default: `0`. |
| `languages` | array | Keep only channels in these languages, e.g. en, fr, es. |
| `activeWithinDays` | integer | Exclude channels with no video published in this many days. Default: `90`. |
| `requireContact` | boolean | Off (default): deliver every qualified channel, contact or not -- 'contact-verified' is billed only when one is actually found. Default: `false`. |
| `maxResults` | integer | Stop after this many qualified creators. Default: `100`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only creators not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "channel_id": "UC8raOG7HXJoCUygx219fU4A",
  "channel_url": "http://www.youtube.com/@ChrisLawley",
  "title": "Christopher Lawley",
  "subscriber_band": "macro",
  "subscriber_count": 206000,
  "median_recent_views": 23183,
  "engagement_rate": 0.0316,
  "videos_last_90d": 15,
  "posting_cadence_days": 9.7,
  "country": "United States",
  "total_views": 40432232,
  "video_count": 450,
  "joined_at": "2015-10-15",
  "last_video_at": "2026-09-14T18:28:20Z",
  "topics": [
    "Technology",
    "Tech"
  ],
  "social_links": [
    "https://instagram.com/chrislawley_"
  ],
  "website_links": [
    "https://chrislawley.me",
    "https://theuntitled.site"
  ],
  "business_contact": {
    "email": "(hidden here)",
    "kind": "business_email",
    "source": "https://www.youtube.com/channel/UC8raOG7HXJoCUygx219fU4A",
    "verification_level": "mx_valid"
  },
  "qualification_score": 98,
  "score_reasons": [
    "median recent views 23,183 (30 pts)",
    "engagement rate 3.16% (20 pts)"
  ]
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/youtube-creator-lead-finder").call(run_input={
    "keywords": [
        "productivity apps"
    ],
    "channelUrls": [
        "https://www.youtube.com/@mkbhd"
    ],
    "maxResults": 10
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~youtube-creator-lead-finder/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["productivity apps"], "channelUrls": ["https://www.youtube.com/@mkbhd"], "maxResults": 10}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/youtube-creator-lead-finder` as a tool.

Full documentation, pricing and the latest changes: [YouTube Creator Lead Finder - Views, Niche, Email](https://apify.com/om_kh/youtube-creator-lead-finder).

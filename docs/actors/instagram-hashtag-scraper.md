---
title: "Instagram Hashtag Media Scraper - Images, Likes, Captions"
description: "Instagram hashtag media scraper: posts for any hashtag with image links (every carousel image), caption, post URL, author, likes, comments, media type and date, plus a flag for fast-rising hashtags. No login. For UGC discovery and campaigns. $6 per 1,000 posts. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Instagram Hashtag Media Scraper - Images, Likes, Captions

Instagram hashtag media scraper: posts for any hashtag with image links (every carousel image), caption, post URL, author, likes, comments, media type and date, plus a flag for fast-rising hashtags. No login. For UGC discovery and campaigns. $6 per 1,000 posts. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/instagram-hashtag-scraper](https://apify.com/om_kh/instagram-hashtag-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Instagram hashtags |
| **We do** | Read the public posts under each hashtag |
| **You get** | One row per post: image links, caption, link, author, likes, comments, media type and date, with a flag for hashtags rising fast, plus every field the supplier returns (`source_data`) |
| **It costs** | $6 per 1,000 posts + $0.001 per run. Optional scheduled monitoring: +$0.10 per check (one-off runs never pay it). Apify also bills the supplier Actor `apify/instagram-hashtag-scraper` that this robot runs for you, at its own price (about $2.60 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in, use your account, or read private content |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `hashtags` | array | Hashtags to monitor (with or without the # sign). Default: `["yourbrand", "campaignhashtag"]`. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "4014445264270600311",
  "query_id": "yourbrand",
  "title": "Reusable and travel perfect tumblers for our friends @becoffeeyeg available in their beautiful bee inspired coffee shop located in South...",
  "url": "https://www.instagram.com/p/De2LLLLGSh3/",
  "text": "Reusable and travel perfect tumblers for our friends @becoffeeyeg available in their beautiful bee inspired coffee shop located in South...",
  "author": "(hidden here)",
  "published_at": "2026-10-23T18:13:09.000Z",
  "score": -1,
  "inputUrl": "https://www.instagram.com/explore/tags/yourbrand",
  "type": "Sidecar",
  "shortCode": "De2LLLLGSh3",
  "mentions": "(hidden here)",
  "commentsCount": 3,
  "dimensionsHeight": 1530,
  "dimensionsWidth": 1148,
  "displayUrl": "https://scontent-bru2-1.cdninstagram.com/v/t51.82787-15/861786141_18119909449953535_3972716117899935621_n.jpg?stp=dst-jpg_e35_tt6&_nc_cat...",
  "locationName": "Louvre at Century Park",
  "locationId": "100701295029138",
  "ownerFullName": "(hidden here)",
  "ownerId": "(hidden here)",
  "productType": "carousel_container",
  "paidPartnership": false,
  "isPinned": false,
  "childPosts_count": 2,
  "childPosts_displayUrl": [
    "https://scontent-bru2-1.cdninstagram.com/v/t51.82787-15/861786141_18119909449953535_3972716117899935621_n.jpg?stp=dst-jpg_e35_tt6&_nc_cat...",
    "https://scontent-bru2-1.cdninstagram.com/v/t51.82787-15/862035060_18119909458953535_2984578742549606434_n.jpg?stp=dst-jpg_e35_tt6&_nc_cat..."
  ],
  "childPosts_id": [
    "4014438736239680620",
    "4014438739771204441"
  ],
  "taggedUsers_count": "(hidden here)",
  "taggedUsers_username": "(hidden here)",
  "taggedUsers_full_name": "(hidden here)",
  "musicInfo_audio_canonical_id": "0",
  "coauthorProducers_username": "(hidden here)",
  "coauthorProducers_full_name": "(hidden here)"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/instagram-hashtag-scraper").call(run_input={
    "hashtags": [
        "yourbrand",
        "campaignhashtag"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~instagram-hashtag-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"hashtags": ["yourbrand", "campaignhashtag"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/instagram-hashtag-scraper` as a tool.

Full documentation, pricing and the latest changes: [Instagram Hashtag Media Scraper - Images, Likes, Captions](https://apify.com/om_kh/instagram-hashtag-scraper).

---
title: "TikTok Hashtag Posts Scraper - Views, Creator Bio, Music"
description: "Scrape TikTok videos for any hashtag: caption, URL, views, comments, shares, saves, duration and music, plus each creator's name, bio, total likes and verified badge, with a flag for hashtags taking off. Export to JSON, CSV or Excel, or use the API. No login. $5 per 1,000 videos."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# TikTok Hashtag Posts Scraper - Views, Creator Bio, Music

Scrape TikTok videos for any hashtag: caption, URL, views, comments, shares, saves, duration and music, plus each creator's name, bio, total likes and verified badge, with a flag for hashtags taking off. Export to JSON, CSV or Excel, or use the API. No login. $5 per 1,000 videos.

**Run it on Apify:** [https://apify.com/om_kh/vigia-tiktok-hashtag-monitor](https://apify.com/om_kh/vigia-tiktok-hashtag-monitor) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | TikTok hashtags |
| **We do** | Read the videos posted under each hashtag |
| **You get** | One row per video: caption, link, views, comments, shares, saves, length and music, plus the creator's name, bio, total likes and verified badge, plus every field the supplier returns (`source_data`) |
| **It costs** | $5 per 1,000 videos + $0.001 per run. Optional scheduled monitoring: +$0.10 per check (one-off runs never pay it). Apify also bills the supplier Actor `apidojo/tiktok-scraper` that this robot runs for you, at its own price (about $0.30 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in, use your account, or read private content |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `hashtags` | array | Hashtags to monitor (with or without the # sign). |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "7672826736773565718",
  "query_id": "tiktokmademebuyit",
  "title": "It just stays on the skin so much longer so no more filling in brows #browtint #eyebrowtint #eyebrows #makeuphacks",
  "url": "https://www.tiktok.com/@emilyruthc/video/7672826736773565718",
  "text": "It just stays on the skin so much longer so no more filling in brows #browtint #eyebrowtint #eyebrows #makeuphacks",
  "author": "(hidden here)",
  "published_at": "2026-08-11T17:26:33.000Z",
  "score": 17038,
  "engagement_rate": 0.0045,
  "hashtag_count": 4,
  "inputSource": "https://www.tiktok.com/tag/tiktokmademebuyit",
  "views": 5021888,
  "comments": 57,
  "shares": 1144,
  "bookmarks": 4318,
  "hashtags": [
    "browtint",
    "eyebrowtint"
  ],
  "uploadedAt": 1786469193,
  "channel_id": "6683923853058524166",
  "channel_name": "Emily Ruth",
  "channel_bio": "emilyruthc.contact@gmail.com\nyes it's me again x",
  "channel_avatar": "(hidden here)",
  "channel_verified": true,
  "channel_url": "https://www.tiktok.com/@emilyruthc",
  "channel_likes": 0,
  "video_width": 576,
  "video_height": 1024,
  "video_ratio": "540p",
  "video_duration": 12.734,
  "video_url": "https://v45-eu.tiktokcdn.com/a8ed545f5059ce41df083a51f13b744c/6ae0d48d/video/tos/no1a/tos-no1a-ve-0068c001-no/ow7BdEnyvl1BAQiWiTVIG7ztYEB...",
  "video_cover": "https://p16-common-sign.tiktokcdn.com/tos-no1a-p-0037-no/oYH9IgtgGNGOrDb2AIeTAkICNLbO4ULIeIsjet~tplv-tiktokx-origin.image?dr=1370&refresh...",
  "song_id": "7611931557393861392",
  "song_title": "âm thanh gốc - cent2_aep",
  "song_artist": "CENT",
  "song_duration": 23,
  "song_cover": "https://p16-common-sign.tiktokcdn.com/tos-alisg-avt-0068/f5068a609f9862a866d51849da480cc5~tplv-tiktokx-cropcenter-q:1080:1080:q70.webp?dr..."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/vigia-tiktok-hashtag-monitor").call(run_input={
    "hashtags": [
        "tiktokmademebuyit",
        "yourbrand"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~vigia-tiktok-hashtag-monitor/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"hashtags": ["tiktokmademebuyit", "yourbrand"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/vigia-tiktok-hashtag-monitor` as a tool.

Full documentation, pricing and the latest changes: [TikTok Hashtag Posts Scraper - Views, Creator Bio, Music](https://apify.com/om_kh/vigia-tiktok-hashtag-monitor).

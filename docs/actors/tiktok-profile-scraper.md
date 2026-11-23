---
title: "TikTok Profile Videos Scraper - Views, Followers, Music"
description: "TikTok profile videos scraper: every video of any TikTok profile with caption, URL, views, likes, comments, shares, saves, duration, music and hashtags, plus the creator's followers, bio and verified badge on every row. Paste usernames or profile URLs. No login. $5 per 1,000 videos."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# TikTok Profile Videos Scraper - Views, Followers, Music

TikTok profile videos scraper: every video of any TikTok profile with caption, URL, views, likes, comments, shares, saves, duration, music and hashtags, plus the creator's followers, bio and verified badge on every row. Paste usernames or profile URLs. No login. $5 per 1,000 videos.

**Run it on Apify:** [https://apify.com/om_kh/tiktok-profile-scraper](https://apify.com/om_kh/tiktok-profile-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | TikTok usernames or profile links |
| **We do** | Read the videos of each public profile |
| **You get** | One row per video: caption, link, views, likes, comments, shares, saves, length, music and hashtags, plus the creator's followers, bio and verified badge, plus every field the supplier returns (`source_data`) |
| **It costs** | $5 per 1,000 videos + $0.001 per run. Optional scheduled monitoring: +$0.08 per check (one-off runs never pay it). Apify also bills the supplier Actor `apidojo/tiktok-scraper` that this robot runs for you, at its own price (about $0.30 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in, use your account, or read private content |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `profiles` | array | TikTok usernames or profile URLs to monitor for new videos (with or without @). |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "7699192373955284238",
  "query_id": "nike",
  "title": "Rise and shine. #JaMorant",
  "url": "https://www.tiktok.com/@nike/video/7699192373955284238",
  "text": "Rise and shine. #JaMorant",
  "author": "(hidden here)",
  "published_at": "2026-10-21T18:39:08.000Z",
  "score": 4691,
  "engagement_rate": 0.1099,
  "hashtag_count": 1,
  "inputSource": "https://www.tiktok.com/@nike",
  "views": 47642,
  "comments": 60,
  "shares": 186,
  "bookmarks": 301,
  "hashtags": [
    "jamorant"
  ],
  "uploadedAt": 1792607948,
  "channel_id": "208464585232822272",
  "channel_name": "Nike",
  "channel_bio": "Just Do It.",
  "channel_avatar": "(hidden here)",
  "channel_verified": false,
  "channel_followers": 9330767,
  "channel_following": "(hidden here)",
  "channel_videos": 1128,
  "channel_likes": 50305509,
  "video_width": 720,
  "video_height": 1280,
  "video_ratio": "720p",
  "video_duration": 12.654,
  "video_url": "https://v45.tiktokcdn-us.com/b5259fdd9c7aab9f791379c1ed55dbf1/6adfd76d/video/tos/useast5/tos-useast5-pve-0068-tx/oYLi2BqtIt5CpWbAaZwBfBlI...",
  "video_cover": "https://p16-common-sign.tiktokcdn-us.com/tos-useast5-p-0068-tx/oMvZYGaMIyg8E4kAVkDgLQBBoiAAtBsiIE6AP~tplv-tiktokx-cropcenter-q:300:400:q7...",
  "song_id": "7573330551328622609",
  "song_title": "Moment of Peace",
  "song_artist": "vozes da natureza & Sons da Natureza & Nature in the world & sublime vocal",
  "song_album": "Magical Nature",
  "song_duration": 56,
  "song_cover": "https://p16-common.tiktokcdn-us.com/tos-alisg-v-2774/oICRFwCMEFAAPaeAISEDsJfiIAf6ABqMDgzP9z~tplv-tiktokx-cropcenter:720:720.jpeg?dr=9584&...",
  "poi_poiName": "Portland Oregon White Stag Sign",
  "poi_address": "70 NW Couch St, Portland, OR, 97209, United States",
  "poi_cityCode": "5746545",
  "poi_cityName": "Portland",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/tiktok-profile-scraper").call(run_input={
    "profiles": [
        "nike",
        "khaby.lame"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~tiktok-profile-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"profiles": ["nike", "khaby.lame"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/tiktok-profile-scraper` as a tool.

Full documentation, pricing and the latest changes: [TikTok Profile Videos Scraper - Views, Followers, Music](https://apify.com/om_kh/tiktok-profile-scraper).

---
title: "YouTube Playlist & Channel Videos Scraper - Exact Views"
description: "YouTube playlist and channel videos scraper: youTube channel scraper: up to 5,000 videos, 2,000 Shorts and 1,000 live streams per channel with exact views, likes, comment counts, dates, description, hashtags and thumbnail, plus the channel's subscribers, country, links and join date. No API key."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# YouTube Playlist & Channel Videos Scraper - Exact Views

YouTube playlist and channel videos scraper: youTube channel scraper: up to 5,000 videos, 2,000 Shorts and 1,000 live streams per channel with exact views, likes, comment counts, dates, description, hashtags and thumbnail, plus the channel's subscribers, country, links and join date. No API key.

**Run it on Apify:** [https://apify.com/om_kh/youtube-channel-videos-scraper](https://apify.com/om_kh/youtube-channel-videos-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | YouTube channels or playlists |
| **We do** | Read the channel's videos, Shorts and live streams, newest first |
| **You get** | One row per video: exact views, likes, comments, date, length, description, hashtags and thumbnail, plus the channel's subscribers, country, links and join date |
| **It costs** | **$0.50 per 1,000 videos** (from 4 December 2026: $1.50 per 1,000) + $0.001 per run. The first 10 results of every run are free. No supplier fee |
| **It does not** | Need a YouTube API key, download videos, or give transcripts (for those, use our YouTube Transcript Scraper) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `channels` | array | YouTube channel handles (@name), channel URLs or channel IDs to scrape the latest videos from. |
| `maxVideos` | integer | How many videos to return per channel (0 to 5,000). Default: `30`. |
| `maxShorts` | integer | How many Shorts to return per channel (0 to 2,000). Default: `0`. |
| `maxStreams` | integer | How many live streams (past and current) to return per channel (0 to 1,000). Default: `0`. |
| `sortBy` | string | YouTube's own order on the channel page, applied to videos, Shorts and live streams. Default: `"newest"`. |
| `oldestVideoDate` | string | YYYY-MM-DD. |
| `includeChannelInfo` | boolean | Add the channel's profile to every row: description, links, country, join date, subscribers, total views, video count, avatar, banner and verified badge. Default: `true`. |
| `currentVideos` | array | Optional: pass video data you already have instead of fetching it from YouTube. |
| `previousVideos` | array | Videos from the prior run; used to identify changes when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "YouTube channel RSS feed (first-party)", "authori`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "type": "video",
  "channel_subscribers": 523000000,
  "channel_handle": "(hidden here)",
  "description": "I can't believe they actually agreed to this\n\nDownload PUBG MOBILE and enjoy the most popular mobile game with multiple gameplays. Happy...",
  "hashtags": [
    "1"
  ],
  "thumbnail_url": "https://i.ytimg.com/vi/AoN1K4c7VKE/hqdefault.jpg",
  "channel_id": "UCX6OQ3DkcsbYNE6H8uQQuVA",
  "channel_title": "MrBeast",
  "channel_url": "http://www.youtube.com/@MrBeast",
  "channel_description": "SUBSCRIBE FOR A COOKIE!\nNew MrBeast or MrBeast Gaming video every single Saturday at noon eastern time!\nAccomplishments:\n- Raised $20,000...",
  "channel_links": [
    "https://instagram.com/mrbeast",
    "https://twitter.com/MrBeast"
  ],
  "channel_country": "United States",
  "channel_joined_at": "2012-02-19",
  "channel_total_views": 144353642443,
  "channel_video_count": 1009,
  "channel_avatar_url": "(hidden here)",
  "channel_banner_url": "https://yt3.googleusercontent.com/mHMO_eEMp0dPvh0ADwXhPXNYb_GnjSVsLI8biqF1CpxT8OPl7izhNQsDPD3JHhd5y5Mg9GrP=w2560-fcrop64=1,00005a57ffffa5...",
  "channel_is_verified": true,
  "video_id": "AoN1K4c7VKE",
  "channel": "@MrBeast",
  "title": "Survive 30 Days Stranded With Your Ex, Win $250,000",
  "view_count": 141185423,
  "like_count": 2577519,
  "comment_count": 152000,
  "like_count_rounded": false,
  "published_at": "2026-03-07T00:00:00+00:00",
  "url": "https://www.youtube.com/watch?v=AoN1K4c7VKE",
  "record_id": "AoN1K4c7VKE",
  "change_type": "new",
  "why_it_matters": "A tracked item changed."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/youtube-channel-videos-scraper").call(run_input={
    "channels": [
        "@MrBeast",
        "@mkbhd"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~youtube-channel-videos-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"channels": ["@MrBeast", "@mkbhd"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/youtube-channel-videos-scraper` as a tool.

Full documentation, pricing and the latest changes: [YouTube Playlist & Channel Videos Scraper - Exact Views](https://apify.com/om_kh/youtube-channel-videos-scraper).

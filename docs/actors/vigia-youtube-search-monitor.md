---
title: "YouTube Search Scraper API - Videos, Views, $0.50/1K"
description: "YouTube search scraper API: up to 1,000 videos per keyword with exact views, duration, channel, handle, verified badge, 4K/CC/live badges and date, plus Shorts and live streams. Filters: upload date, length, HD, 4K, subtitles. No API key. $0.50 per 1,000 videos."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# YouTube Search Scraper API - Videos, Views, $0.50/1K

YouTube search scraper API: up to 1,000 videos per keyword with exact views, duration, channel, handle, verified badge, 4K/CC/live badges and date, plus Shorts and live streams. Filters: upload date, length, HD, 4K, subtitles. No API key. $0.50 per 1,000 videos.

**Run it on Apify:** [https://apify.com/om_kh/vigia-youtube-search-monitor](https://apify.com/om_kh/vigia-youtube-search-monitor) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords, with optional filters (upload date, length, HD, 4K, subtitles) |
| **We do** | Search YouTube |
| **You get** | One row per video: exact views, length, channel, handle, verified badge, 4K / CC / live badges, date and rank, plus Shorts and live streams |
| **It costs** | **$0.50 per 1,000 videos** + $0.001 per run. The first 10 results of every run are free. No supplier fee |
| **It does not** | Need a YouTube API key. YouTube stops one search after a few hundred results: split the search for more |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchTerms` | array | Words to search on YouTube, one search per line. |
| `startUrls` | array | Paste youtube.com/results links: the words and the filters of each link are used as they are. |
| `maxResults` | integer | Videos per search term, in YouTube's order. Default: `50`. |
| `maxShorts` | integer | Also return Shorts for the same words (YouTube's own Shorts filter). Default: `0`. |
| `maxLiveStreams` | integer | Also return streams that are live now for the same words. Default: `0`. |
| `sortBy` | string | YouTube no longer offers 'upload date' and 'rating' orders. 'Newest first' reorders the results this run read; combine it with Upload date. Default: `"relevance"`. |
| `uploadDate` | string | Only videos uploaded in the last hour, today, this week, this month or this year (YouTube's own filter). |
| `videoDuration` | string | Only short (under 4 min), medium (4-20 min) or long (over 20 min) videos. |
| `videoType` | string | YouTube's type filter. Default: `"video"`. |
| `features` | array | Keep only videos with every feature picked (YouTube's own filters). |
| `publishedAfter` | string | YYYY-MM-DD. |
| `includeVideoDetails` | boolean | Open each video for its likes, comment count, exact publication date, full description, hashtags and the channel's subscribers and handle. Default: `false`. |
| `currentItems` | array | Optional: pass records you already have instead of fetching them from YouTube. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "YouTube public endpoints (first-party)", "authori`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "https://www.youtube.com/watch?v=ix9cRaBkVe0",
  "query_id": "python tutorial",
  "title": "Python Full Course for free 🐍",
  "url": "https://www.youtube.com/watch?v=ix9cRaBkVe0",
  "text": "python #tutorial #beginners Python tutorial for beginners' full course 2024 *Learn Python in 1 HOUR* ...",
  "author": "(hidden here)",
  "published_at": "2024-10-24T07:00:48+00:00",
  "videoId": "ix9cRaBkVe0",
  "channelId": "UC4SVo0Ue36XCfOyb5Lh1viQ",
  "channelUrl": "https://www.youtube.com/channel/UC4SVo0Ue36XCfOyb5Lh1viQ",
  "viewCount": 13095866,
  "duration": "12:00:00",
  "durationSeconds": 43200,
  "publishedTimeText": "2 years ago",
  "thumbnailUrl": "https://i.ytimg.com/vi/ix9cRaBkVe0/hq720.jpg?sqp=-oaymwEXCNAFEJQDSFryq4qpAwkIARUAAIhCGAE=&rs=AOn4CLA3zOqGqeejlG_66zpDnm9pzuH_2Q",
  "channelHandle": "(hidden here)",
  "channelIsVerified": true,
  "channelAvatarUrl": "(hidden here)",
  "badges": [
    "Fundraiser"
  ],
  "isLive": false,
  "hasCaptions": false,
  "is4K": false,
  "type": "video",
  "searchRank": 1,
  "searchQuery": "python tutorial",
  "scrapedAt": "2026-10-24T19:00:50Z",
  "extra_channelIsVerified": true,
  "extra_badges": [
    "Fundraiser"
  ],
  "extra_isLive": false,
  "extra_hasCaptions": false,
  "extra_is4K": false
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/vigia-youtube-search-monitor").call(run_input={
    "searchTerms": [
        "python tutorial"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~vigia-youtube-search-monitor/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["python tutorial"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/vigia-youtube-search-monitor` as a tool.

Full documentation, pricing and the latest changes: [YouTube Search Scraper API - Videos, Views, $0.50/1K](https://apify.com/om_kh/vigia-youtube-search-monitor).

---
title: "YouTube Comments & Replies Scraper - Playlists $0.40/1K"
description: "YouTube comments and replies scraper: youTube comments scraper: up to 50,000 comments per video with replies, newest or top first, date limit, exact likes, reply count, author channel, pinned and creator-heart flags. $0.40 per 1,000, first 10 per run free. No API key, no login. JSON, CSV, API, MCP."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# YouTube Comments & Replies Scraper - Playlists $0.40/1K

YouTube comments and replies scraper: youTube comments scraper: up to 50,000 comments per video with replies, newest or top first, date limit, exact likes, reply count, author channel, pinned and creator-heart flags. $0.40 per 1,000, first 10 per run free. No API key, no login. JSON, CSV, API, MCP.

**Run it on Apify:** [https://apify.com/om_kh/youtube-comments-scraper](https://apify.com/om_kh/youtube-comments-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | YouTube video links, or a channel or playlist link (its latest videos) |
| **We do** | Read the video's comments, and their replies if you want |
| **You get** | One row per comment (up to 50,000 per video): text, author, likes, reply count, date and a direct link |
| **It costs** | **$0.40 per 1,000 comments** + $0.001 per run. The first 10 results of every run are free. A video with comments turned off costs nothing. No supplier fee |
| **It does not** | Need a YouTube API key or sign in. Old comments have approximate dates (YouTube shows "3 weeks ago") |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `videoUrls` | array | YouTube video URLs, Shorts URLs or 11-character video IDs. |
| `maxVideosPerChannel` | integer | For a channel or playlist link: how many of its latest videos to read (channels newest first, playlists in their own order). Default: `5`. |
| `maxComments` | integer | How many comments to collect per video (1 to 50,000). Default: `100`. |
| `sortBy` | string | Newest first (default) or YouTube's Top comments order. Default: `"newest"`. |
| `includeReplies` | boolean | Open every comment thread and return its replies too. Default: `false`. |
| `maxRepliesPerComment` | integer | How many replies to read under each comment (1 to 1,000). Default: `100`. |
| `oldestCommentDate` | string | YYYY-MM-DD. |
| `currentItems` | array | Optional: pass records you already have instead of fetching them from YouTube. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "YouTube public endpoints (first-party)", "authori`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "UgxWpJDtrX1S7spcAnF4AaABAg",
  "query_id": "https://www.youtube.com/watch?v=dQw4w9WgXcQ",
  "url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ&lc=UgxWpJDtrX1S7spcAnF4AaABAg",
  "text": "Rick Roll Meme",
  "author": "(hidden here)",
  "published_at": "2026-10-24T21:31:13+00:00",
  "score": 0,
  "commentId": "UgxWpJDtrX1S7spcAnF4AaABAg",
  "type": "comment",
  "videoId": "dQw4w9WgXcQ",
  "videoTitle": "Rick Astley - Never Gonna Give You Up (Official Video) (4K Remaster)",
  "likeCount": 0,
  "replyCount": 0,
  "authorChannelId": "(hidden here)",
  "authorHandle": "(hidden here)",
  "authorUrl": "(hidden here)",
  "authorThumbnail": "(hidden here)",
  "authorIsChannelOwner": "(hidden here)",
  "authorIsVerified": "(hidden here)",
  "isHearted": false,
  "isPinned": false,
  "isEdited": false,
  "publishedTimeText": "8 minutes ago",
  "commentsCount": 2460536,
  "likes": 0,
  "extra_likeCount": 0,
  "extra_replyCount": 0,
  "extra_authorIsChannelOwner": "(hidden here)",
  "extra_authorIsVerified": "(hidden here)",
  "extra_isHearted": false,
  "extra_isPinned": false,
  "extra_isEdited": false
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/youtube-comments-scraper").call(run_input={
    "videoUrls": [
        "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~youtube-comments-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"videoUrls": ["https://www.youtube.com/watch?v=dQw4w9WgXcQ"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/youtube-comments-scraper` as a tool.

Full documentation, pricing and the latest changes: [YouTube Comments & Replies Scraper - Playlists $0.40/1K](https://apify.com/om_kh/youtube-comments-scraper).

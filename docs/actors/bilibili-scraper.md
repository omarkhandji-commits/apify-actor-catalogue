---
title: "Bilibili Video Scraper - Search, Creators, Danmaku $4/1K"
description: "Bilibili video scraper: bilibili (B站) scraper by keyword (with date window), video link, creator or the popular board: views, likes, coins, favorites, shares, danmaku and comment counts, tags, creator followers and verified title, top comments and danmaku. No login. $4 per 1,000 videos."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Bilibili Video Scraper - Search, Creators, Danmaku $4/1K

Bilibili video scraper: bilibili (B站) scraper by keyword (with date window), video link, creator or the popular board: views, likes, coins, favorites, shares, danmaku and comment counts, tags, creator followers and verified title, top comments and danmaku. No login. $4 per 1,000 videos.

**Run it on Apify:** [https://apify.com/om_kh/bilibili-scraper](https://apify.com/om_kh/bilibili-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords, video links, creator UIDs, or nothing for the popular-now board |
| **We do** | Read Bilibili (哔哩哔哩) without a login |
| **You get** | Videos (views, likes, coins, favorites, shares, comments, danmaku count, tags, top comments), creators (followers, videos, likes) and danmaku bullet comments |
| **It costs** | $4 per 1,000 videos or creators, $0.20 per 1,000 danmaku, + $0.001 per run. The first 10 videos or creators of every run are free. No supplier fee |
| **It does not** | Sign in to Bilibili or download videos |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Search Bilibili videos for these words (Chinese or English): 数码测评, 原神, iPhone.. Default: `["数码测评"]`. |
| `sortBy` | string | Bilibili's own sort for keyword searches. Default: `"relevance"`. |
| `duration` | string | Bilibili's duration filter for keyword searches. Default: `"any"`. |
| `publishedAfter` | string | Keyword searches only: keep videos published on or after this day (YYYY-MM-DD, UTC). |
| `publishedBefore` | string | Keyword searches only: keep videos published on or before this day (YYYY-MM-DD, UTC). |
| `maxVideosPerKeyword` | integer | Bilibili shows at most 1,000 videos for one search. Default: `100`. |
| `searchAliases` | array | Other spellings searched next to every keyword and merged without duplicates, e.g. the Chinese name of a Latin brand (耐克 for Nike). |
| `videoUrls` | array | Optional. bilibili.com/video/BV... links, BV ids or av ids. |
| `popular` | boolean | Also get Bilibili's 'popular now' (热门) videos. Default: `false`. |
| `maxPopularVideos` | integer | How many videos of the popular board. Default: `100`. |
| `creators` | array | Optional. |
| `creatorVideos` | array | Optional. |
| `creatorVideosSortBy` | string | Bilibili's own order on the creator's space page. Default: `"newest"`. |
| `maxVideosPerCreator` | integer | Uploads read per creator, 40 per page. Default: `100`. |
| `creatorKeywords` | array | Optional. |
| `maxCreatorsPerKeyword` | integer | How many creators per creator keyword. Default: `20`. |
| `includeDetails` | boolean | Read each video page: coins, shares, parts, original or repost, and the creator's followers, uploads and likes. Default: `true`. |
| `includeTopComments` | boolean | Add the hottest comments of each video (Bilibili shows 3 to visitors who are not logged in). Default: `false`. |
| `maxRepliesPerComment` | integer | With Top comments on: also read the replies under each top comment (replyThread). 0 = none. Default: `0`. |
| `maxDanmakuPerVideo` | integer | Bullet comments (弹幕) to deliver per video, with their time in the video and posting date. 0 = none. Default: `0`. |
| `sentimentAnalysis` | boolean | Tag every video (title and description) and every top comment with sentiment (positive, neutral, negative) and a score from -1 to 1, from a Chinese and English word list. Default: `false`. |
| `onlyNewVideos` | boolean | Monitor mode: the first run delivers everything, later runs with the same search deliver only new videos. Default: `false`. |
| `memoryName` | string | Names the saved list of delivered videos (with Only new videos). |
| `maxTotalChargeUsd` | number | The run delivers no more rows than this amount pays for. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "video",
  "bvid": "BV1wxnB6aE4E",
  "aid": 117479099602589,
  "title": "现在二手平台都变成这样了？？？",
  "description": "-",
  "url": "https://www.bilibili.com/video/BV1wxnB6aE4E",
  "thumbnailUrl": "https://i1.hdslb.com/bfs/archive/2406500a6b5223d77c0c9f84eb5ad00d40eefe93.jpg",
  "durationSeconds": 271,
  "publishedAt": "2026-10-22T10:00:00Z",
  "category": "数码",
  "tags": [
    "测评",
    "数码"
  ],
  "views": 157177,
  "likes": 5433,
  "favorites": 1095,
  "comments": 82,
  "danmakuCount": 80,
  "creatorId": "99902757",
  "creatorName": "科技晨Pro",
  "creatorUrl": "https://space.bilibili.com/99902757",
  "searchTotalResults": 1000,
  "searchQuery": "数码测评",
  "isOriginal": false,
  "parts": 1,
  "cid": 42929359532,
  "coins": 2005,
  "shares": 9,
  "creatorFollowers": 715986,
  "creatorVideos": 176,
  "creatorLikes": 2833343,
  "creatorVerified": true,
  "creatorVerifiedTitle": "bilibili 知名科技UP主"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/bilibili-scraper").call(run_input={
    "keywords": [
        "数码测评"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~bilibili-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["数码测评"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/bilibili-scraper` as a tool.

Full documentation, pricing and the latest changes: [Bilibili Video Scraper - Search, Creators, Danmaku $4/1K](https://apify.com/om_kh/bilibili-scraper).

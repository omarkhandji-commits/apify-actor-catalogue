---
title: "Reddit Keyword Search Scraper - Posts, Comments, Upvotes"
description: "Reddit keyword search scraper: search all of Reddit for any keyword or brand: post title, body, link, subreddit, author and flair, upvotes, upvote ratio, comments, awards, media and date, plus optional comments. JSON, CSV, Excel, API, n8n or Make. Our fee $9 per 1,000 posts + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Reddit Keyword Search Scraper - Posts, Comments, Upvotes

Reddit keyword search scraper: search all of Reddit for any keyword or brand: post title, body, link, subreddit, author and flair, upvotes, upvote ratio, comments, awards, media and date, plus optional comments. JSON, CSV, Excel, API, n8n or Make. Our fee $9 per 1,000 posts + supplier.

**Run it on Apify:** [https://apify.com/om_kh/reddit-posts-comments-scraper](https://apify.com/om_kh/reddit-posts-comments-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords or brand names |
| **We do** | Search all of Reddit, and optionally read the comments |
| **You get** | One row per post: title, text, link, subreddit, author, upvotes, upvote ratio, comments, awards, media and date, plus sentiment, topic and our free lead score (asks for a tool, complains, talks price), plus every field the supplier returns (`source_data`) |
| **It costs** | $9 per 1,000 posts, no start fee (lowered on 21 November 2026 from $10). Optional scheduled monitoring: +$0.014 per check (one-off runs never pay it). Apify also bills the supplier Actor `fatihtahta/reddit-scraper-search-fast` that this robot runs for you, at its own price (about $1.49 per 1,000 rows; if it is down, the backup `automation-lab/reddit-scraper` runs instead, about $1.15 per 1,000 posts + $0.003 per run). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Need a Reddit API key, sign in, or post for you |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Brand, product, or competitor keywords to monitor across Reddit posts. |
| `includeComments` | boolean | Return Reddit comments as well as posts. Default: `false`. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "1xngm90",
  "query_id": "notion",
  "title": "Notion Calendar finally has an iPad app",
  "url": "https://www.reddit.com/r/Notion/comments/1xngm90/notion_calendar_finally_has_an_ipad_app/",
  "text": "https://preview.redd.it/v5mrjaxlcjzh1.png?width=480&format=png&auto=webp&s=fbafcefabba85e9125197a...",
  "author": "(hidden)",
  "published_at": "2026-11-04T06:01:24.000Z",
  "score": 2,
  "kind": "post",
  "sentiment_label": "neutral",
  "sentiment_confidence": 0.39,
  "sentiment_score_normalized": 0.37,
  "content_category_label": "Computer Software and Applications",
  "content_category_path": [
    "Technology & Computing",
    "Computing",
    "Computer Software and Applications"
  ],
  "content_category_confidence": 0.94,
  "content_category_match_type": "multi_signal",
  "upvote_ratio": 1,
  "num_comments": 0,
  "subreddit": "Notion",
  "permalink": "/r/Notion/comments/1xngm90/notion_calendar_finally_has_an_ipad_app/",
  "old_reddit_url": "https://old.reddit.com/r/Notion/comments/1xngm90/notion_calendar_finally_has_an_ipad_app/",
  "flair": "Notion Calendar",
  "over_18": false,
  "is_self": true,
  "is_video": false,
  "is_gallery": false,
  "domain": "self",
  "subreddit_id": "t5_hds7r",
  "subreddit_name_prefixed": "r/Notion",
  "age_hours": 0.0605,
  "retrieved_at": "2026-11-04T06:05:01.858Z",
  "media_type": "text",
  "has_media": false,
  "gallery_count": 0,
  "title_length": 39,
  "body_length": 254,
  "word_count": 36,
  "score_per_hour": 33.0579,
  "comments_per_hour": 0,
  "is_deleted_or_removed": false,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/reddit-posts-comments-scraper").call(run_input={
    "keywords": [
        "notion",
        "airtable"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~reddit-posts-comments-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["notion", "airtable"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/reddit-posts-comments-scraper` as a tool.

Full documentation, pricing and the latest changes: [Reddit Keyword Search Scraper - Posts, Comments, Upvotes](https://apify.com/om_kh/reddit-posts-comments-scraper).

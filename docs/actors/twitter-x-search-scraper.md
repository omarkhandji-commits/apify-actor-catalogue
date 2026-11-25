---
title: "Twitter Keyword Scraper & Monitor - X Posts, Likes, Replies"
description: "Twitter keyword scraper and monitor: scrape X (Twitter) search results for any keyword, hashtag or query: post text, URL, author, likes, reposts, replies and date. Export to JSON, CSV or Excel, or call it as an API. No login or X API key needed. $1 per 1,000 posts, $0.32 from 16 Dec 2026."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Twitter Keyword Scraper & Monitor - X Posts, Likes, Replies

Twitter keyword scraper and monitor: scrape X (Twitter) search results for any keyword, hashtag or query: post text, URL, author, likes, reposts, replies and date. Export to JSON, CSV or Excel, or call it as an API. No login or X API key needed. $1 per 1,000 posts, $0.32 from 16 Dec 2026.

**Run it on Apify:** [https://apify.com/om_kh/twitter-x-search-scraper](https://apify.com/om_kh/twitter-x-search-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords, hashtags or X search queries |
| **We do** | Search X (Twitter), then clean and check every post |
| **You get** | One row per post: text, link, author, likes, reposts, replies and date, as JSON, CSV or Excel, plus every field the supplier returns (`source_data`) |
| **It costs** | $1 per 1,000 posts today, $0.32 per 1,000 from 16 December 2026. Apify also bills the supplier Actor this robot runs for you, at its own price (about $0.25 per 1,000), so about **$1.25 per 1,000 in total today ($0.57 from 16 December 2026)**. The first 10 results of every run are free of this robot's fee |
| **It does not** | Sign in to X or need an X API key |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Brand, product or keyword phrases to monitor across X/Twitter search. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "2114106678157459532",
  "query_id": "your brand",
  "url": "https://x.com/hallwayhighway/status/2114106678157459532",
  "text": "@piersmorgan Let's just remember who you had on your show after allegations. Fiona Harvey, Kevin Spacey, Russell Brand, Cuba Gooding Jr,...",
  "author": "(hidden here)",
  "published_at": "1792877284000",
  "timestamp": 1792877284000,
  "conversationId": "2114085104536699014",
  "replyCount": 0,
  "quoteCount": 0,
  "repostCount": 0,
  "favouriteCount": 0,
  "author_userId": "(hidden here)",
  "author_screenName": "(hidden here)",
  "author_profileImageUrl": "(hidden here)"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/twitter-x-search-scraper").call(run_input={
    "keywords": [
        "openai",
        "anthropic"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~twitter-x-search-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["openai", "anthropic"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/twitter-x-search-scraper` as a tool.

Full documentation, pricing and the latest changes: [Twitter Keyword Scraper & Monitor - X Posts, Likes, Replies](https://apify.com/om_kh/twitter-x-search-scraper).

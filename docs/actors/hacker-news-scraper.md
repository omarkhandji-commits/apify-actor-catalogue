---
title: "Hacker News Data Scraper - Stories, Comments, Points"
description: "Hacker News data scraper: search stories and comments by keyword, or read the front page, newest, Ask, Show, jobs and best. Filters by date, points and comments, up to 10,000 per search. Official HN APIs, so it never breaks. $0.19 per 1,000 stories and comments."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Hacker News Data Scraper - Stories, Comments, Points

Hacker News data scraper: search stories and comments by keyword, or read the front page, newest, Ask, Show, jobs and best. Filters by date, points and comments, up to 10,000 per search. Official HN APIs, so it never breaks. $0.19 per 1,000 stories and comments.

**Run it on Apify:** [https://apify.com/om_kh/hacker-news-scraper](https://apify.com/om_kh/hacker-news-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords, with optional dates and minimum points |
| **We do** | Search the official Hacker News (Algolia) API |
| **You get** | One row per story or comment: title, link, author, points, comment count, date, text and the Hacker News link |
| **It costs** | $0.19 per 1,000 stories and comments + $0.001 per run. Optional scheduled monitoring: +$0.002 per check (one-off runs never pay it). The first 10 results of every run are free. No supplier fee |
| **It does not** | Sign in, vote or post |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Brand, product, or tech keywords to monitor across Hacker News stories and comments. Default: `["your product", "competitor name"]`. |
| `sections` | array | Read whole Hacker News sections, with or without keywords. |
| `maxStories` | integer | 1 to 10,000. Default: `100`. |
| `contentType` | string | For keyword searches. Default: `"all"`. |
| `sortBy` | string | For keyword searches. Default: `"date"`. |
| `dateFrom` | string | YYYY-MM-DD, inclusive. |
| `dateTo` | string | YYYY-MM-DD, inclusive. |
| `minPoints` | integer | Keep only stories with at least this score. |
| `minComments` | integer | Keep only stories with at least this many comments. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Hacker News official Algolia API (first-party)", `. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "50225165",
  "query_id": "your product",
  "title": "Show HN: Claude Code(and others) embedded in your app",
  "url": "https://github.com/gtanczyk/genaicode",
  "text": "I started this project in 2024 when I got fascinated with LLMs, and what I did was a coding agent (CLI -&gt; interactive -&gt; GUI). I al...",
  "author": "(hidden here)",
  "published_at": "2026-10-24T20:54:27Z",
  "score": 1,
  "points": 1,
  "num_comments": 0,
  "story_id": "50225165",
  "hn_url": "https://news.ycombinator.com/item?id=50225165",
  "type": "story",
  "domain": "github.com",
  "created_at_i": 1792875267,
  "rank_in_list": 25,
  "extra_num_comments": 0
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/hacker-news-scraper").call(run_input={
    "keywords": [
        "your product",
        "competitor name"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~hacker-news-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["your product", "competitor name"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/hacker-news-scraper` as a tool.

Full documentation, pricing and the latest changes: [Hacker News Data Scraper - Stories, Comments, Points](https://apify.com/om_kh/hacker-news-scraper).

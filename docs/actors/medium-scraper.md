---
title: "Medium Scraper - Articles, Full Text, Tags $2/1K"
description: "Scrape Medium articles from writers, publications (custom domains too) and tags: title, link, author, date, tags, cover image, full text, word count and reading time. Keyword and date filters, only-new mode for schedules. No login. $2 per 1,000 articles."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Medium Scraper - Articles, Full Text, Tags $2/1K

Scrape Medium articles from writers, publications (custom domains too) and tags: title, link, author, date, tags, cover image, full text, word count and reading time. Keyword and date filters, only-new mode for schedules. No login. $2 per 1,000 articles.

**Run it on Apify:** [https://apify.com/om_kh/medium-scraper](https://apify.com/om_kh/medium-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Medium writers, publications or tags |
| **We do** | Read their articles, including publications on their own domain |
| **You get** | One row per article: title, link, author, dates, tags, cover image, full text, word count and reading time |
| **It costs** | $2 per 1,000 articles + $0.001 per run. Feeds that fail and articles your filters drop are never charged. No supplier fee |
| **It does not** | Sign in to Medium |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `users` | array | Medium writers: @handle, handle or profile link (medium.com/@name or name.medium.com). Default: `["@JoeyColeman"]`. |
| `publications` | array | Medium publications: slug (better-programming), medium.com link or the publication's own domain (betterprogramming.pub). Default: `["better-programming"]`. |
| `tags` | array | Medium tags (artificial-intelligence, python, startup...). |
| `feedUrls` | array | Any Medium-hosted site or feed link. |
| `keywords` | array | Keep only articles whose title, tags or text contain one of these words (case-insensitive). |
| `publishedAfter` | string | Keep only articles published on or after this date. |
| `includeHtml` | boolean | Adds the original HTML of each article (with images and links) next to the plain text. Default: `false`. |
| `onlyNewArticles` | boolean | Each run delivers only articles you have not received yet. Default: `false`. |
| `monitorId` | string | With 'Only new articles', keeps separate memories for separate schedules. |
| `maxTotalChargeUsd` | number | The run stops before it would cost more than this. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "article",
  "articleId": "ccbd1d3f9fd7",
  "title": "GPT Function Calling: 5 Underrated Use Cases",
  "url": "https://medium.com/better-programming/gpt-function-calling-5-underrated-use-cases-ccbd1d3f9fd7",
  "author": "(hidden here)",
  "publishedAt": "2023-11-10T17:33:58Z",
  "updatedAt": "2023-11-20T20:55:28.826Z",
  "tags": [
    "automation",
    "llm"
  ],
  "imageUrl": "https://cdn-images-1.medium.com/max/1024/1*doghMb44J43LgPYtkUCByw.jpeg",
  "fullText": true,
  "wordCount": 1677,
  "readingTimeMinutes": 6,
  "text": "OpenAI’s “Function Calling” might be the most groundbreaking yet under appreciated feature released by any software company… ever.\nWhat a...",
  "feedType": "publication",
  "feedName": "Better Programming - Medium",
  "feedInput": "better-programming",
  "feedUrl": "https://medium.com/feed/better-programming"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/medium-scraper").call(run_input={
    "users": [
        "@JoeyColeman"
    ],
    "publications": [
        "better-programming"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~medium-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"users": ["@JoeyColeman"], "publications": ["better-programming"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/medium-scraper` as a tool.

Full documentation, pricing and the latest changes: [Medium Scraper - Articles, Full Text, Tags $2/1K](https://apify.com/om_kh/medium-scraper).

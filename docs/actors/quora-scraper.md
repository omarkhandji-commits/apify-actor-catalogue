---
title: "Quora Search Scraper - Questions, Answers, Views by Keyword"
description: "Quora search scraper: scrape Quora for any keyword: question, URL, answer text, author, views, shares, comments and date. Export to JSON, CSV or Excel, or call it from the API, n8n or Make. No login needed. For audience research, content ideas and SEO topics. $2.50 per 1,000 questions and answers."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Quora Search Scraper - Questions, Answers, Views by Keyword

Quora search scraper: scrape Quora for any keyword: question, URL, answer text, author, views, shares, comments and date. Export to JSON, CSV or Excel, or call it from the API, n8n or Make. No login needed. For audience research, content ideas and SEO topics. $2.50 per 1,000 questions and answers.

**Run it on Apify:** [https://apify.com/om_kh/quora-scraper](https://apify.com/om_kh/quora-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords |
| **We do** | Search Quora for questions and answers |
| **You get** | One row per question or answer: title, text, author, views, shares, comments, date and link, plus every field the supplier returns (`source_data`) |
| **It costs** | $2.50 per 1,000 questions and answers + $0.001 per run. Optional scheduled monitoring: +$0.18 per check (one-off runs never pay it). Apify also bills the supplier Actor `fatihtahta/quora-scraper` that this robot runs for you, at its own price (about $0.99 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Quora or post answers |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Brand, product or topic phrases to monitor across Quora search. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "https://donewiththebullshit.quora.com/Why-are-Democrats-trying-to-remove-God-from-America-393",
  "query_id": "your brand",
  "title": "Why are Democrats trying to remove God from America?",
  "url": "https://donewiththebullshit.quora.com/Why-are-Democrats-trying-to-remove-God-from-America-393",
  "text": "no one is They are trying to keep it out of schools, healthcare and laws that affect all as not everyone follows your brand of fairytales...",
  "author": "(hidden here)",
  "published_at": "2022-12-30T07:32:49.039000Z",
  "score": 95,
  "comments": 0,
  "shares": 0,
  "views": 843,
  "record_type": "answer",
  "source_context_seed_type": "keyword",
  "source_context_source_url": "https://www.quora.com/search?q=your%20brand&type=answer",
  "source_context_scraped_at": "2026-10-24T21:38:25.980664Z",
  "source_context_search_type": "Answer",
  "source_context_search_time_filter": "All Time",
  "status_has_results": true,
  "author_url": "(hidden here)",
  "author_credential": "(hidden here)",
  "metrics_comments": 0,
  "metrics_shares": 0,
  "flags_is_locked": true,
  "flags_is_sensitive": false,
  "question_id": 122894425,
  "question_slug": "Why-are-Democrats-trying-to-remove-God-from-America-9",
  "question_url": "https://donewiththebullshit.quora.com/Why-are-Democrats-trying-to-remove-God-from-America",
  "question_posted_at": "2022-07-19T20:55:26.943000Z",
  "question_metrics_answers": 606,
  "question_metrics_followers": 9,
  "question_metrics_comments": 6,
  "question_author_name": "(hidden here)",
  "question_space_name": "Done with the Bullshit?",
  "question_space_url": "https://donewiththebullshit.quora.com",
  "question_flags_is_locked": true,
  "question_flags_is_sensitive": false,
  "answer_id": 407877183,
  "answer_access_option": "free",
  "answer_metrics_comments": 0,
  "answer_metrics_shares": 0
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/quora-scraper").call(run_input={
    "keywords": [
        "your brand",
        "your product category"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~quora-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["your brand", "your product category"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/quora-scraper` as a tool.

Full documentation, pricing and the latest changes: [Quora Search Scraper - Questions, Answers, Views by Keyword](https://apify.com/om_kh/quora-scraper).

---
title: "Reddit Subreddit Posts Scraper - Upvotes, Comments, Media"
description: "Get the newest posts of any subreddit: title, text, link, author and flair, upvotes, upvote ratio, comment count, awards, images and video, plus optional comments and a spike signal for sudden activity. Export to JSON, CSV or Excel, or use the API. Our fee $0.75 per 1,000 posts + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Reddit Subreddit Posts Scraper - Upvotes, Comments, Media

Get the newest posts of any subreddit: title, text, link, author and flair, upvotes, upvote ratio, comment count, awards, images and video, plus optional comments and a spike signal for sudden activity. Export to JSON, CSV or Excel, or use the API. Our fee $0.75 per 1,000 posts + supplier.

**Run it on Apify:** [https://apify.com/om_kh/reddit-subreddit-scraper](https://apify.com/om_kh/reddit-subreddit-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Subreddit names or links |
| **We do** | Read the newest posts of each subreddit, and optionally their comments |
| **You get** | One row per post: title, text, link, author and flair, upvotes, upvote ratio, comments, awards, images and video, with a spike signal for sudden activity, plus sentiment, topic and our free lead score (asks for a tool, complains, talks price), plus every field the supplier returns (`source_data`) |
| **It costs** | $0.75 per 1,000 posts, no start fee (lowered on 21 November 2026 from $10). Optional scheduled monitoring: +$0.005 per check (one-off runs never pay it). Apify also bills the supplier Actor `fatihtahta/reddit-scraper-search-fast` that this robot runs for you, at its own price (about $1.49 per 1,000 rows; if it is down, the backup `automation-lab/reddit-scraper` runs instead, about $1.15 per 1,000 posts + $0.003 per run). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Need a Reddit API key, sign in, or post for you |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `subreddits` | array | Subreddit names to watch (with or without the r/ prefix), e.g. 'SaaS' or 'r/startups'. |
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
  "record_id": "1xngj6e",
  "query_id": "SaaS",
  "title": "Just crossed the $100 MRR with my app 🥳🥳",
  "url": "https://www.reddit.com/r/SaaS/comments/1xngj6e/just_crossed_the_100_mrr_with_my_app/",
  "text": "After several months of continuous development of my app, Glance, listening to early raiders on w...",
  "author": "(hidden)",
  "published_at": "2026-11-04T05:56:40.000Z",
  "score": 2,
  "kind": "post",
  "query": "https://www.reddit.com/r/SaaS/new/",
  "sentiment_score": 9,
  "sentiment_label": "positive",
  "sentiment_confidence": 0.91,
  "sentiment_score_normalized": 1.19,
  "upvote_ratio": 1,
  "num_comments": 0,
  "permalink": "/r/SaaS/comments/1xngj6e/just_crossed_the_100_mrr_with_my_app/",
  "old_reddit_url": "https://old.reddit.com/r/SaaS/comments/1xngj6e/just_crossed_the_100_mrr_with_my_app/",
  "post_hint": "image",
  "is_self": false,
  "is_video": false,
  "is_gallery": false,
  "domain": "i.redd.it",
  "url_overridden_by_dest": "https://i.redd.it/hndy7tbicjzh1.jpeg",
  "subreddit_id": "t5_2qkq6",
  "subreddit_name_prefixed": "r/SaaS",
  "age_hours": 0.129,
  "retrieved_at": "2026-11-04T06:04:24.530Z",
  "has_media": true,
  "gallery_count": 0,
  "title_length": 42,
  "body_length": 618,
  "word_count": 118,
  "score_per_hour": 15.5039,
  "comments_per_hour": 0,
  "is_deleted_or_removed": false,
  "comment_to_score_ratio": 0,
  "is_high_engagement": false,
  "total_awards_received": 0,
  "author_fullname": "(hidden)",
  "served_by": "fatihtahta/reddit-scraper-search-fast",
  "buying_intent": true,
  "complaint": false,
  "mentions_price": true,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/reddit-subreddit-scraper").call(run_input={
    "subreddits": [
        "SaaS",
        "startups"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~reddit-subreddit-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"subreddits": ["SaaS", "startups"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/reddit-subreddit-scraper` as a tool.

Full documentation, pricing and the latest changes: [Reddit Subreddit Posts Scraper - Upvotes, Comments, Media](https://apify.com/om_kh/reddit-subreddit-scraper).

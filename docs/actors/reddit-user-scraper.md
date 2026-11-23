---
title: "Reddit User Scraper API - Posts, Comments, Upvotes, Flair"
description: "Scrape any Reddit user's posts: title, text, link, subreddit, upvotes, upvote ratio, comments, awards, flair, media, NSFW flag and date, plus optional comments. Paste usernames or profile URLs. Export JSON, CSV, Excel or API. No login or Reddit key. Our fee $0.75 per 1,000 posts + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Reddit User Scraper API - Posts, Comments, Upvotes, Flair

Scrape any Reddit user's posts: title, text, link, subreddit, upvotes, upvote ratio, comments, awards, flair, media, NSFW flag and date, plus optional comments. Paste usernames or profile URLs. Export JSON, CSV, Excel or API. No login or Reddit key. Our fee $0.75 per 1,000 posts + supplier.

**Run it on Apify:** [https://apify.com/om_kh/reddit-user-scraper](https://apify.com/om_kh/reddit-user-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Reddit usernames or profile links |
| **We do** | Read each user's posts, and optionally their comments |
| **You get** | One row per post: title, text, link, subreddit, upvotes, upvote ratio, comments, awards, flair, media, NSFW flag and date, plus sentiment, topic and our free lead score (asks for a tool, complains, talks price), plus every field the supplier returns (`source_data`) |
| **It costs** | Our fee is $0.75 per 1,000 posts; the optional scheduled monitoring adds $0.005 per check (one-off runs never pay it). Apify also bills the supplier Actor `fatihtahta/reddit-scraper-search-fast` that this robot runs for you, at its own price (about $1.49 per 1,000 rows; if it is down, the backup `automation-lab/reddit-scraper` runs instead, about $1.15 per 1,000 posts + $0.003 per run). |
| **It does not** | Need a Reddit API key, sign in, or read private content |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `userUrls` | array | Full Reddit user profile URLs to monitor (e.g. https://www.reddit.com/user/spez/). |
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
  "record_id": "1xiupm0",
  "query_id": "spez",
  "title": "About that login screen",
  "url": "https://www.reddit.com/r/u_spez/comments/1xiupm0/about_that_login_screen/",
  "text": "I want to talk about a big change we're making on Reddit: we're going to evolve Reddit to being a...",
  "author": "(hidden)",
  "published_at": "2026-10-29T20:08:37.000Z",
  "score": 0,
  "kind": "post",
  "query": "https://www.reddit.com/user/spez/submitted/",
  "upvote_ratio": 0.26865671641791045,
  "num_comments": 483,
  "subreddit": "u_spez",
  "permalink": "/r/u_spez/comments/1xiupm0/about_that_login_screen/",
  "old_reddit_url": "https://old.reddit.com/r/u_spez/comments/1xiupm0/about_that_login_screen/",
  "is_self": true,
  "is_video": false,
  "is_gallery": false,
  "domain": "self",
  "subreddit_id": "t5_3k30p",
  "subreddit_name_prefixed": "r/u_spez",
  "age_hours": 129.9408,
  "retrieved_at": "2026-11-04T06:05:03.863Z",
  "media_type": "text",
  "has_media": false,
  "gallery_count": 0,
  "title_length": 23,
  "body_length": 4812,
  "word_count": 831,
  "score_per_hour": 0,
  "comments_per_hour": 3.7171,
  "is_deleted_or_removed": false,
  "is_high_engagement": false,
  "total_awards_received": 10,
  "author_fullname": "(hidden)",
  "served_by": "fatihtahta/reddit-scraper-search-fast",
  "buying_intent": true,
  "complaint": true,
  "mentions_price": false,
  "is_question": false,
  "lead_score": 70,
  "lead_reasons": [
    "asks: looking for",
    "complains: doesn't work"
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/reddit-user-scraper").call(run_input={
    "userUrls": [
        "https://www.reddit.com/user/spez/"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~reddit-user-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"userUrls": ["https://www.reddit.com/user/spez/"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/reddit-user-scraper` as a tool.

Full documentation, pricing and the latest changes: [Reddit User Scraper API - Posts, Comments, Upvotes, Flair](https://apify.com/om_kh/reddit-user-scraper).

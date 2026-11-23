---
title: "Telegram Channel Posts Scraper - Views, Reactions"
description: "Telegram channel posts scraper: scrape public Telegram channels: post text, date, views, reactions, media, polls, replies, links and forwards. Channel profile and subscribers, keyword search, date and last-N-days filters. No login, no phone. $0.50 per 1,000 posts."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Telegram Channel Posts Scraper - Views, Reactions

Telegram channel posts scraper: scrape public Telegram channels: post text, date, views, reactions, media, polls, replies, links and forwards. Channel profile and subscribers, keyword search, date and last-N-days filters. No login, no phone. $0.50 per 1,000 posts.

**Run it on Apify:** [https://apify.com/om_kh/telegram-channel-scraper](https://apify.com/om_kh/telegram-channel-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Public Telegram channel names or links |
| **We do** | Read each channel's public web preview |
| **You get** | One row per post: text, date, views, reactions, photos, video flag, links and forwards, with the channel's title and subscriber count |
| **It costs** | $0.50 per 1,000 posts (lowered to $0.40 on 4 December 2026) + $0.001 per run. The last 1,000 posts of 10 channels = **$5**. No supplier fee |
| **It does not** | Read private channels, groups or member lists, or need a phone number |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `channels` | array | Public Telegram channels: t.me links, @usernames or usernames, one per line (up to 100). Default: `["https://t.me/durov", "@telegram"]`. |
| `maxPostsPerChannel` | integer | Newest posts first, 1 to 5,000. Default: `100`. |
| `searchQuery` | string | Only posts matching this keyword, using the channel's own search. |
| `postedAfter` | string | Only posts on or after this date (YYYY-MM-DD). |
| `lastNDays` | integer | 1: today's posts only. 2: today and yesterday. |
| `profileOnly` | boolean | Return one row per channel (title, description, subscribers, photo and video counts, verified badge, avatar) and no posts. Default: `false`. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "postId": 548,
  "url": "https://t.me/durov/548",
  "channel": "durov",
  "date": "2026-09-11T16:04:02+00:00",
  "text": "🤝 Telegram has become the sponsor of Codeforces — the largest competitive programming platform in the world. \n\n ⚡CodeForces organizes ove...",
  "views": 3640000,
  "reactionsTotal": 78890,
  "author": "(hidden here)",
  "hasVideo": false,
  "linkPreviewUrl": "https://codeforces.com/blog/entry/156620",
  "links": [
    "https://codeforces.com/blog/entry/156620"
  ],
  "channelTitle": "Pavel Durov",
  "channelSubscribers": 10300000,
  "channelVerified": true,
  "channelDescription": "Founder of Telegram.",
  "channelAvatarUrl": "(hidden here)"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/telegram-channel-scraper").call(run_input={
    "channels": [
        "https://t.me/durov",
        "@telegram"
    ],
    "maxPostsPerChannel": 30
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~telegram-channel-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"channels": ["https://t.me/durov", "@telegram"], "maxPostsPerChannel": 30}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/telegram-channel-scraper` as a tool.

Full documentation, pricing and the latest changes: [Telegram Channel Posts Scraper - Views, Reactions](https://apify.com/om_kh/telegram-channel-scraper).

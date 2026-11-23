---
title: "Threads Replies Scraper API - Comments, Likes $2/1K"
description: "Threads replies scraper API: every reply under any public Threads post - text, author, verified badge, likes, reply and repost counts, date, links, mentions, media. Top, recent or all, up to 10,000 per post, optional sub-replies. No login, no cookies. $2 per 1,000 replies."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Threads Replies Scraper API - Comments, Likes $2/1K

Threads replies scraper API: every reply under any public Threads post - text, author, verified badge, likes, reply and repost counts, date, links, mentions, media. Top, recent or all, up to 10,000 per post, optional sub-replies. No login, no cookies. $2 per 1,000 replies.

**Run it on Apify:** [https://apify.com/om_kh/threads-replies-scraper](https://apify.com/om_kh/threads-replies-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Links to public Threads posts |
| **We do** | Read every reply Threads shows without an account, top or most recent first |
| **You get** | One row per reply: text, author, verified badge, likes, reply and repost counts, date, links, mentions, images and videos |
| **It costs** | $2 per 1,000 replies, + $0.001 per run. The first 20 replies of every run are free. No supplier fee |
| **It does not** | Read private profiles. On very large posts Threads stops serving replies at some point, and you pay only for what was delivered |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `postUrls` | array | Links of public Threads posts, e.g. https://www.threads.com/@zuck/post/Dd1MqfcG0aH (threads.net links and bare post codes work too). Default: `["https://www.threads.com/@zuck/post/Dd1MqfcG0aH"]`. |
| `maxRepliesPerPost` | integer | 1 to 10,000. Default: `100`. |
| `sortOrder` | string | Top replies first (as Threads shows them), the most recent first, or all: both orders merged, for the most replies Threads shows without an account (slower). Default: `"top"`. |
| `includeNestedReplies` | boolean | Also return the replies-to-replies that Threads shows inline under a reply (not every sub-reply of long conversations). Default: `false`. |
| `includePost` | boolean | Add one row for the post (text, author, likes, reply count, media) before its replies. Default: `true`. |
| `postedAfter` | string | Only replies on or after this date (YYYY-MM-DD). |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "reply",
  "postUrl": "https://www.threads.com/@zuck/post/Dd1MqfcG0aH",
  "postAuthorUsername": "(hidden here)",
  "postReplyCount": 2661,
  "postLikeCount": 2754,
  "rank": 6,
  "replyId": "3996164469004254295",
  "code": "Dd1Oml3CTxX",
  "url": "https://www.threads.com/@pie_3.1415926._/post/Dd1Oml3CTxX",
  "text": "他頭貼變黑白我還以為他掛了",
  "language": "zh_TW",
  "createdAt": "2026-09-28T12:52:29Z",
  "createdAtTimestamp": 1790599949,
  "authorUsername": "(hidden here)",
  "authorFullName": "(hidden here)",
  "authorId": "(hidden here)",
  "authorIsVerified": "(hidden here)",
  "authorProfileUrl": "(hidden here)",
  "authorProfilePicUrl": "(hidden here)",
  "likeCount": 61,
  "replyCount": 1,
  "repostCount": 2,
  "quoteCount": 0,
  "shareCount": 1,
  "engagement": 65,
  "replyToUsername": "(hidden here)",
  "isLikedByPostAuthor": "(hidden here)",
  "isEdited": false,
  "isPaidPartnership": false,
  "replyControl": "everyone",
  "mediaType": "text",
  "hasMedia": false,
  "isQuotePost": false,
  "isRepost": false,
  "isDirectReply": true,
  "isByPostAuthor": "(hidden here)",
  "repliedAfterSeconds": 1017
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/threads-replies-scraper").call(run_input={
    "postUrls": [
        "https://www.threads.com/@zuck/post/Dd1MqfcG0aH"
    ],
    "maxRepliesPerPost": 50
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~threads-replies-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"postUrls": ["https://www.threads.com/@zuck/post/Dd1MqfcG0aH"], "maxRepliesPerPost": 50}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/threads-replies-scraper` as a tool.

Full documentation, pricing and the latest changes: [Threads Replies Scraper API - Comments, Likes $2/1K](https://apify.com/om_kh/threads-replies-scraper).

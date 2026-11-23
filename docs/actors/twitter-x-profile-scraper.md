---
title: "X Twitter User Profile Scraper - Posts, Followers, Views"
description: "X Twitter user profile scraper: any account's profile (followers, following, bio, location, verified type, post count) and its recent posts with text, likes, reposts, replies, quotes, views, bookmarks and date. Paste handles; JSON, CSV, Excel or API. Our fee $0.29 per 1,000 posts + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# X Twitter User Profile Scraper - Posts, Followers, Views

X Twitter user profile scraper: any account's profile (followers, following, bio, location, verified type, post count) and its recent posts with text, likes, reposts, replies, quotes, views, bookmarks and date. Paste handles; JSON, CSV, Excel or API. Our fee $0.29 per 1,000 posts + supplier.

**Run it on Apify:** [https://apify.com/om_kh/twitter-x-profile-scraper](https://apify.com/om_kh/twitter-x-profile-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | X (Twitter) handles |
| **We do** | Read each account's profile and its recent posts |
| **You get** | The profile (followers, following, bio, location, verified type, post count) and one row per post: text, likes, reposts, replies, quotes, views, bookmarks and date, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.29 per 1,000 posts, no start fee (lowered on 21 November 2026 from $10). Optional scheduled monitoring: +$0.005 per check (one-off runs never pay it). Apify also bills the supplier Actor `xquik/x-profile-scraper` that this robot runs for you, at its own price (about $0.15 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to X or need an X API key |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `handles` | array | X/Twitter handles to monitor for new posts (with or without the @ sign). |
| `currentItems` | array | Skip the chained fetch and pass posts directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained X/Twitter actor", "authorization": "publi`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "2065071905791500430",
  "query_id": "nike",
  "url": "https://x.com/Nike/status/2065071905791500430",
  "text": "Our collars are popped",
  "author": "(hidden here)",
  "published_at": "Thu Jun 11 14:01:24 +0000 2026",
  "score": 417,
  "retweetCount": 41,
  "replyCount": 65,
  "quoteCount": 4,
  "viewCount": 162661,
  "bookmarkCount": 37,
  "displayTextRange": [
    0,
    22
  ],
  "isNoteTweet": false,
  "isPinned": false,
  "isQuoteStatus": true,
  "isReply": false,
  "isRetweet": false,
  "isTranslatable": false,
  "lang": "en",
  "quotedTweetId": "2065071816536891421",
  "type": "tweet",
  "viewState": "EnabledWithCount",
  "resultType": "profileTweet",
  "edit_editableUntilMsecs": "1781190084000",
  "edit_editTweetIds": [
    "2065071905791500430"
  ],
  "quotedTweetPermalink_displayUrl": "x.com/nikefootball/s…",
  "quotedTweetPermalink_expandedUrl": "https://twitter.com/nikefootball/status/2065071816536891421",
  "quotedTweetPermalink_url": "https://t.co/U2MsqgfNI6",
  "author_id": "(hidden here)",
  "author_followers": "(hidden here)",
  "author_following": "(hidden here)",
  "author_verified": "(hidden here)",
  "author_isBlueVerified": "(hidden here)",
  "author_isVerified": "(hidden here)",
  "author_profilePicture": "(hidden here)",
  "author_profilePictureOriginal": "(hidden here)",
  "author_coverPicture": "(hidden here)",
  "author_description": "(hidden here)",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/twitter-x-profile-scraper").call(run_input={
    "handles": [
        "nike",
        "stripe"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~twitter-x-profile-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"handles": ["nike", "stripe"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/twitter-x-profile-scraper` as a tool.

Full documentation, pricing and the latest changes: [X Twitter User Profile Scraper - Posts, Followers, Views](https://apify.com/om_kh/twitter-x-profile-scraper).

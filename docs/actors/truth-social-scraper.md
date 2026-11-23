---
title: "Truth Social Scraper API - Posts, Likes, ReTruths"
description: "Truth Social scraper API: public accounts and posts with text, date, replies, ReTruths, likes, media, links, polls, hashtags and mentions. Followers and verified badge, filters by date, replies, media and only new since last run. No login. $1 per 1,000 posts."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Truth Social Scraper API - Posts, Likes, ReTruths

Truth Social scraper API: public accounts and posts with text, date, replies, ReTruths, likes, media, links, polls, hashtags and mentions. Followers and verified badge, filters by date, replies, media and only new since last run. No login. $1 per 1,000 posts.

**Run it on Apify:** [https://apify.com/om_kh/truth-social-scraper](https://apify.com/om_kh/truth-social-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Public Truth Social account names |
| **We do** | Read each account's posts, back to any date |
| **You get** | One row per post: text, date, likes, ReTruths, replies, media, links, hashtags and mentions, with the account's followers and verified badge |
| **It costs** | $1 per 1,000 posts (from 4 December 2026: $3 per 1,000) + $0.001 per run. The first 20 posts of every run are free; an account that does not exist is never charged. No supplier fee |
| **It does not** | Search by keyword or show trends (Truth Social needs a login for those) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `accounts` | array | Truth Social handles or profile links (truthsocial.com/@handle), one per line (up to 50). Default: `["realDonaldTrump"]`. |
| `maxPostsPerAccount` | integer | Newest first, 1 to 5,000. Default: `100`. |
| `postedAfter` | string | Only posts on or after this date (YYYY-MM-DD). |
| `includeReplies` | boolean | Also return the account's replies to other posts. Default: `false`. |
| `onlyReplies` | boolean | Keep only the posts the account wrote in reply to someone. Default: `false`. |
| `onlyMedia` | boolean | Keep only posts with a photo or a video. Default: `false`. |
| `onlyNewPosts` | boolean | Remember the newest post of each account and return only what was posted since the previous run. Default: `false`. |
| `olderThanPostId` | string | Read the timeline from just under a known post ID, to continue an earlier export. |
| `postUrls` | array | Post links or post IDs to fetch one by one, instead of or in addition to whole timelines. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "postId": "117496430405406772",
  "url": "https://truthsocial.com/@realDonaldTrump/117496430405406772",
  "createdAt": "2026-10-24T14:47:27.153Z",
  "text": "RT: https://truthsocial.com/users/realDonaldTrump/statuses/117495828914407705Georgia: See you at 7 P.M. MAKE AMERICA GREAT AGAIN! Preside...",
  "isRetruth": false,
  "isReply": false,
  "isQuote": true,
  "replies": 678,
  "retruths": 2161,
  "likes": 8910,
  "linkUrl": "https://www.youtube.com/live/9eW9_If62pc?si=oQjVlT916OMjbXkH",
  "linkTitle": "LIVE: President Trump Holds a Rally in Macon, GA - 10/24/26",
  "mentions": "(hidden here)",
  "language": "en",
  "contentHtml": "<p><span class=\"quote-inline\"><br/>RT: https://truthsocial.com/users/realDonaldTrump/statuses/117495828914407705</span>Georgia: See you a...",
  "quoteId": "117495828914407705",
  "linkImage": "https://static-assets-1.truthsocial.com/tmtg:prime-ts-assets/cache/preview_cards/images/078/310/207/original/e23c906f45f5e9fc.jpg",
  "isPinned": false,
  "isSensitive": false,
  "visibility": "public",
  "linkDescription": "Join RSBN LIVE as we give you exclusive on the ground coverage of President Trump's Rally in Macon, GA. Subscribe on Rumble: https://rumb...",
  "linkProvider": "www.youtube.com",
  "mediaCount": 0,
  "isSponsored": false,
  "upvotes": 8910,
  "downvotes": 0,
  "accountHandle": "(hidden here)",
  "accountName": "Donald J. Trump",
  "accountFollowers": 13131819,
  "accountVerified": true,
  "accountFollowing": "(hidden here)",
  "accountPostsCount": 37552,
  "accountCreatedAt": "2022-02-11T16:16:57.705Z",
  "accountAvatar": "(hidden here)",
  "accountWebsite": "www.DonaldJTrump.com",
  "accountId": "107780257626128497"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/truth-social-scraper").call(run_input={
    "accounts": [
        "realDonaldTrump"
    ],
    "maxPostsPerAccount": 40
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~truth-social-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"accounts": ["realDonaldTrump"], "maxPostsPerAccount": 40}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/truth-social-scraper` as a tool.

Full documentation, pricing and the latest changes: [Truth Social Scraper API - Posts, Likes, ReTruths](https://apify.com/om_kh/truth-social-scraper).

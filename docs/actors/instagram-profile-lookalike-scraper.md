---
title: "Instagram Lookalike Scraper - Similar Accounts & Followers"
description: "Instagram lookalike finder for influencer discovery and competitor audience mapping. Give one seed profile and get similar accounts back, with followers, engagement rate, bio contact and verification level for each match. Our fee $0.007 per profile + supplier. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Instagram Lookalike Scraper - Similar Accounts & Followers

Instagram lookalike finder for influencer discovery and competitor audience mapping. Give one seed profile and get similar accounts back, with followers, engagement rate, bio contact and verification level for each match. Our fee $0.007 per profile + supplier. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/instagram-profile-lookalike-scraper](https://apify.com/om_kh/instagram-profile-lookalike-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | One Instagram profile |
| **We do** | Find accounts similar to it and measure each one |
| **You get** | One row per similar account: followers, following, posts, business flag, verified badge, category, bio, e-mails and social links written in the bio, every bio link, profile photo, website, engagement rate, median recent likes and last post date, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.007 per profile + $0.0008 per recent post + $0.001 per run. Apify also bills the supplier Actor `apify/instagram-scraper` that this robot runs for you, at its own price (about $2.70 per 1,000 results). An item that returns an error is never charged |
| **It does not** | Sign in to Instagram or read private accounts |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `usernames` | array | Instagram usernames or full profile URLs. Default: `["nasa"]`. |
| `profileUrls` | array | Full Instagram profile URLs, if you have them instead of bare usernames. |
| `seedForLookalike` | string | One username whose Instagram-suggested similar accounts should also be fetched. |
| `lookalikeDepth` | integer | How many levels of similar accounts to expand from the seed. Default: `1`. |
| `includeRecentPosts` | boolean | Attach each profile's recent posts (likes, comments, date). Default: `false`. |
| `recentPostsCount` | integer | How many recent posts to attach per profile, when enabled. Default: `12`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only profiles not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "username": "(hidden here)",
  "profile_url": "https://www.instagram.com/nasa",
  "full_name": "(hidden here)",
  "followers": 104360501,
  "following": "(hidden here)",
  "posts_count": 4974,
  "is_business": true,
  "category": "Government Agencies",
  "bio": "Making the seemingly impossible, possible. ✨",
  "external_url": "https://www.nasa.gov/",
  "engagement_rate": 0.0022,
  "median_recent_likes": 227624,
  "last_post_at": "2026-10-10T15:15:02.000Z",
  "lookalikes": [
    {
      "username": "(hidden here)",
      "full_name": "(hidden here)",
      "is_verified": true
    },
    {
      "username": "(hidden here)",
      "full_name": "(hidden here)",
      "is_verified": true
    }
  ]
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/instagram-profile-lookalike-scraper").call(run_input={
    "usernames": [
        "nasa"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~instagram-profile-lookalike-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"usernames": ["nasa"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/instagram-profile-lookalike-scraper` as a tool.

Full documentation, pricing and the latest changes: [Instagram Lookalike Scraper - Similar Accounts & Followers](https://apify.com/om_kh/instagram-profile-lookalike-scraper).

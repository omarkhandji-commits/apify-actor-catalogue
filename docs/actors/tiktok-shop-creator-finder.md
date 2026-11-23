---
title: "TikTok Shop Creator Finder"
description: "Find TikTok Shop creators worth an affiliate invite: shop activity, engagement, category fit and public contact — with the source URL behind every field. Our fee $0.005 per creator + supplier. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# TikTok Shop Creator Finder

Find TikTok Shop creators worth an affiliate invite: shop activity, engagement, category fit and public contact — with the source URL behind every field. Our fee $0.005 per creator + supplier. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/tiktok-shop-creator-finder](https://apify.com/om_kh/tiktok-shop-creator-finder) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A niche or a list of TikTok usernames |
| **We do** | Find creators actually running TikTok Shop content and measure them |
| **You get** | One row per creator: exact followers, following, total likes and video count, bio, bio link, e-mails written in the bio, Instagram / YouTube / Facebook / X links shown in the bio, avatar, business account and category, account creation date, engagement, average likes, category fit, shop activity signals and a public business contact where one exists, every field with its source, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.005 per qualified creator (since 21 Nov 2026; was $0.03) + $0.002 per shop activity signal, + $0.001 per run. Apify also bills the supplier Actor `clockworks/tiktok-scraper` that this robot runs for you, at its own price (about $3.70 per 1,000 results). An item that returns an error is never charged |
| **It does not** | Sign in to TikTok or send invitations |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Niches or hashtags to search for shop-active creators in, e.g. 'tiktokmademebuyit' or 'skincare'. Default: `["tiktokmademebuyit"]`. |
| `usernames` | array | Creators you already have. |
| `categories` | array | Keep only creators whose recent hashtags overlap with these categories, e.g. 'beauty', 'fitness'. |
| `hasShopActivity` | boolean | Only deliver creators with at least one recent video flagged as TikTok Shop content. Default: `true`. |
| `minFollowers` | integer | Skip creators below this follower count. |
| `minMedianRecentViews` | integer | Skip creators whose recent videos median below this view count. Default: `0`. |
| `maxResults` | integer | Stop after this many qualified creators. Default: `100`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only creators not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "username": "(hidden here)",
  "profile_url": "https://www.tiktok.com/@dailynchannel",
  "nickname": "(hidden here)",
  "follower_band": "macro",
  "median_recent_views": 1670,
  "engagement_rate": 0.0347,
  "posting_cadence_days": 5.2,
  "last_video_at": "2026-10-23T19:18:19Z",
  "shop_active": true,
  "affiliate_signal": "observed",
  "public_contact": {
    "email": "(hidden here)",
    "kind": "business_email",
    "source": "https://www.tiktok.com/@dailynchannel",
    "verification_level": "published"
  },
  "qualification_score": 71,
  "score_reasons": [
    "median recent views 1,670 (1 pts)",
    "engagement rate 3.47% (20 pts)"
  ]
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/tiktok-shop-creator-finder").call(run_input={
    "keywords": [
        "tiktokmademebuyit"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~tiktok-shop-creator-finder/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["tiktokmademebuyit"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/tiktok-shop-creator-finder` as a tool.

Full documentation, pricing and the latest changes: [TikTok Shop Creator Finder](https://apify.com/om_kh/tiktok-shop-creator-finder).

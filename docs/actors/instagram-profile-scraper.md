---
title: "Instagram Profile Posts Scraper - Reels, Captions, Views"
description: "Instagram profile posts scraper: scrape the latest posts and reels of any Instagram profile: caption, post URL, comment count, video views and duration, music, mentions, location, media type and date. Paste usernames or profile URLs. No login. $6 per 1,000 posts, $1 from 16 Dec 2026."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Instagram Profile Posts Scraper - Reels, Captions, Views

Instagram profile posts scraper: scrape the latest posts and reels of any Instagram profile: caption, post URL, comment count, video views and duration, music, mentions, location, media type and date. Paste usernames or profile URLs. No login. $6 per 1,000 posts, $1 from 16 Dec 2026.

**Run it on Apify:** [https://apify.com/om_kh/instagram-profile-scraper](https://apify.com/om_kh/instagram-profile-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Instagram usernames or profile links |
| **We do** | Read the latest posts and reels of each public profile |
| **You get** | One row per post: caption, link, comments, video views and length, music, mentions, place, type and date, plus every field the supplier returns (`source_data`) |
| **It costs** | $6 per 1,000 posts today, $1 per 1,000 from 16 December 2026 + $0.001 per run. Optional scheduled monitoring: +$0.08 per check today, $0.005 from 16 December 2026 (one-off runs never pay it). Apify also bills the supplier Actor `apify/instagram-scraper` that this robot runs for you, at its own price (about $2.70 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in, use your account, or read private content |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `profileUrls` | array | Full Instagram profile URLs to monitor for new posts. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "profile_fullName": "(hidden here)",
  "profile_biography": "Just Do It.",
  "profile_externalUrl": "http://empli.fi/nike",
  "profile_followersCount": 290896326,
  "profile_followsCount": 266,
  "profile_postsCount": 1675,
  "profile_verified": true,
  "profile_private": false,
  "profile_isBusinessAccount": true,
  "profile_accountType": "business",
  "profile_businessAddress": {
    "streetAddress": "One Bowerman Dr",
    "cityName": "Beaverton, Oregon",
    "zipCode": "97005",
    "latitude": 45.5076448,
    "longitude": -122.8269159
  },
  "profile_profilePicUrlHD": "(hidden here)",
  "profile_highlightReelCount": 5,
  "profile_joinedRecently": false,
  "profile_engagement_engagementRate": 0.1349,
  "profile_engagement_avgLikes": 389964.42,
  "profile_engagement_medianLikes": 75773,
  "profile_engagement_avgComments": 2496.25,
  "profile_engagement_postsPerWeek": 2.21,
  "profile_engagement_lastPostAt": "2026-10-23T14:00:42.000Z",
  "profile_engagement_activeLast30Days": true,
  "profile_signals_followerTier": "celebrity",
  "profile_signals_hasContactInfo": false,
  "record_id": "4008651950882420385",
  "query_id": "https://www.instagram.com/nike/",
  "title": "Not everyone fits in.\n\nRaffle opens tomorrow at 7AM PST.\n\nhttps://yachty.shop\n\ndir. by me and @camhicks_",
  "url": "https://www.instagram.com/p/Dehl7Xohfah/",
  "text": "Not everyone fits in.\n\nRaffle opens tomorrow at 7AM PST.\n\nhttps://yachty.shop\n\ndir. by me and @camhicks_",
  "author": "(hidden here)",
  "published_at": "2026-10-15T18:30:48.000Z",
  "score": 192726,
  "type": "Video",
  "shortCode": "Dehl7Xohfah",
  "mentions": "(hidden here)",
  "commentsCount": 898,
  "firstComment": "These joints is fire 🔥🔥🔥🔥",
  "dimensionsHeight": 2144,
  "dimensionsWidth": 1206,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/instagram-profile-scraper").call(run_input={
    "profileUrls": [
        "https://www.instagram.com/nike/"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~instagram-profile-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"profileUrls": ["https://www.instagram.com/nike/"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/instagram-profile-scraper` as a tool.

Full documentation, pricing and the latest changes: [Instagram Profile Posts Scraper - Reels, Captions, Views](https://apify.com/om_kh/instagram-profile-scraper).

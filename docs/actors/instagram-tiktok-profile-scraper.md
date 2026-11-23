---
title: "Instagram & TikTok Profile Scraper - Followers, Bio"
description: "Get profile stats for Instagram and TikTok accounts in one run: username, followers, following, posts count, engagement and bio. Run it on a schedule to build your own follower-growth history. Export to JSON, CSV or Excel. No login needed. For influencer vetting and reporting. $6 per 1,000 profiles."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Instagram & TikTok Profile Scraper - Followers, Bio

Get profile stats for Instagram and TikTok accounts in one run: username, followers, following, posts count, engagement and bio. Run it on a schedule to build your own follower-growth history. Export to JSON, CSV or Excel. No login needed. For influencer vetting and reporting. $6 per 1,000 profiles.

**Run it on Apify:** [https://apify.com/om_kh/instagram-tiktok-profile-scraper](https://apify.com/om_kh/instagram-tiktok-profile-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Instagram and TikTok usernames |
| **We do** | Read each public profile, and compare with your last run |
| **You get** | One row per profile: username, name, followers, following, posts, bio, website, verified and business flags, plus every field the supplier returns (`source_data`) |
| **It costs** | $6 per 1,000 profiles + $0.001 per run. Optional scheduled monitoring: +$0.12 per check (one-off runs never pay it). Apify also bills the supplier Actor `dami_studio/instagram-profile-scraper` that this robot runs for you, at its own price (about $0.70 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Read private accounts. Follower history builds up only if you run it on a schedule |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `instagramUsernames` | array | Instagram usernames or profile URLs to track. |
| `tiktokUsernames` | array | TikTok usernames or profile URLs to track. |
| `youtubeUsernames` | array | YouTube channel handles (without @) or URLs to track. |
| `currentProfiles` | array | Bring your own normalized profile records instead of Vigia fetching them. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run's own change events may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Instagram profile data (via apify/instagram-scrap`. |

## Example output

A row as shown in the Actor's README:

```json
{
  "profile_id": "instagram:nike",
  "platform": "instagram",
  "username": "(hidden here)",
  "followers": 290908835,
  "posts_count": 1675,
  "latest_post_id": "4014317612986615579",
  "bio": "Just Do It.",
  "recordType": "profile",
  "inputUrl": "https://www.instagram.com/nike/",
  "id": "13460080",
  "url": "https://www.instagram.com/nike/",
  "fullName": "(hidden here)",
  "biography": "Just Do It.",
  "externalUrl": "http://empli.fi/nike",
  "followersCount": 290908835,
  "followsCount": 266,
  "postsCount": 1675,
  "verified": true,
  "private": false,
  "isBusinessAccount": true,
  "isProfessionalAccount": true,
  "profilePicUrl": "(hidden here)",
  "profilePicUrlHD": "(hidden here)",
  "highlightReelCount": 5,
  "igtvVideoCount": 20,
  "hasChannel": false,
  "joinedRecently": false,
  "fbid": "17841400602400210",
  "dataSource": "profile-api",
  "limitedData": false,
  "scrapedAt": "2026-10-25T03:16:12.671Z",
  "accountType": "business",
  "businessAddress_streetAddress": "One Bowerman Dr",
  "businessAddress_cityName": "Beaverton, Oregon",
  "businessAddress_zipCode": "97005",
  "businessAddress_latitude": 45.5076448,
  "businessAddress_longitude": -122.8269159,
  "accountAbout_available": false,
  "engagement_postsAnalysed": 12,
  "engagement_avgLikes": 387426.92,
  "engagement_medianLikes": 75729.5,
  "engagement_avgComments": 2468.42,
  "engagement_medianComments": 1285.5,
  "engagement_engagementRate": 0.134,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/instagram-tiktok-profile-scraper").call(run_input={
    "instagramUsernames": [
        "nike",
        "natgeo"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~instagram-tiktok-profile-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"instagramUsernames": ["nike", "natgeo"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/instagram-tiktok-profile-scraper` as a tool.

Full documentation, pricing and the latest changes: [Instagram & TikTok Profile Scraper - Followers, Bio](https://apify.com/om_kh/instagram-tiktok-profile-scraper).

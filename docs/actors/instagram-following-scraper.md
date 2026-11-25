---
title: "Instagram Following & Related Profiles Scraper - Full List"
description: "List every account an Instagram profile follows, or Instagram's own related-accounts suggestions, for influencer discovery and competitor research. Optional enrichment per account: followers, engagement rate, bio and public contact. No login or cookies needed. Fee $0.00005 per account + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Instagram Following & Related Profiles Scraper - Full List

List every account an Instagram profile follows, or Instagram's own related-accounts suggestions, for influencer discovery and competitor research. Optional enrichment per account: followers, engagement rate, bio and public contact. No login or cookies needed. Fee $0.00005 per account + supplier.

**Run it on Apify:** [https://apify.com/om_kh/instagram-following-scraper](https://apify.com/om_kh/instagram-following-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | One Instagram username |
| **We do** | List who that account follows, or Instagram's own suggested similar accounts |
| **You get** | One row per account (up to 50 per run). Option: followers, engagement and bio contact for up to 25 of them, plus every field the supplier returns (`source_data`) |
| **It costs** | **$0.00005 per account listed and $0.00115 per enriched profile** (since 25 November 2026; before that $0.002 and $0.004). Apify also bills the supplier Actor this robot runs for you, at its own price (about $0.50 per 1,000). The first 3 results of every run are free of this robot's fee |
| **It does not** | Sign in to Instagram or read private accounts |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `username` | string | Instagram username or profile URL to list accounts from. Default: `"natgeo"`. |
| `mode` | string | 'following' lists accounts the profile follows. 'related' returns Instagram's own similar-accounts suggestions. Default: `"following"`. |
| `maxResults` | integer | Stop after this many accounts. Default: `50`. |
| `enrichProfiles` | boolean | Adds followers, engagement and bio contact to the listed accounts (up to 25 per run): $0.00115 per enriched profile (free plan; less on paid plans). Default: `false`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only accounts not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "username": "(hidden here)",
  "profile_url": "https://www.instagram.com/mikemcgovern/",
  "full_name": "(hidden here)",
  "is_verified": true,
  "is_private": false,
  "user_id": "(hidden here)",
  "profile_pic_url": "(hidden here)",
  "enriched": false
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/instagram-following-scraper").call(run_input={
    "username": "natgeo"
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~instagram-following-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"username": "natgeo"}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/instagram-following-scraper` as a tool.

Full documentation, pricing and the latest changes: [Instagram Following & Related Profiles Scraper - Full List](https://apify.com/om_kh/instagram-following-scraper).

---
title: "Twitch Clips Scraper - Clips, View Counts, Creator Names"
description: "Scrape Twitch clips for any channel or game: clip title, URL, creator, view count, duration, game and creation date. Export to JSON, CSV or Excel, or call it from the API, n8n or Make. No login needed. Built for esports research, creator discovery and highlight curation. $5 per 1,000 clips."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Twitch Clips Scraper - Clips, View Counts, Creator Names

Scrape Twitch clips for any channel or game: clip title, URL, creator, view count, duration, game and creation date. Export to JSON, CSV or Excel, or call it from the API, n8n or Make. No login needed. Built for esports research, creator discovery and highlight curation. $5 per 1,000 clips.

**Run it on Apify:** [https://apify.com/om_kh/twitch-clips-scraper](https://apify.com/om_kh/twitch-clips-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Twitch channels or games |
| **We do** | Read their clips |
| **You get** | One row per clip: title, link, creator, game, view count, length, clipper and date, plus every field the supplier returns (`source_data`) |
| **It costs** | $5 per 1,000 clips + $0.001 per run. Optional scheduled monitoring: +$0.12 per check (one-off runs never pay it). Apify also bills the supplier Actor `automation-lab/twitch-scraper` that this robot runs for you, at its own price (about $3.45 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Twitch or download the videos |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `channels` | array | Twitch channel usernames to monitor for new clips. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "1967893419",
  "query_id": "ninja",
  "title": "Fact or Cap",
  "url": "https://www.twitch.tv/ninja/clip/PlacidTangibleKumquatBleedPurple--1vyhC3pZTChw9SR",
  "author": "(hidden here)",
  "published_at": "2026-10-21T01:46:09Z",
  "viewCount": 371,
  "durationSeconds": 30,
  "game": "Just Chatting",
  "curatorLogin": "itsxolten",
  "curatorDisplayName": "(hidden here)",
  "thumbnailUrl": "https://static-cdn.jtvnw.net/twitch-video-assets/twitch-vap-video-assets-prod-us-west-2/ca790260-d61d-4666-b37c-8c6e8362c543/landscape/th...",
  "scrapedAt": "2026-10-24T21:38:47.298Z"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/twitch-clips-scraper").call(run_input={
    "channels": [
        "ninja",
        "pokimane"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~twitch-clips-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"channels": ["ninja", "pokimane"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/twitch-clips-scraper` as a tool.

Full documentation, pricing and the latest changes: [Twitch Clips Scraper - Clips, View Counts, Creator Names](https://apify.com/om_kh/twitch-clips-scraper).

---
title: "Facebook Ad Creative Tracker - New, Edited, Dropped Ads"
description: "Compare two ad-creative snapshots and get back only what changed: new ads, edited copy, swapped landing pages, dropped ads. Bring your own ad records -- this does not fetch ads. Pricing: $0.02 per change, first 10 free. $2 per 1,000 ads."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Facebook Ad Creative Tracker - New, Edited, Dropped Ads

Compare two ad-creative snapshots and get back only what changed: new ads, edited copy, swapped landing pages, dropped ads. Bring your own ad records -- this does not fetch ads. Pricing: $0.02 per change, first 10 free. $2 per 1,000 ads.

**Run it on Apify:** [https://apify.com/om_kh/facebook-ad-creative-tracker](https://apify.com/om_kh/facebook-ad-creative-tracker) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Two snapshots of your own ad records (before and after) |
| **We do** | Compare them and keep only what changed |
| **You get** | One row per change: new ad, edited copy, swapped landing page or dropped ad, with the advertiser, headline, landing page and why it matters |
| **It costs** | $2 per 1,000 changed ads + $0.001 per run. The first 10 results of every run are free. No scraping, so no supplier fee |
| **It does not** | Fetch ads from Facebook: you bring the records (for that, use our Facebook Ads Library Scraper) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `previousAds` | array | Ads from the prior run; used to identify changes. |
| `currentAds` | array | Current authorized ad data to compare. Default: `[{"ad_id": "123", "advertiser": "Example Co", "headline": "5`. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Customer-authorized input", "authorization": "cus`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "ad_id": "123",
  "advertiser": "Example Co",
  "headline": "50% off today",
  "landing_url": "https://example.com/sale",
  "record_id": "123",
  "creative_fingerprint": "3684e372abdc2c956df96e4f75a823c482bb5b236be448fa742ae825312e485f",
  "change_type": "new",
  "runs_seen": 0,
  "long_running_creative": false,
  "why_it_matters": "Competitor launched a new ad — see what they're pushing."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/facebook-ad-creative-tracker").call(run_input={
    "currentAds": [
        {
            "ad_id": "123",
            "advertiser": "Example Co",
            "headline": "50% off today",
            "landing_url": "https://example.com/sale"
        }
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~facebook-ad-creative-tracker/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"currentAds": [{"ad_id": "123", "advertiser": "Example Co", "headline": "50% off today", "landing_url": "https://example.com/sale"}]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/facebook-ad-creative-tracker` as a tool.

Full documentation, pricing and the latest changes: [Facebook Ad Creative Tracker - New, Edited, Dropped Ads](https://apify.com/om_kh/facebook-ad-creative-tracker).

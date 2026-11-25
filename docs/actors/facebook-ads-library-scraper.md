---
title: "Facebook Ads Library Scraper API - Ad Copy, CTA, Impressions"
description: "Facebook Ads Library scraper API: scrape any advertiser's Facebook and Instagram ads from Meta's Ad Library: ad text, headline, call to action, landing page, format, platforms, impressions band, page likes and dates. Search by page name. No login. $12.50 per 1,000 ads, $1.95 from 16 Dec 2026."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Facebook Ads Library Scraper API - Ad Copy, CTA, Impressions

Facebook Ads Library scraper API: scrape any advertiser's Facebook and Instagram ads from Meta's Ad Library: ad text, headline, call to action, landing page, format, platforms, impressions band, page likes and dates. Search by page name. No login. $12.50 per 1,000 ads, $1.95 from 16 Dec 2026.

**Run it on Apify:** [https://apify.com/om_kh/facebook-ads-library-scraper](https://apify.com/om_kh/facebook-ads-library-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Facebook page names |
| **We do** | Read the advertiser's ads in Meta's public Ad Library |
| **You get** | One row per ad: text, headline, call to action, landing page, format, platforms (Facebook, Instagram...), impressions band, page likes and dates, plus every field the supplier returns (`source_data`) |
| **It costs** | $12.50 per 1,000 ads today, $1.95 per 1,000 from 16 December 2026 + $0.001 per run. Optional scheduled monitoring: +$0.45 per check today, $0.006 from 16 December 2026 (one-off runs never pay it). Apify also bills the supplier Actor `jmlp/meta-ad-library-scraper` that this robot runs for you, at its own price (about $0.15 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Facebook |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `pageNames` | array | Meta Page names (or Page URLs) whose public Ad Library entries you want monitored. |
| `currentAds` | array | Skip the chained Meta Ad Library fetch and pass ad data directly. |
| `previousAds` | array | Ads from the prior run; used to identify changes when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Meta Ad Library actor", "authorization": `. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "ad_id": "1077427058038979",
  "page_name": "Nike",
  "creative": "Meus looks favoritos são a combinação perfeita entre o esportivo e o casual 😮‍💨 @nikesportswear \nAs fotos são do melhor fotógrafo do mund...",
  "landing_url": "https://www.nike.com.br/busca?term=initiator",
  "is_active": true,
  "start_date": "2026-08-14T07:00:00Z",
  "ad_archive_id": "1077427058038979",
  "page_id": "15087023444",
  "has_user_reported": "(hidden here)",
  "page_is_deleted": false,
  "categories": [
    "UNKNOWN"
  ],
  "collation_count": 1,
  "collation_id": "1617744163243628",
  "contains_digital_created_media": false,
  "contains_sensitive_content": false,
  "end_date": 1792998000,
  "gated_type": "ELIGIBLE",
  "hide_data_status": "NONE",
  "is_aaa_eligible": false,
  "publisher_platform": [
    "FACEBOOK",
    "INSTAGRAM"
  ],
  "snapshot_branded_content_page_id": "15087023444",
  "snapshot_branded_content_page_is_deleted": false,
  "snapshot_branded_content_page_profile_uri": "https://www.facebook.com/nike/",
  "snapshot_branded_content_page_name": "Nike",
  "snapshot_page_id": "15087023444",
  "snapshot_page_is_deleted": false,
  "snapshot_page_profile_uri": "https://www.facebook.com/nike/",
  "snapshot_page_name": "Nike",
  "snapshot_page_profile_picture_url": "(hidden here)",
  "snapshot_body_text": "Meus looks favoritos são a combinação perfeita entre o esportivo e o casual 😮‍💨 @nikesportswear \nAs fotos são do melhor fotógrafo do mund...",
  "snapshot_is_reshared": false,
  "snapshot_caption": "nike.com.br",
  "snapshot_cards_count": 8,
  "snapshot_cards_title": [
    "initiator - Nike",
    "initiator - Nike"
  ],
  "snapshot_cta_text": "Shop now",
  "snapshot_cta_type": "SHOP_NOW",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/facebook-ads-library-scraper").call(run_input={
    "pageNames": [
        "Nike",
        "Allbirds"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~facebook-ads-library-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"pageNames": ["Nike", "Allbirds"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/facebook-ads-library-scraper` as a tool.

Full documentation, pricing and the latest changes: [Facebook Ads Library Scraper API - Ad Copy, CTA, Impressions](https://apify.com/om_kh/facebook-ads-library-scraper).

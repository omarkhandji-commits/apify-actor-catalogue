---
title: "Google Ads Transparency Scraper - Ad Text & Countries $1.40/1K"
description: "Google Ads Transparency scraper for any domain, advertiser name or ID: ad headline and description, format, first and last shown, days running, image or video, countries, and EU impressions and targeting. Filter by country, platform, format, dates. $1.40 per 1,000 ads, details included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Google Ads Transparency Scraper - Ad Text & Countries $1.40/1K

Google Ads Transparency scraper for any domain, advertiser name or ID: ad headline and description, format, first and last shown, days running, image or video, countries, and EU impressions and targeting. Filter by country, platform, format, dates. $1.40 per 1,000 ads, details included.

**Run it on Apify:** [https://apify.com/om_kh/google-ads-transparency-scraper](https://apify.com/om_kh/google-ads-transparency-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Domains, advertiser names or advertiser IDs, with optional country, platform, format and date filters |
| **We do** | Read Google's Ads Transparency Center |
| **You get** | One row per ad: headline, description, format, first and last shown dates, days running, image or video, every country it ran in, and for EU ads the impressions, platforms and targeting |
| **It costs** | $1.40 per 1,000 ads, no start fee, no monitoring fee. The first 10 ads of every run are free. Inputs that fail are never charged. No supplier fee |
| **It does not** | Solve CAPTCHAs, or give impressions and targeting outside the EU (Google does not publish them) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `queries` | array | One per line: a domain (nike.com), an advertiser name (Nike), an advertiser ID (AR16735076323512287233) or an Ads Transparency Center link. Default: `["nike.com", "Adidas"]`. |
| `domains` | array | Websites such as nike.com. |
| `advertiserIds` | array | Google advertiser IDs such as AR16735076323512287233. |
| `startUrls` | array | Advertiser, domain-search or ad links copied from adstransparency.google.com. |
| `resultType` | string | Ads (default), or only the advertisers that match each name. Default: `"ads"`. |
| `region` | string | Two-letter country where the ads were shown (US, GB, FR, DE...), or 'anywhere'. Default: `"US"`. |
| `platform` | string | Where the ads ran. Default: `"all"`. |
| `platforms` | array | Optional: ads shown on any of these platforms (an ad on several is delivered once). |
| `adFormat` | string | Text, image or video ads. Default: `"all"`. |
| `startDate` | string | Only ads shown on or after this date (YYYY-MM-DD). |
| `endDate` | string | Only ads shown on or before this date (YYYY-MM-DD). |
| `maxAdsPerQuery` | integer | 1 to 10,000. Default: `100`. |
| `resultsLimit` | integer | Alias of 'Max ads per query' for people coming from other ad scrapers. |
| `maxAdvertisersPerQuery` | integer | For a name, how many matching advertisers to read (1 to 20). Default: `3`. |
| `includeDetails` | boolean | For each ad: the headline, description and display URL of text ads, every variation, the YouTube video of video ads, and every country it ran in with its last day there. Default: `true`. |
| `skipDetails` | boolean | Turn on to skip the ad detail pages (faster). Default: `false`. |
| `onlyNewAds` | boolean | Return only ads this monitor has not returned before. Default: `false`. |
| `monitorId` | string | Optional name to keep separate 'only new ads' histories. |
| `maxTotalChargeUsd` | number | The run stops charging at this amount. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "ad",
  "advertiserId": "AR01437837420136497153",
  "advertiserName": "株式会社ナイキジャパン",
  "domain": "nike.com",
  "creativeId": "CR10784295660552192001",
  "format": "TEXT",
  "firstShown": "2024-12-09T04:00:07Z",
  "lastShown": "2026-10-23T22:29:29Z",
  "daysRunning": 684,
  "imageUrl": "https://tpc.googlesyndication.com/archive/simgad/9134810007502584797",
  "adUrl": "https://adstransparency.google.com/advertiser/AR01437837420136497153/creative/CR10784295660552192001?region=US",
  "region": "US",
  "searchQuery": "nike.com",
  "totalAdsMin": 8000,
  "totalAdsMax": 9000,
  "variations": [
    {
      "imageUrl": "https://tpc.googlesyndication.com/archive/simgad/9134810007502584797",
      "width": 348,
      "height": 504
    },
    {
      "imageUrl": "https://tpc.googlesyndication.com/archive/simgad/3490117570977004461",
      "width": 364,
      "height": 233
    }
  ],
  "variationCount": 3,
  "regionsShown": [
    {
      "region": "SG",
      "lastShown": "2026-10-19"
    },
    {
      "region": "JP",
      "lastShown": "2026-10-23"
    }
  ],
  "regionCount": 14,
  "impressionsMin": 0,
  "impressionsMax": 1000,
  "platformImpressions": [
    {
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-ads-transparency-scraper").call(run_input={
    "queries": [
        "nike.com",
        "Adidas"
    ],
    "maxAdsPerQuery": 50
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-ads-transparency-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"queries": ["nike.com", "Adidas"], "maxAdsPerQuery": 50}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-ads-transparency-scraper` as a tool.

Full documentation, pricing and the latest changes: [Google Ads Transparency Scraper - Ad Text & Countries $1.40/1K](https://apify.com/om_kh/google-ads-transparency-scraper).

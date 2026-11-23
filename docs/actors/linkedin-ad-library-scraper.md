---
title: "LinkedIn Ads Library Scraper - Impressions, Targeting"
description: "LinkedIn Ads Library scraper by keyword, advertiser, company page, pasted search link, country or date: full ad text, headline, CTA, landing page, images, video, run dates, impressions by country and targeting. No login. $2 per 1,000 ads, no start fee."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# LinkedIn Ads Library Scraper - Impressions, Targeting

LinkedIn Ads Library scraper by keyword, advertiser, company page, pasted search link, country or date: full ad text, headline, CTA, landing page, images, video, run dates, impressions by country and targeting. No login. $2 per 1,000 ads, no start fee.

**Run it on Apify:** [https://apify.com/om_kh/linkedin-ad-library-scraper](https://apify.com/om_kh/linkedin-ad-library-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A keyword (`crm`), an advertiser (`HubSpot`), ad links, or countries |
| **We do** | Search LinkedIn's public Ad Library, then open every ad's own page |
| **You get** | One row per ad: text, headline, call to action, landing page, images and video, run dates, estimated impressions with the split by country, and the targeting the advertiser chose |
| **It costs** | $1 per 1,000 ads, no start fee. The first 20 ads of every run are free, and an ad whose details could not be read is delivered free |
| **It does not** | Sign in to LinkedIn, or give spend and clicks (LinkedIn does not publish them). Run dates, impressions and targeting exist only for ads shown in the EU: add an EU country such as `FR` or `DE` |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchTerms` | array | Search the Ad Library by keyword (ad text or advertiser), one per line. Default: `["crm"]`. |
| `advertisers` | array | Company or person names that paid for the ads, e.g. HubSpot. Default: `["HubSpot"]`. |
| `exactAdvertiserMatch` | boolean | Keep only ads whose advertiser name equals what you typed (drops partners and resellers). Default: `false`. |
| `adUrls` | array | Specific ads: linkedin.com/ad-library/detail/... links or ad IDs. |
| `startUrls` | array | Paste any of: an Ad Library search link (run again with its filters), a company page such as https://www.linkedin.com/company/nvidia (all the ads of exactly that company), or a single ad link. |
| `countries` | array | Two-letter country codes where the ads were shown, e.g. US, FR, DE. |
| `dateRange` | string | When the ads ran. |
| `startDate` | string | Custom range start (YYYY-MM-DD). |
| `endDate` | string | Custom range end (YYYY-MM-DD). |
| `maxAdsPerSearch` | integer | 1 to 5,000. Default: `50`. |
| `includeDetails` | boolean | Full text, landing page, media, run dates, impressions by country and targeting (one extra page per ad, same price). Default: `true`. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "adId": "1585176223",
  "advertiser": "HubSpot",
  "format": "Single Image Ad",
  "creativeType": "SPONSORED_STATUS_UPDATE",
  "searchQuery": "HubSpot",
  "adUrl": "https://www.linkedin.com/ad-library/detail/1585176223",
  "advertiserUrl": "https://www.linkedin.com/company/68529",
  "advertiserLogo": "https://media.licdn.com/dms/image/v2/C4D0BAQF8H-SLmMDZlA/company-logo_100_100/company-logo_100_100/0/1646683330132/hubspot_logo?e=1794441...",
  "text": "Deine Systeme kosten Zeit und Nerven? Diese Live-Demo ist für Teams, die über einen Wechsel zu HubSpot nachdenken.",
  "headline": "Bereit für den Wechsel?",
  "callToAction": "Mehr erfahren",
  "landingUrl": "https://hubs.la/Q04B5zLF0?utm_campaign=EMEA&utm_source=linkedin&utm_medium=paid&utm_id=805100113&hsa_acc=517582366&hsa_cam=805100113&hsa_...",
  "imageUrls": [
    "https://media.licdn.com/dms/image/v2/D4D10AQF7IoszLHsyqg/image-shrink_1280/B4DaFZz24EHcAc-/0/1792508129137/1png?e=2147483647&v=beta&t=BLX..."
  ],
  "paidBy": "HubSpot, Inc.",
  "startDate": "2026-10-20",
  "endDate": "2026-10-23",
  "totalImpressions": "30k-50k",
  "impressionsMin": 30000,
  "impressionsMax": 50000,
  "impressionsByCountry": [
    {
      "country": "Germany",
      "percent": "100%"
    },
    {
      "country": "Spain",
      "percent": "less than 1%"
    }
  ],
  "targetingLanguages": [
    "Deutsch"
  ],
  "targetingLocations": [
    "Deutschland"
  ],
  "targetingParameters": {
    "Audience": {
      "targeted": false,
      "excluded": true
    },
    "Demographic": {
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/linkedin-ad-library-scraper").call(run_input={
    "searchTerms": [
        "crm"
    ],
    "advertisers": [
        "HubSpot"
    ],
    "maxAdsPerSearch": 24
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~linkedin-ad-library-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["crm"], "advertisers": ["HubSpot"], "maxAdsPerSearch": 24}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/linkedin-ad-library-scraper` as a tool.

Full documentation, pricing and the latest changes: [LinkedIn Ads Library Scraper - Impressions, Targeting](https://apify.com/om_kh/linkedin-ad-library-scraper).

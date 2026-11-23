---
title: "Google Trends Data Scraper - Interest, Regions, $2/1K"
description: "Google Trends data scraper that does not time out: 100% of runs succeeded in the last 30 days. Interest over time, % change, breakout queries, interest by country, region, city and metro, YouTube and News, Trending now. Up to 1,000 keywords per run. $2 per 1,000 keywords + $0.001 per run."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Google Trends Data Scraper - Interest, Regions, $2/1K

Google Trends data scraper that does not time out: 100% of runs succeeded in the last 30 days. Interest over time, % change, breakout queries, interest by country, region, city and metro, YouTube and News, Trending now. Up to 1,000 keywords per run. $2 per 1,000 keywords + $0.001 per run.

**Run it on Apify:** [https://apify.com/om_kh/google-trends-scraper](https://apify.com/om_kh/google-trends-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords (up to 5 compared), a country, dates and a source (Search, YouTube, News, Images, Shopping); or a country for Trending now |
| **We do** | Read Google Trends |
| **You get** | Interest over time, average, peak and change, rising and breakout queries, interest by country, region, city and metro; or every Trending now search with volume, growth and category |
| **It costs** | $2 per 1,000 keyword rows, $1 per 1,000 Trending now searches, + $0.001 per run. The first 3 results of every run are free; a keyword Google cannot return is never charged. No supplier fee |
| **It does not** | Give search volumes for keywords: Google Trends values are relative (0 to 100) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchTerms` | array | Keywords or topics to analyse on Google Trends, one per line (up to 1,000 per run). Default: `["chatgpt", "claude ai"]`. |
| `geo` | string | Two-letter country code (US, FR, GB, DE, IN...). |
| `timeRange` | string | Period to analyse. Default: `"past_12_months"`. |
| `customTimeRange` | string | Two dates, start then end: 2024-01-01 2024-12-31. |
| `searchProperty` | string | Which Google service the searches were made on. Default: `"web"`. |
| `compare` | boolean | Group keywords by 5 so their 0-100 values are directly comparable (like typing them together on Google Trends). Default: `false`. |
| `includeRelated` | boolean | Top and rising (breakout) related queries, plus related topics when Google has them. Default: `true`. |
| `includeRegions` | boolean | Where the keyword is most searched: countries when the search is worldwide, regions when it is one country. Default: `true`. |
| `regionLevels` | array | Extra breakdowns in the same row: interestByCountry, interestBySubregion, interestByCity, interestByMetro. |
| `maxRegions` | integer | How many places to keep per level, most interested first. 0 = all of them. Default: `15`. |
| `includeLowSearchVolumeRegions` | boolean | Also list places Google hides by default because few people search there. Default: `false`. |
| `category` | integer | Optional Google Trends category ID (0 = all categories). Default: `0`. |
| `startUrls` | array | Paste trends.google.com/trends/explore links: terms, country, dates, category and service are read from each link. |
| `spreadsheetId` | string | Link or ID of a Google Sheet shared as 'Anyone with the link'. |
| `language` | string | Language of topic names, place names and date labels: en-US, fr, es, de, pt-BR, ja... Default: `"en-US"`. |
| `viewedFrom` | string | Two-letter country the request leaves from (us, gb, fr...). |
| `trendingNowCountries` | array | Optional: two-letter country codes to also get the trending searches of each (search volume, growth, start time, categories, related queries, news). |
| `trendingNowTimeframe` | string | How far back to list trending searches. Default: `"24"`. |
| `trendingNowMaxItems` | integer | Biggest trends first. Default: `25`. |
| `trendingNowCategories` | array | Keep only trends of these categories. |
| `maxTotalChargeUsd` | number | Optional hard cap on what this run can cost you. |
| `isMultiple` | boolean | When on, an entry like `tea, coffee` is read as two search terms. Default: `false`. |
| `maxItems` | integer | Most records returned by the run. 0 = no limit. Default: `0`. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "keyword",
  "keyword": "chatgpt",
  "geo": "worldwide",
  "timeRange": "today 12-m",
  "category": 0,
  "searchProperty": "web",
  "averageInterest": 82.1,
  "peakInterest": 100,
  "peakDate": "2025-11-16T00:00:00Z",
  "latestInterest": 95,
  "trendDirection": "stable",
  "changePct": -7.2,
  "timeline": [
    {
      "date": "2025-10-19T00:00:00Z",
      "label": "Oct 19 – 25, 2025",
      "value": 94,
      "partial": false
    },
    {
      "date": "2025-10-26T00:00:00Z",
      "label": "Oct 26 – Nov 1, 2025",
      "value": 93,
      "partial": false
    }
  ],
  "topRegions": [
    {
      "region": "Rwanda",
      "code": "RW",
      "value": 100
    },
    {
      "region": "Sri Lanka",
      "code": "LK",
      "value": 77
    }
  ],
  "relatedQueriesTop": [
    {
      "query": "ai chatgpt",
      "value": 100,
      "formattedValue": "100",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-trends-scraper").call(run_input={
    "searchTerms": [
        "chatgpt",
        "claude ai"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-trends-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["chatgpt", "claude ai"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-trends-scraper` as a tool.

Full documentation, pricing and the latest changes: [Google Trends Data Scraper - Interest, Regions, $2/1K](https://apify.com/om_kh/google-trends-scraper).

---
title: "Google News Scraper - Headlines, Source, Date, API"
description: "Google News API: articles for any keyword, topic section, city or Google News link, in any country and language. Up to 5,000 per search, custom dates, the publisher's own link, picture and summary. No API key. $2 per 1,000 articles ($3 from Nov 12)."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Google News Scraper - Headlines, Source, Date, API

Google News API: articles for any keyword, topic section, city or Google News link, in any country and language. Up to 5,000 per search, custom dates, the publisher's own link, picture and summary. No API key. $2 per 1,000 articles ($3 from Nov 12).

**Run it on Apify:** [https://apify.com/om_kh/google-news-scraper](https://apify.com/om_kh/google-news-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Searches (a brand, a company, a person, a topic), Google News sections, or cities for local news |
| **We do** | Read Google News' own feeds and, on request, the publisher's page |
| **You get** | One row per article: headline, publisher, publication date and link; option: the publisher's own link, picture, summary and author |
| **It costs** | **$3 per 1,000 articles**, no start fee. A search with no result costs nothing; the first result of every run is free |
| **It does not** | Give the full article text. Above 100 articles a search is cut into date windows (one day at the smallest) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `queries` | array | Keywords, brands, companies or people to search on Google News, one per line. Default: `["openai", "electric vehicles"]`. |
| `topics` | array | Google News sections of the chosen country edition: the headlines Google shows there right now. |
| `locations` | array | Cities or regions: Montreal, Texas, Lyon. |
| `topicUrls` | array | Any news.google.com topic, section, publication or search link: its articles are returned. |
| `country` | string | Two-letter country code of the Google News edition, e.g. US, GB, FR, DE, IN, BR, CA. Default: `"US"`. |
| `language` | string | Two-letter language code of the edition, e.g. en, fr, de, es, pt. Default: `"en"`. |
| `timeRange` | string | Only articles from the last hour/day/week/month/year (Google's own 'when:' filter). |
| `dateFrom` | string | YYYY-MM-DD. |
| `dateTo` | string | YYYY-MM-DD, included. |
| `maxArticlesPerQuery` | integer | Google News gives 100 articles per search. Default: `100`. |
| `sourceDomains` | array | Domains to keep: reuters.com, bbc.com, lemonde.fr. |
| `excludeDomains` | array | Domains to leave out. |
| `decodeUrls` | boolean | Google News links point to news.google.com. Default: `false`. |
| `includeArticleDetails` | boolean | Open each article's page for its picture, summary, author and site name. Default: `false`. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Google News official RSS feed (first-party, no th`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "CBMiogFBVV95cUxQRXdjM1lJeFg0SF9wQ1FfYVpqMzZfY2R4aVhqaHVRT252Q2lZMm5QVTc3TDlkR3pCWG8yR3FPOTQxak1SUk4zVkhYaUhXdk9TbVhwcXhKSXU2SUw1OEZRNGpxS...",
  "query_id": "openai",
  "title": "An OpenAI Model Spent Ethereum Without Permission. Here's What That Means For Crypto Investors. - Yahoo Finance",
  "url": "https://news.google.com/rss/articles/CBMiogFBVV95cUxQRXdjM1lJeFg0SF9wQ1FfYVpqMzZfY2R4aVhqaHVRT252Q2lZMm5QVTc3TDlkR3pCWG8yR3FPOTQxak1SUk4z...",
  "text": "An OpenAI Model Spent Ethereum Without Permission. Here's What That Means For Crypto Investors. Yahoo Finance",
  "author": "(hidden here)",
  "published_at": "2026-10-24T21:26:00+00:00",
  "headline": "An OpenAI Model Spent Ethereum Without Permission. Here's What That Means For Crypto Investors.",
  "sourceUrl": "https://finance.yahoo.com",
  "sourceDomain": "finance.yahoo.com",
  "publishedTimestamp": 1792877160,
  "resultRank": 1,
  "queryType": "search",
  "country": "US",
  "language": "en"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-news-scraper").call(run_input={
    "queries": [
        "openai",
        "electric vehicles"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-news-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"queries": ["openai", "electric vehicles"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-news-scraper` as a tool.

Full documentation, pricing and the latest changes: [Google News Scraper - Headlines, Source, Date, API](https://apify.com/om_kh/google-news-scraper).

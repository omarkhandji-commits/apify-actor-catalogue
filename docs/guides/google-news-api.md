---
title: "Google News API — Headlines by Keyword, Country and Date, JSON"
description: "Get Google News articles for any keyword as JSON: headline, publisher, date, snippet and link, for any country edition and time range. No API key."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Google News API — Headlines by Keyword, Country and Date, JSON

## How do I get Google News results as JSON by API?

Use the **Google News API** Actor with your keywords, a country and a language. It reads Google News' official public RSS feeds and returns one row per article: headline, publisher, publication date (ISO UTC), snippet and link. Limit results to recent articles with `timeRange`. No API key.

**Try it:** [Google News API on Apify](https://apify.com/om_kh/google-news-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [Google News API](https://apify.com/om_kh/google-news-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "queries": [
    "openai",
    "electric vehicles"
  ],
  "country": "US",
  "language": "en"
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-news-scraper").call(run_input={
    "queries": [
        "openai",
        "electric vehicles"
    ],
    "country": "US",
    "language": "en"
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-news-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"queries": ["openai", "electric vehicles"], "country": "US", "language": "en"}'
```

## What you get

- `title`
- `url`
- `author` (publisher)
- `text` (snippet)
- `published_at`
- `query_id`

## Price

Pay per article — see the Pricing tab for the current price. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- Brand and competitor news monitoring
- News feeds for newsletters and dashboards
- Context for AI agents answering current-events questions

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-news-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Which countries are supported?**  
Any Google News edition: set `country` and `language`, e.g. FR + fr.

**Can I get only new articles on a schedule?**  
Yes, turn on monitoring; later runs return only new articles.

## Related

- [Google Trends Scraper - Interest, Regions, Rising Queries](https://apify.com/om_kh/google-trends-scraper)
- [Hacker News Scraper - Posts, Points, Comment Count](https://apify.com/om_kh/hacker-news-scraper)
- [Reddit Posts & Comments Scraper - Upvotes, Text, Date](https://apify.com/om_kh/reddit-posts-comments-scraper)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I get Google News results as JSON by API?", "acceptedAnswer": {"@type": "Answer", "text": "Use the Google News API Actor with your keywords, a country and a language. It reads Google News' official public RSS feeds and returns one row per article: headline, publisher, publication date (ISO UTC), snippet and link. Limit results to recent articles with `timeRange`. No API key."}}, {"@type": "Question", "name": "Which countries are supported?", "acceptedAnswer": {"@type": "Answer", "text": "Any Google News edition: set `country` and `language`, e.g. FR + fr."}}, {"@type": "Question", "name": "Can I get only new articles on a schedule?", "acceptedAnswer": {"@type": "Answer", "text": "Yes, turn on monitoring; later runs return only new articles."}}]}
</script>

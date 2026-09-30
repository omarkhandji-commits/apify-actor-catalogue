---
title: "Google Trends API — Interest Over Time, Rising Queries, JSON"
description: "Unofficial Google Trends API: interest over time, average, peak, % change, top regions, rising and breakout queries, and daily trending searches, as JSON or CSV."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Google Trends API — Interest Over Time, Rising Queries, JSON

## Is there a Google Trends API?

Google has no public, self-serve Google Trends API for most developers. The **Google Trends Scraper** Actor gives you the same data as JSON: for each keyword, the 0–100 interest timeline, average, peak, latest value, trend direction and % change, the top 15 regions, top and rising related queries (including **Breakout**), plus today's **Trending now** searches for any country. $0.002 per keyword, first 3 results of every run free.

**Try it:** [Google Trends Scraper on Apify](https://apify.com/om_kh/google-trends-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [Google Trends Scraper](https://apify.com/om_kh/google-trends-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "searchTerms": [
    "chatgpt",
    "claude ai",
    "gemini"
  ],
  "geo": "US",
  "timeRange": "past_12_months",
  "compare": true,
  "trendingNowCountries": [
    "US"
  ]
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-trends-scraper").call(run_input={
    "searchTerms": [
        "chatgpt",
        "claude ai",
        "gemini"
    ],
    "geo": "US",
    "timeRange": "past_12_months",
    "compare": True,
    "trendingNowCountries": [
        "US"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-trends-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["chatgpt", "claude ai", "gemini"], "geo": "US", "timeRange": "past_12_months", "compare": true, "trendingNowCountries": ["US"]}'
```

## What you get

- `keyword`
- `averageInterest`
- `peakInterest`
- `peakDate`
- `latestInterest`
- `trendDirection` (rising / falling / stable)
- `changePct`
- `timeline`
- `topRegions`
- `relatedQueriesRising`
- `relatedQueriesTop`
- `trendsUrl`

## Price

$0.002 per keyword, $0.001 per trending search, no start fee. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- SEO and content calendars — find rising queries early
- Product and market research across countries
- Daily trend alerts with the news behind each trend
- Let an AI agent check whether a topic is growing

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-trends-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Are the values search volumes?**  
No. Google Trends values are relative (0–100 for the period and place), exactly like the website.

**Can I compare keywords on one scale?**  
Yes, set `compare: true`; keywords are grouped by 5 like on trends.google.com.

**Does it need a Google account?**  
No.

## Related

- [Google News API - Headlines, Source, Date, No Login](https://apify.com/om_kh/google-news-scraper)
- [YouTube Search Scraper API - Videos, Views, $0.50/1K](https://apify.com/om_kh/vigia-youtube-search-monitor)
- [Google Search Results Scraper - Rankings, SERP, Position](https://apify.com/om_kh/google-search-results-scraper)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "Is there a Google Trends API?", "acceptedAnswer": {"@type": "Answer", "text": "Google has no public, self-serve Google Trends API for most developers. The Google Trends Scraper Actor gives you the same data as JSON: for each keyword, the 0–100 interest timeline, average, peak, latest value, trend direction and % change, the top 15 regions, top and rising related queries (including Breakout), plus today's Trending now searches for any country. $0.002 per keyword, first 3 results of every run free."}}, {"@type": "Question", "name": "Are the values search volumes?", "acceptedAnswer": {"@type": "Answer", "text": "No. Google Trends values are relative (0–100 for the period and place), exactly like the website."}}, {"@type": "Question", "name": "Can I compare keywords on one scale?", "acceptedAnswer": {"@type": "Answer", "text": "Yes, set `compare: true`; keywords are grouped by 5 like on trends.google.com."}}, {"@type": "Question", "name": "Does it need a Google account?", "acceptedAnswer": {"@type": "Answer", "text": "No."}}]}
</script>

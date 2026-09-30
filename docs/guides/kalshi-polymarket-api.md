---
title: "Kalshi and Polymarket API — Prediction Market Odds as JSON"
description: "Live Kalshi and Polymarket odds in one table: implied probability, bid/ask, 24h move, volume and liquidity for any topic."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Kalshi and Polymarket API — Prediction Market Odds as JSON

## How do I get Kalshi and Polymarket odds by API?

Use the **Kalshi & Polymarket Scraper**. Type a topic (for example `fed rate`, `election`, `bitcoin`) and it searches both exchanges through their official public APIs, returning one row per market with the same fields on both venues: implied probability, yes price, bid, ask, spread, 24h move, volume, liquidity, open interest (Kalshi), close time and rules. Leave the topic empty for the most-traded markets. $1 per 1,000 markets.

**Try it:** [Kalshi & Polymarket Scraper on Apify](https://apify.com/om_kh/kalshi-polymarket-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [Kalshi & Polymarket Scraper](https://apify.com/om_kh/kalshi-polymarket-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "searchTerms": [
    "fed rate",
    "election"
  ],
  "platforms": [
    "kalshi",
    "polymarket"
  ],
  "minVolume": 10000
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/kalshi-polymarket-scraper").call(run_input={
    "searchTerms": [
        "fed rate",
        "election"
    ],
    "platforms": [
        "kalshi",
        "polymarket"
    ],
    "minVolume": 10000
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~kalshi-polymarket-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["fed rate", "election"], "platforms": ["kalshi", "polymarket"], "minVolume": 10000}'
```

## What you get

- `platform` (kalshi / polymarket)
- `question`
- `outcome`
- `impliedProbabilityPct`
- `yesPrice`
- `bestBid`
- `bestAsk`
- `change24h`
- `volume`
- `volume24h`
- `liquidity`
- `openInterest`
- `closeTime`
- `url`

## Price

$0.001 per market row, no start fee. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- Compare Kalshi vs Polymarket on the same event
- Probability dashboards and alerts
- Research and journalism
- AI agents that check market odds

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/kalshi-polymarket-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Do I need an exchange account?**  
No, both publish market data publicly.

**Is it trading advice?**  
No. It only reads market data and places no trades.

## Related

- [Google Trends Scraper - Interest, Regions, Rising Queries](https://apify.com/om_kh/google-trends-scraper)
- [Google News API - Headlines, Source, Date, No Login](https://apify.com/om_kh/google-news-scraper)
- [X (Twitter) Search Scraper - Posts, Likes, Replies](https://apify.com/om_kh/twitter-x-search-scraper)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I get Kalshi and Polymarket odds by API?", "acceptedAnswer": {"@type": "Answer", "text": "Use the Kalshi & Polymarket Scraper. Type a topic (for example `fed rate`, `election`, `bitcoin`) and it searches both exchanges through their official public APIs, returning one row per market with the same fields on both venues: implied probability, yes price, bid, ask, spread, 24h move, volume, liquidity, open interest (Kalshi), close time and rules. Leave the topic empty for the most-traded markets. $1 per 1,000 markets."}}, {"@type": "Question", "name": "Do I need an exchange account?", "acceptedAnswer": {"@type": "Answer", "text": "No, both publish market data publicly."}}, {"@type": "Question", "name": "Is it trading advice?", "acceptedAnswer": {"@type": "Answer", "text": "No. It only reads market data and places no trades."}}]}
</script>

---
title: "Kalshi & Polymarket Scraper - Odds, Probability, Volume"
description: "Prediction-market data from Kalshi and Polymarket in one table: implied probability, yes price, bid/ask, spread, 24h move, volume, liquidity, open interest, close time, rules, optional live order book. Open or resolved markets, any topic. Optional AI reading. $1 per 1,000 markets."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Kalshi & Polymarket Scraper - Odds, Probability, Volume

Prediction-market data from Kalshi and Polymarket in one table: implied probability, yes price, bid/ask, spread, 24h move, volume, liquidity, open interest, close time, rules, optional live order book. Open or resolved markets, any topic. Optional AI reading. $1 per 1,000 markets.

**Run it on Apify:** [https://apify.com/om_kh/kalshi-polymarket-scraper](https://apify.com/om_kh/kalshi-polymarket-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Topics (elections, the Fed, crypto, sports...) or nothing, for the biggest markets |
| **We do** | Read Kalshi and Polymarket |
| **You get** | One row per market: implied probability, yes price, bid / ask, spread, 24-hour move, volume, liquidity, open interest, close time, resolution rules, No price, resolved outcome, resolution source, event and token IDs, bid / ask size, optional live order book |
| **It costs** | $1 per 1,000 markets + $0.001 per run. A daily snapshot of 200 markets for a month = **$6**. The first 20 rows of every run are free. No supplier fee |
| **It does not** | Place trades or give financial advice |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchTerms` | array | Topics to search on both exchanges, one per line (up to 20), e.g. 'fed rate', 'bitcoin', 'election'. Default: `["fed rate", "bitcoin"]`. |
| `platforms` | array | Kalshi, Polymarket or both (default). Default: `["kalshi", "polymarket"]`. |
| `status` | string | Open markets (default), resolved ones for back-testing, or both. Default: `"active"`. |
| `maxMarkets` | integer | 1 to 1,000. Default: `100`. |
| `category` | string | Optional, e.g. Economics, Politics, Elections, Crypto, Sports (Kalshi category / Polymarket tag). |
| `minVolume` | number | Optional: skip markets with less total traded volume (Kalshi contracts / Polymarket USD). Default: `1000`. |
| `sortBy` | string | 24h volume (default), total volume, liquidity or closing soonest. Default: `"volume24h"`. |
| `includeOrderbook` | boolean | Add an orderbook object to each market (YES side): the best bids and asks with their size, read live from Kalshi and the Polymarket CLOB. Default: `false`. |
| `orderbookDepth` | integer | How many price levels per side (1 to 50). Default: `10`. |
| `analyzeWithAi` | boolean | Add an ai object to each market: what it asks, what settles it, key factors and ambiguities in its rules. Default: `false`. |
| `anthropicApiKey` | string | Needed only for the AI analysis. |
| `aiModel` | string | Claude model ID, e.g. claude-opus-5-5 (default), claude-sonnet-5-5 or claude-haiku-4-5 for a lower cost. Default: `"claude-opus-5-5"`. |
| `maxAiRows` | integer | The AI reads at most this many results per run (1 to 500), to keep your model bill predictable. Default: `100`. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "platform": "polymarket",
  "marketId": "0x12aa13b3da17ceae1b0a59b5d5b77121e91bb79b4bb0b52bf6543ed3f8d0953b",
  "question": "Will the Fed increase interest rates by 25 bps after the October 2026 meeting?",
  "eventTitle": "Fed Decision in October?",
  "outcome": "Yes",
  "yesPrice": 0.065,
  "impliedProbabilityPct": 6.5,
  "bestBid": 0.06,
  "bestAsk": 0.07,
  "spread": 0.01,
  "lastPrice": 0.07,
  "change24h": 0.01,
  "volume": 13904629.528330002,
  "volume24h": 1236896.6302630003,
  "liquidity": 616736.2329,
  "outcomes": [
    {
      "name": "(hidden here)",
      "price": 0.065
    },
    {
      "name": "(hidden here)",
      "price": 0.935
    }
  ],
  "category": "Fed, fomc, Trump",
  "closeTime": "2026-10-29T03:59:00Z",
  "marketStatus": "active",
  "rules": "The FED interest rates are defined in this market by the upper bound of the target federal funds range. The decisions on the target feder...",
  "url": "https://polymarket.com/event/fed-decision-in-october-20260617190323537",
  "searchQuery": "fed rate"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/kalshi-polymarket-scraper").call(run_input={
    "searchTerms": [
        "fed rate",
        "bitcoin"
    ],
    "maxMarkets": 20,
    "minVolume": 1000
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~kalshi-polymarket-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["fed rate", "bitcoin"], "maxMarkets": 20, "minVolume": 1000}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/kalshi-polymarket-scraper` as a tool.

Full documentation, pricing and the latest changes: [Kalshi & Polymarket Scraper - Odds, Probability, Volume](https://apify.com/om_kh/kalshi-polymarket-scraper).

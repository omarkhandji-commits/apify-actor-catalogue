---
title: "Redfin API: Every Home for Sale in a City, with Area-Median Comparison (2026)"
description: "How to get every Redfin home for sale in a city, county or neighborhood as JSON or CSV, with price per sq ft compared with the area median. Dated run: 632 homes in 43 seconds."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# How do I get Redfin listings for a whole city as data?

*Written by the maker of the Actor (om_kh). Figures come from a dated run on Apify and anyone can repeat it.*

## Short answer

Redfin has no public listings API. Use the **[Redfin Scraper (om_kh)](https://apify.com/om_kh/redfin-scraper)**: paste a Redfin city, county or neighborhood link and get every home for sale with price, beds, baths, sq ft, price per sq ft, HOA, days on market, open houses, features, broker, GPS and photos. Each home also carries the **area's median price and price per sq ft, and how far above or below it sits**, so possible deals stand out. **$0.40 per 1,000 homes**, no login.

## Dated run on Apify

2026-10-23: Zilker (Austin neighborhood), Austin TX and New York NY, 300 homes max per link, at least 2 bedrooms.

| | Result |
|---|---|
| Homes | 632 (Zilker 34, Austin 298, New York 300) |
| Below the area median price per sq ft | 309 |
| With photos | 557 |
| Time | 43 seconds |
| Platform cost | $0.0006 |

A whole city also works: Austin, TX returned 5,796 homes for sale in one search.

## What you can and cannot get

- **Yes:** homes for sale (active and coming soon) in any Redfin city, county or neighborhood link, with filters for price, beds, baths, size, HOA, days on market, home type, ZIP codes and keywords in the description.
- **Not included:** sold homes, rentals, the Redfin Estimate and price history. Those sit on each home's page, which Redfin protects; the Actor does not try to get around that protection.
- **ZIP-code links** are not accepted yet: search the city and use the ZIP filter.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/redfin-scraper").call(run_input={
    "searchUrls": ["https://www.redfin.com/city/30818/TX/Austin"],
    "maxHomesPerSearch": 2000,
    "maxPrice": 450000,
    "minBeds": 3,
    "belowMedianOnly": True,
})
for home in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(home["address"], home["price"], home["pricePerSqFtVsAreaMedianPct"], home["url"])
```

## Common uses

Deal lists for investors, fresh-listing alerts for agents, open-house planning, city-wide price and size studies, and maps or valuation models for proptech apps and AI agents through MCP.

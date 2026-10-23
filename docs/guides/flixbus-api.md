---
title: "FlixBus API: Bus and Train Prices, Seats and Schedules as Data (2026)"
description: "How to get FlixBus and FlixTrain prices, seats left and schedules for any route and date as JSON or CSV, with a 90-day price calendar. Dated run: 773 trips in 35 seconds."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# How do I get FlixBus prices and schedules for a route as data?

*Written by the maker of the Actor (om_kh). Figures come from a dated run on Apify and anyone can repeat it.*

## Short answer

Use the **[FlixBus Scraper (om_kh)](https://apify.com/om_kh/flixbus-scraper)**: write routes in plain words (`Paris, FR -> Amsterdam`), pick a first date and up to 90 days, and get every FlixBus and FlixTrain ride with price, seats left, times, duration, stations, transfers and amenities, with the cheapest ride of each day flagged. **$1 per 1,000 trips**, no key. It was the first FlixBus Actor in the Apify Store on 2026-10-22.

## Dated run on Apify

2026-10-22: Paris -> Amsterdam, Berlin -> Munich and New York -> Boston, 7 days from 2026-11-20.

| | Result |
|---|---|
| Trips | 773 (Paris -> Amsterdam 193, Berlin -> Munich 113, New York -> Boston 467) |
| Cheapest ride | 16.99 EUR (Berlin -> Munich) |
| Time | 35 seconds |
| Platform cost | $0.0018 |
| Errors | 0 |

## What you can and cannot get

- **Yes:** every ride FlixBus sells between two cities on each date, in Europe and North America, with live price and seats for 1 to 9 adults in 14 currencies.
- **No booking:** each row has a link to the FlixBus search for that day.
- **Prices move:** they are the prices shown at the time of the run; schedule the Actor to follow them.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/flixbus-scraper").call(run_input={
    "routes": ["Paris, FR -> Amsterdam"],
    "startDate": "2026-11-20",
    "numberOfDays": 30,
    "directOnly": True,
})
for row in client.dataset(run["defaultDatasetId"]).iterate_items():
    if row.get("cheapestOfTheDay"):
        print(row["date"], row["price"], row["departure"])
```

## Common uses

Price calendars and alerts, travel apps and comparison sites, intercity bus market research, and AI travel agents through MCP.

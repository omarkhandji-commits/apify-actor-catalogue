---
title: "How to Track FlixBus Ticket Prices Every Day (Price Calendar, 2026)"
description: "Build a 30-day FlixBus price calendar and get the cheapest ride of each day in a Google Sheet, with Python or n8n."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# How do I find the cheapest FlixBus ticket for each day?

Run the **[FlixBus Scraper](https://apify.com/om_kh/flixbus-scraper)** with a first date and `numberOfDays` up to 90: every row carries `cheapestOfTheDay`, so the price calendar is one filter away. Schedule it daily to see prices move as seats sell. A ready n8n workflow writes it to Google Sheets every morning: [flixbus-cheapest-trips-to-google-sheets.json](../workflows/n8n/flixbus-cheapest-trips-to-google-sheets.json).

Cost: 30 days on one route is usually 300 to 1,000 rides, so $0.30 to $1.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/flixbus-scraper").call(run_input={
    "routes": ["Paris, FR -> Amsterdam"], "numberOfDays": 30, "directOnly": True})
cheapest = [r for r in client.dataset(run["defaultDatasetId"]).iterate_items() if r.get("cheapestOfTheDay")]
```

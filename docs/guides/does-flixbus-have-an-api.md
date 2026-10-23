---
title: "Does FlixBus Have a Public API? (2026 Answer and a Working Alternative)"
description: "FlixBus has no public developer API for prices. How to get FlixBus prices, seats and schedules as JSON anyway, with a dated test."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Does FlixBus have a public API?

**No public developer API** for searching rides and prices: FlixBus's partner API is for travel agencies under contract. The FlixBus website itself reads its prices from a search service, and the **[FlixBus Scraper (om_kh)](https://apify.com/om_kh/flixbus-scraper)** reads that same public search: any route, any date, price, seats left, times, stations, transfers and amenities as JSON, CSV or Excel, **$1 per 1,000 trips**.

Dated test on 2026-10-22: Paris -> Amsterdam, Berlin -> Munich and New York -> Boston over 7 days returned **773 rides in 35 seconds**; the cheapest was 16.99 EUR.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/flixbus-scraper").call(run_input={"routes": ["Berlin -> Munich"], "numberOfDays": 7})
```

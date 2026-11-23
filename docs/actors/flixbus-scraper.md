---
title: "FlixBus Scraper - Bus & Train Prices, Seats $1/1K"
description: "Scrape FlixBus and FlixTrain rides for any city pairs and dates: price, seats left, departure and arrival time, duration, stations, transfers, operator, amenities and booking link. Date ranges, direct-only and max-price filters. No login. $1 per 1,000 trips."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# FlixBus Scraper - Bus & Train Prices, Seats $1/1K

Scrape FlixBus and FlixTrain rides for any city pairs and dates: price, seats left, departure and arrival time, duration, stations, transfers, operator, amenities and booking link. Date ranges, direct-only and max-price filters. No login. $1 per 1,000 trips.

**Run it on Apify:** [https://apify.com/om_kh/flixbus-scraper](https://apify.com/om_kh/flixbus-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | City pairs (`Berlin -> Munich`) or FlixBus search links, and a date, a range of up to 90 days or flexible dates |
| **We do** | Read FlixBus and FlixTrain rides |
| **You get** | One row per trip: price with and without the booking fee, seats left, departure and arrival time and station, duration, transfers, operator, amenities and a booking link |
| **It costs** | $1 per 1,000 trips + $0.001 per run. Searches that fail are never charged. No supplier fee |
| **It does not** | Book tickets |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `routes` | array | One route per line: 'From -> To'. Default: `["Paris, FR -> Amsterdam", "Berlin -> Munich"]`. |
| `searchUrls` | array | Search links copied from shop.flixbus.com (after you search on the site). |
| `returnTrips` | boolean | Adds To -> From for every route. (Ignored when a return date is set.). Default: `false`. |
| `returnDate` | string | YYYY-MM-DD. |
| `startDate` | string | Default: tomorrow. |
| `numberOfDays` | integer | Search every day from the first date, up to 90 days. Default: `1`. |
| `dates` | array | Exact dates (YYYY-MM-DD). |
| `flexibleDays` | integer | Also searches this many days before and after each date (and the return date), to find the cheapest day. 0 = exact dates. Default: `0`. |
| `adults` | integer | Prices are for this many adults. Default: `1`. |
| `children0to5` | integer | Children aged 0 to 5. Default: `0`. |
| `children6to14` | integer | Children aged 6 to 14. Default: `0`. |
| `bikes` | integer | Bike slots. Default: `0`. |
| `currency` | string | Currency of the prices. Default: `"EUR"`. |
| `locale` | string | Language of city and station names. Default: `"en"`. |
| `directOnly` | boolean | Leave out rides with a transfer. Default: `false`. |
| `maxPrice` | number | Leave out rides above this price (in the chosen currency). |
| `availableOnly` | boolean | Leave out sold-out rides. Default: `false`. |
| `maxTotalChargeUsd` | number | The run stops before it would cost more than this. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "trip",
  "tripId": "direct:c6aa9ead-dfc2-4e18-bc30-f67933914fbe:dcc5426b-9603-11e6-9066-549f350fcb0c:dcc5b353-9603-11e6-9066-549f350fcb0c",
  "rideStatus": "available",
  "fromCity": "Paris",
  "toCity": "Amsterdam",
  "fromStation": "Paris (Bercy Seine)",
  "toStation": "Schiphol Airport",
  "departure": "2026-10-24T09:05:00+02:00",
  "arrival": "2026-10-24T16:50:00+02:00",
  "durationMinutes": 465,
  "price": 44.99,
  "priceWithFee": 45.98,
  "originalPrice": 44.99,
  "currency": "EUR",
  "adults": 1,
  "seatsAvailable": 9,
  "seatsLeftAtPrice": 1,
  "capacity": "low",
  "transfers": 0,
  "transferType": "Direct",
  "meansOfTransport": [
    "bus"
  ],
  "operators": [
    "FlixBus B.V."
  ],
  "amenities": [
    "POWER_SOCKETS",
    "WIFI"
  ],
  "provider": "flixbus",
  "date": "2026-10-24",
  "bookingUrl": "https://shop.flixbus.com/search?departureCity=40de8964-8646-11e6-9066-549f350fcb0c&arrivalCity=40dde3b8-8646-11e6-9066-549f350fcb0c&rideD...",
  "route": "Paris, FR -> Amsterdam",
  "cheapestOfTheDay": true
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/flixbus-scraper").call(run_input={
    "routes": [
        "Paris, FR -> Amsterdam",
        "Berlin -> Munich"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~flixbus-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"routes": ["Paris, FR -> Amsterdam", "Berlin -> Munich"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/flixbus-scraper` as a tool.

Full documentation, pricing and the latest changes: [FlixBus Scraper - Bus & Train Prices, Seats $1/1K](https://apify.com/om_kh/flixbus-scraper).

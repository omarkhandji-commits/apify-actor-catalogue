---
title: "Google Hotels Search Scraper - Prices, OTA Rates, Ratings"
description: "Google Hotels search scraper that does not fail: 100% of runs succeeded in the last 30 days. Any city and dates: nightly and total price, about 20 booking-site offers per hotel, stars, rating, review themes, amenities, nearby places, photos. Google's own sort and filters. From $2 per 1,000."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Google Hotels Search Scraper - Prices, OTA Rates, Ratings

Google Hotels search scraper that does not fail: 100% of runs succeeded in the last 30 days. Any city and dates: nightly and total price, about 20 booking-site offers per hotel, stars, rating, review themes, amenities, nearby places, photos. Google's own sort and filters. From $2 per 1,000.

**Run it on Apify:** [https://apify.com/om_kh/google-hotels-scraper](https://apify.com/om_kh/google-hotels-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Cities and dates, with Google's own sort and filters |
| **We do** | Read Google Hotels |
| **You get** | One row per property: nightly and total price, star class, guest rating, review count and themes, amenities, eco flag, GPS, photos, nearby places; option: prices from every booking site with links, room rates and free-cancellation dates |
| **It costs** | $2 per 1,000 properties, $4 per 1,000 with every booking site's prices, + $0.001 per run from Dec 4, 2026 (no start fee before). The first 20 properties of every run are free. No supplier fee |
| **It does not** | Book rooms, or return more than a few hundred properties per search (split big cities by neighborhood) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `locations` | array | Cities, neighborhoods or full searches: Lisbon, Paris 11e, Miami Beach, 'boutique hotels near the Eiffel Tower' (up to 50). Default: `["Lisbon"]`. |
| `checkInDate` | string | YYYY-MM-DD. |
| `checkOutDate` | string | YYYY-MM-DD. |
| `adults` | integer | Guests per room. Default: `2`. |
| `children` | integer | Children per room. Default: `0`. |
| `currency` | string | Three-letter code: USD, EUR, GBP, CAD, AUD, JPY, INR... Default: `"USD"`. |
| `country` | string | Two-letter country of the traveler (Google shows country-specific prices and booking sites). Default: `"us"`. |
| `propertyType` | string | What Google Hotels returns for each destination. Default: `"all"`. |
| `maxHotelsPerLocation` | integer | In Google's order (20 per page), 1 to 600. Default: `50`. |
| `sortBy` | string | Google's own sort, applied to the whole destination before the properties are read. Default: `"relevance"`. |
| `minHotelClass` | integer | Keep only hotels with at least this star class. |
| `minRating` | number | Keep only properties rated at least this (out of 5). |
| `minPricePerNight` | number | In the chosen currency, before taxes. |
| `maxPricePerNight` | number | In the chosen currency, before taxes. |
| `amenities` | array | Keep only properties that have every amenity picked here (Google's own Amenities filter). |
| `freeCancellation` | boolean | Keep only properties with a free-cancellation rate for your dates. Default: `false`. |
| `ecoCertified` | boolean | Keep only hotels Google marks as eco-certified. Default: `false`. |
| `specialOffers` | boolean | Keep only properties with a deal for your dates. Default: `false`. |
| `language` | string | Two-letter language of descriptions, amenities and review themes: en, fr, es, de, it, pt, ja... Default: `"en"`. |
| `includePrices` | boolean | Open each property for every booking site's offer (Booking.com, Expedia, Agoda, hotel website...) with nightly and total price and booking link, plus address, phone, check-in times and ratings from other sites. $0.004 instead of $0.002 per…. Default: `false`. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |
| `days` | integer | Used when no check-out date is given. |
| `entity` | array | Google Travel hotel IDs (start with `Ch`) or exact hotel names: prices from every booking site are read for them. |
| `device` | string | Google Travel shows some prices only on mobile. Default: `"desktop"`. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "name": "(hidden here)",
  "propertyType": "hotel",
  "hotelClass": 3,
  "hotelClassText": "3-star hotel",
  "rating": 4.3,
  "reviewCount": 456,
  "ratingHistogram": {
    "1": 28,
    "2": 9,
    "3": 38,
    "4": 90,
    "5": 291
  },
  "reviewsBreakdown": [
    {
      "name": "(hidden here)",
      "mentions": "(hidden here)",
      "positive": 44,
      "negative": 5,
      "neutral": 1
    },
    {
      "name": "(hidden here)",
      "mentions": "(hidden here)",
      "positive": 26,
      "negative": 4,
      "neutral": 1
    }
  ],
  "pricePerNight": 82.35,
  "pricePerNightWithTaxes": 100,
  "totalPriceWithTaxes": 100.27,
  "currency": "USD",
  "checkIn": "2026-11-06",
  "checkOut": "2026-11-07",
  "description": "Understated, nature-themed rooms in a casual hotel offering a gym, plus a restaurant with a terrace.",
  "amenities": [
    "Breakfast ($)",
    "Free Wi-Fi"
  ],
  "amenityCodes": [
    165,
    29
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-hotels-scraper").call(run_input={
    "locations": [
        "Lisbon"
    ],
    "maxHotelsPerLocation": 20
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-hotels-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"locations": ["Lisbon"], "maxHotelsPerLocation": 20}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-hotels-scraper` as a tool.

Full documentation, pricing and the latest changes: [Google Hotels Search Scraper - Prices, OTA Rates, Ratings](https://apify.com/om_kh/google-hotels-scraper).

---
title: "Eventbrite Events Scraper - Prices, Organizers $2/1K"
description: "Eventbrite events scraper: eventbrite scraper for any city or online: event name, date, venue, address, GPS, category, ticket price range, free, sold-out and sales status, plus organizer followers, website and socials for lead generation. Up to 1,000 events per search. $2 per 1,000 events."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Eventbrite Events Scraper - Prices, Organizers $2/1K

Eventbrite events scraper: eventbrite scraper for any city or online: event name, date, venue, address, GPS, category, ticket price range, free, sold-out and sales status, plus organizer followers, website and socials for lead generation. Up to 1,000 events per search. $2 per 1,000 events.

**Run it on Apify:** [https://apify.com/om_kh/eventbrite-scraper](https://apify.com/om_kh/eventbrite-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A place (`Montreal, Canada` or `online`) with keywords or a category |
| **We do** | Search Eventbrite and read every event and its organizer |
| **You get** | One row per event (up to 1,000 per search): name, dates, ticket price range, free / sold-out / on-sale status, ticket sales window and checkout link, venue address and GPS, category, and the organizer's followers, website and social links |
| **It costs** | $2 per 1,000 events (organizer details included) + $0.001 per run. The first 10 events of every run are free. No supplier fee |
| **It does not** | Buy tickets or sign in to Eventbrite |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `locations` | array | Cities to search: 'Montreal, Canada', 'New York, NY, USA', 'Paris', or 'online' for online events. Default: `["Montreal, Canada"]`. |
| `country` | string | Optional: a country such as Canada or United States. |
| `city` | string | Optional: a city, used with the country above. |
| `keywords` | array | Optional search words (networking, AI, marketing, yoga...). Default: `["networking"]`. |
| `keyword` | string | One keyword. |
| `category` | string | Optional Eventbrite category, used when no keyword is given. |
| `date` | string | Eventbrite's own date filter. Default: `"any"`. |
| `startDate` | string | Optional, YYYY-MM-DD. |
| `endDate` | string | Optional, YYYY-MM-DD. |
| `freeOnly` | boolean | Only events with free tickets. Default: `false`. |
| `price` | string | Free only is the same as the switch above; paid only drops free events. |
| `searchUrls` | array | Optional. |
| `maxEventsPerSearch` | integer | Eventbrite shows at most 1,000 events for one search. Default: `100`. |
| `maxResults` | integer | Stops the run after this many events in total, whatever the number of searches. 0 or empty: no total limit. |
| `includeDetails` | boolean | Ticket price range, free / sold-out / on-sale status, and the organizer's name, followers, website, Facebook and X. Default: `true`. |
| `includeOrganizerProfile` | boolean | Also read each organizer's page: total events hosted, attendees hosted, years on Eventbrite, upcoming events, all social links. Default: `false`. |
| `onlyNewEvents` | boolean | For scheduled runs: skip events delivered by earlier runs with the same monitor ID. Default: `false`. |
| `monitorId` | string | Optional name that keeps the 'Only new events' history apart for each of your schedules. |
| `maxTotalChargeUsd` | number | The run delivers no more events than this amount pays for. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "event",
  "eventId": "1997503402448",
  "name": "(hidden here)",
  "summary": "Join ECO Canada at the free Environmental Professional Networking Event on November 5th, 2026 in Montreal!",
  "url": "https://www.eventbrite.ca/e/environmental-professionals-meetup-montreal-qc-registration-1997503402448",
  "start": "2026-11-05T17:30",
  "end": "2026-11-05T20:30",
  "timezone": "America/Montreal",
  "isOnline": false,
  "isCancelled": false,
  "language": "en-ca",
  "category": "Business & Professional",
  "subcategory": "Environment & Sustainability",
  "format": "Meeting or Networking Event",
  "tags": [
    "Networking",
    "Environmental"
  ],
  "venueName": "Resto Plateau",
  "address": "4450 Rue Saint-Hubert #Suite 232, Montréal, QC H2J 2W9",
  "city": "Montréal",
  "region": "QC",
  "country": "CA",
  "postalCode": "H2J 2W9",
  "latitude": 45.5250052,
  "longitude": -73.5802526,
  "imageUrl": "https://img.evbuc.com/https%3A%2F%2Fcdn.evbuc.com%2Fimages%2F1190747302%2F66891460325%2F1%2Foriginal.20260810-212015?auto=format%2Ccompre...",
  "organizerId": "4348208881",
  "publishedAt": "2026-08-10T21:22:57Z",
  "isRecurring": false,
  "ticketsBy": "Eventbrite",
  "searchQuery": "networking | Montreal, Canada",
  "searchUrl": "https://www.eventbrite.com/d/canada--montreal/networking/",
  "searchTotalResults": 194,
  "isFree": false,
  "priceMin": 0,
  "priceMax": 13.18,
  "currency": "CAD",
  "isSoldOut": false,
  "hasAvailableTickets": true,
  "salesStatus": "on_sale",
  "organizerName": "ECO Canada",
  "organizerUrl": "https://www.eventbrite.ca/o/eco-canada-4348208881",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/eventbrite-scraper").call(run_input={
    "locations": [
        "Montreal, Canada"
    ],
    "keywords": [
        "networking"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~eventbrite-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"locations": ["Montreal, Canada"], "keywords": ["networking"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/eventbrite-scraper` as a tool.

Full documentation, pricing and the latest changes: [Eventbrite Events Scraper - Prices, Organizers $2/1K](https://apify.com/om_kh/eventbrite-scraper).

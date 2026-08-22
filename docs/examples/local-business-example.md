[← Catalogue home](../../README.md) · [Local Business family](../local-business.md)

# Find newly discovered local businesses and qualify them

## Problem

You want new leads in a category and area — not a static one-time list, but businesses that are genuinely new since you last checked — and then a real contact to reach out to.

## Actors used

1. [Google Maps Business Scraper](https://apify.com/om_kh/vigia-local-business-monitor) — optional, for the full current picture
2. [Google Maps New Business Scraper](https://apify.com/om_kh/vigia-maps-new-business-monitor) — required, for ongoing new-listing detection
3. [Business Email Finder & Verifier](https://apify.com/om_kh/vigia-lead-quality-api) — required, to qualify a contact

## Inputs

```json
{
  "searches": ["coffee shops in Austin, TX"],
  "maxPlacesPerSearch": 10,
  "monitorEnabled": true,
  "maxTotalChargeUsd": 1
}
```

## Steps

1. Run **Google Maps New Business Scraper** with `monitorEnabled: true`. The first run establishes a silent baseline (no alerts yet — see the family page for why). Every run after that reports only listings genuinely new since the last check.
2. For each new business, take its `website` field and pass it to **Business Email Finder & Verifier**.
3. (Optional) Run **Google Maps Business Scraper** without monitoring if you also want the full current picture, not just what's new.

## Sample result shape

*Illustrative — derived from the Actor's real dataset schema, not live data.*

```json
{
  "business_name": "Black Cat Coffee",
  "category": "Coffee shop",
  "address": "603 W Live Oak St, Austin, TX 78704",
  "rating": 5,
  "review_count": 124,
  "website": "https://blkcatcoffee.com/",
  "google_maps_url": "https://www.google.com/maps/search/?api=1&query=Black%20Cat%20Coffee&query_place_id=..."
}
```

## Try it live

[Public Task example (coffee shops, Austin TX)](https://apify.com/om_kh/vigia-maps-new-business-monitor/examples/vigia-maps-new-business-monitor-quickstart)

## Code

### curl

```bash
curl "https://api.apify.com/v2/actor-tasks/om_kh~vigia-maps-new-business-monitor-quickstart/run-sync-get-dataset-items?token=$APIFY_TOKEN" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"searches": ["coffee shops in Austin, TX"], "maxPlacesPerSearch": 10, "monitorEnabled": true, "maxTotalChargeUsd": 1}'
```

### Python

```python
import os, requests

token = os.environ["APIFY_TOKEN"]
url = "https://api.apify.com/v2/actor-tasks/om_kh~vigia-maps-new-business-monitor-quickstart/run-sync-get-dataset-items"
resp = requests.post(url, params={"token": token}, json={
    "searches": ["coffee shops in Austin, TX"],
    "maxPlacesPerSearch": 10,
    "monitorEnabled": True,
    "maxTotalChargeUsd": 1,
})
new_businesses = resp.json()
```

## Next step

See [Leads & Verification](../leads-verification.md) for the qualification-step Actor used above.

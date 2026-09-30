---
title: "Find Newly Opened Businesses on Google Maps by City"
description: "Get businesses that newly appeared on Google Maps for any category and city — name, address, rating, categories — for local B2B lead generation."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Find Newly Opened Businesses on Google Maps by City

## How do I find new businesses that just opened in my city?

Use **New Business Leads — New Google Maps Listings**. Give it searches like 'coffee shops in Austin, TX'. The first run returns the full current list; with monitoring on and a schedule, later runs return **only businesses that newly appeared**. That is the moment new owners buy POS systems, insurance, marketing and supplies.

**Try it:** [New Business Leads — Google Maps on Apify](https://apify.com/om_kh/google-maps-new-business-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [New Business Leads — Google Maps](https://apify.com/om_kh/google-maps-new-business-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "searches": [
    "coffee shops in Austin, TX"
  ],
  "maxPlacesPerSearch": 50,
  "monitorEnabled": true
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-maps-new-business-scraper").call(run_input={
    "searches": [
        "coffee shops in Austin, TX"
    ],
    "maxPlacesPerSearch": 50,
    "monitorEnabled": True
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-maps-new-business-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searches": ["coffee shops in Austin, TX"], "maxPlacesPerSearch": 50, "monitorEnabled": true}'
```

## What you get

- `place_id`
- `title` (business name)
- `address`
- `rating`
- `reviews_count`
- `categories`
- `phone` / website / url when Google Maps shows them

## Price

$0.01 per new business, $0.08 per monitored search re-check. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- Local B2B sales (POS, insurance, marketing agencies, suppliers)
- Market-entry tracking for franchises
- Local news and directories

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-maps-new-business-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**How do I get only new ones?**  
Set `monitorEnabled: true` and schedule the Actor daily or weekly.

**Can I run several cities?**  
Yes, add one search per city and category.

## Related

- [Google Maps Business Scraper - Name, Rating, Address](https://apify.com/om_kh/google-maps-business-scraper)
- [Business Email Finder API - Verify, Score, Confidence](https://apify.com/om_kh/vigia-lead-quality-api)
- [Google Maps Reviews Scraper - Rating, Text, Reviewer](https://apify.com/om_kh/google-maps-reviews-scraper)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I find new businesses that just opened in my city?", "acceptedAnswer": {"@type": "Answer", "text": "Use New Business Leads — New Google Maps Listings. Give it searches like 'coffee shops in Austin, TX'. The first run returns the full current list; with monitoring on and a schedule, later runs return only businesses that newly appeared. That is the moment new owners buy POS systems, insurance, marketing and supplies."}}, {"@type": "Question", "name": "How do I get only new ones?", "acceptedAnswer": {"@type": "Answer", "text": "Set `monitorEnabled: true` and schedule the Actor daily or weekly."}}, {"@type": "Question", "name": "Can I run several cities?", "acceptedAnswer": {"@type": "Answer", "text": "Yes, add one search per city and category."}}]}
</script>

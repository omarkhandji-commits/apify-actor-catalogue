---
title: "Find YouTube Channels by Niche — Subscribers, Country, Business Email"
description: "Search YouTube channels by keyword, filter by subscriber count and country, and get social links and public business emails for influencer outreach."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Find YouTube Channels by Niche — Subscribers, Country, Business Email

## How do I find YouTube influencers in a niche with their email?

Use the **YouTube Channel Search Scraper**: give it keywords, optional min/max subscribers and a country. It returns one row per channel (name, handle, subscribers, description, link) and, with enrichment on, the country, total views, join date, social links and the **business email the creator publishes in their bio**, checked against the domain's mail server. Emails are never guessed. $0.50 per 1,000 channels, +$0.002 per enriched channel.

**Try it:** [YouTube Channel Search Scraper on Apify](https://apify.com/om_kh/youtube-channel-search-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [YouTube Channel Search Scraper](https://apify.com/om_kh/youtube-channel-search-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "searchTerms": [
    "personal finance"
  ],
  "maxChannels": 100,
  "minSubscribers": 10000,
  "maxSubscribers": 500000,
  "enrichChannels": true,
  "country": "United States"
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/youtube-channel-search-scraper").call(run_input={
    "searchTerms": [
        "personal finance"
    ],
    "maxChannels": 100,
    "minSubscribers": 10000,
    "maxSubscribers": 500000,
    "enrichChannels": True,
    "country": "United States"
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~youtube-channel-search-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["personal finance"], "maxChannels": 100, "minSubscribers": 10000, "maxSubscribers": 500000, "enrichChannels": true, "country": "United States"}'
```

## What you get

- `channelId`
- `title`
- `handle`
- `subscribers`
- `description`
- `channelUrl`
- `country`
- `totalViews`
- `videoCount`
- `joinedAt`
- `socialLinks`
- `websiteLinks`
- `businessEmail` (email, verification_level)

## Price

$0.0005 per channel, +$0.002 per enriched channel, first 10 channels free. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- Influencer marketing shortlists by size and country
- Sponsorship and agency prospecting
- Mapping who owns a topic on YouTube

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/youtube-channel-search-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Where do the emails come from?**  
Only from the public channel description. The hidden 'View email address' button is not bypassed.

**Can I keep only micro-influencers?**  
Yes, use `minSubscribers` and `maxSubscribers`.

**I want engagement and activity filters too**  
Use [YouTube Creator Lead Finder](https://apify.com/om_kh/youtube-creator-lead-finder): median recent views, activity window and verified contact.

## Related

- [YouTube Creator Lead Finder - Views, Niche, Email](https://apify.com/om_kh/youtube-creator-lead-finder)
- [YouTube Channel Videos Scraper - Exact Views, $0.50/1K](https://apify.com/om_kh/youtube-channel-videos-scraper)
- [Instagram Following & Related Profiles Scraper - Full List](https://apify.com/om_kh/instagram-following-scraper)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I find YouTube influencers in a niche with their email?", "acceptedAnswer": {"@type": "Answer", "text": "Use the YouTube Channel Search Scraper: give it keywords, optional min/max subscribers and a country. It returns one row per channel (name, handle, subscribers, description, link) and, with enrichment on, the country, total views, join date, social links and the business email the creator publishes in their bio, checked against the domain's mail server. Emails are never guessed. $0.50 per 1,000 channels, +$0.002 per enriched channel."}}, {"@type": "Question", "name": "Where do the emails come from?", "acceptedAnswer": {"@type": "Answer", "text": "Only from the public channel description. The hidden 'View email address' button is not bypassed."}}, {"@type": "Question", "name": "Can I keep only micro-influencers?", "acceptedAnswer": {"@type": "Answer", "text": "Yes, use `minSubscribers` and `maxSubscribers`."}}, {"@type": "Question", "name": "I want engagement and activity filters too", "acceptedAnswer": {"@type": "Answer", "text": "Use [YouTube Creator Lead Finder](https://apify.com/om_kh/youtube-creator-lead-finder): median recent views, activity window and verified contact."}}]}
</script>

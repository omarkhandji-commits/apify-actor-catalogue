---
title: "Export the Instagram Following List of Any Public Account"
description: "Get the accounts a public Instagram profile follows, with username, full name, followers and public contact, as CSV or JSON."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Export the Instagram Following List of Any Public Account

## How do I export who an Instagram account follows?

Use the **Instagram Following Scraper** with a public username. It returns the accounts that profile follows (or related profiles), one row per account: username, profile link, full name, and with enrichment the follower count and public business contact. Useful for finding brands, creators and partners in a niche from one seed account.

**Try it:** [Instagram Following Scraper on Apify](https://apify.com/om_kh/instagram-following-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [Instagram Following Scraper](https://apify.com/om_kh/instagram-following-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "username": "natgeo",
  "mode": "following",
  "maxResults": 200,
  "enrichProfiles": true
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/instagram-following-scraper").call(run_input={
    "username": "natgeo",
    "mode": "following",
    "maxResults": 200,
    "enrichProfiles": True
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~instagram-following-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"username": "natgeo", "mode": "following", "maxResults": 200, "enrichProfiles": true}'
```

## What you get

- `username`
- `profile_url`
- `full_name`
- `followers`
- `public_contact`
- `status`

## Price

$0.002 per account listed, +$0.0008 per enriched profile. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- Influencer and partner discovery from a seed account
- Competitor network analysis
- Lead lists of brands in a niche

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/instagram-following-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Does it work on private accounts?**  
No, only public profiles.

**Do I need to log in?**  
No login or cookies from you are needed.

## Related

- [Instagram Lookalike Scraper - Similar Accounts, Followers, Bio](https://apify.com/om_kh/instagram-profile-lookalike-scraper)
- [Instagram Profile Scraper - Followers, Bio, Posts Data](https://apify.com/om_kh/instagram-profile-scraper)
- [YouTube Channel Search Scraper - Subscribers, Emails](https://apify.com/om_kh/youtube-channel-search-scraper)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I export who an Instagram account follows?", "acceptedAnswer": {"@type": "Answer", "text": "Use the Instagram Following Scraper with a public username. It returns the accounts that profile follows (or related profiles), one row per account: username, profile link, full name, and with enrichment the follower count and public business contact. Useful for finding brands, creators and partners in a niche from one seed account."}}, {"@type": "Question", "name": "Does it work on private accounts?", "acceptedAnswer": {"@type": "Answer", "text": "No, only public profiles."}}, {"@type": "Question", "name": "Do I need to log in?", "acceptedAnswer": {"@type": "Answer", "text": "No login or cookies from you are needed."}}]}
</script>

---
title: "YouTube Channel Email Finder — Business Emails of Creators"
description: "Get the public business email of YouTube channels from the channel bio or the creator's website, MX-checked, with socials, country and subscribers."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# YouTube Channel Email Finder — Business Emails of Creators

## How do I find the email address of a YouTube channel?

Use the **YouTube Channel Email Scraper** with channel URLs, @handles or keywords. For each channel it reads the business email written in the channel description; if there is none, it opens the creator's own website (home and /contact page). Every email is checked against its domain's mail server. It also flags channels whose email is hidden behind YouTube's "View email address" button (never bypassed). $0.004 per email found + $0.0005 per channel checked.

**Try it:** [YouTube Channel Email Scraper on Apify](https://apify.com/om_kh/youtube-channel-email-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [YouTube Channel Email Scraper](https://apify.com/om_kh/youtube-channel-email-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "channels": [
    "@mkbhd",
    "@veritasium"
  ],
  "searchTerms": [
    "personal finance"
  ],
  "maxChannelsPerSearch": 100,
  "onlyWithEmail": true
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/youtube-channel-email-scraper").call(run_input={
    "channels": [
        "@mkbhd",
        "@veritasium"
    ],
    "searchTerms": [
        "personal finance"
    ],
    "maxChannelsPerSearch": 100,
    "onlyWithEmail": True
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~youtube-channel-email-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"channels": ["@mkbhd", "@veritasium"], "searchTerms": ["personal finance"], "maxChannelsPerSearch": 100, "onlyWithEmail": true}'
```

## What you get

- `title`
- `handle`
- `email`
- `emailFoundIn` (channel_bio / website)
- `emailVerification` (mx_valid / published)
- `hasHiddenEmail`
- `subscribers`
- `country`
- `socialLinks`
- `websiteLinks`
- `channelUrl`

## Price

$0.004 per email found, $0.0005 per channel checked, no start fee. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- Influencer and sponsorship outreach
- Agency prospect lists by niche and country
- Enriching a list of channels you already track

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/youtube-channel-email-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Are emails guessed?**  
No. Only emails the creator publishes in the bio or on their own website.

**What does hasHiddenEmail mean?**  
The channel shares an email only through YouTube's protected button, which needs a signed-in human.

## Related

- [YouTube Channel Search Scraper - Subscribers, Emails](https://apify.com/om_kh/youtube-channel-search-scraper)
- [YouTube Creator Lead Finder - Views, Niche, Email](https://apify.com/om_kh/youtube-creator-lead-finder)
- [Business Email Finder API - Verify, Score, Confidence](https://apify.com/om_kh/vigia-lead-quality-api)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I find the email address of a YouTube channel?", "acceptedAnswer": {"@type": "Answer", "text": "Use the YouTube Channel Email Scraper with channel URLs, @handles or keywords. For each channel it reads the business email written in the channel description; if there is none, it opens the creator's own website (home and /contact page). Every email is checked against its domain's mail server. It also flags channels whose email is hidden behind YouTube's \"View email address\" button (never bypassed). $0.004 per email found + $0.0005 per channel checked."}}, {"@type": "Question", "name": "Are emails guessed?", "acceptedAnswer": {"@type": "Answer", "text": "No. Only emails the creator publishes in the bio or on their own website."}}, {"@type": "Question", "name": "What does hasHiddenEmail mean?", "acceptedAnswer": {"@type": "Answer", "text": "The channel shares an email only through YouTube's protected button, which needs a signed-in human."}}]}
</script>

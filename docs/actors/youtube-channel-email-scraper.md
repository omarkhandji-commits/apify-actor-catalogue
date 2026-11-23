---
title: "YouTube Business Email Scraper - Bio, Website, Videos $4/1K"
description: "YouTube business email scraper: find more YouTube creator emails: from the bio, the creator's website and link page, and their latest videos, Steam and podcast pages. MX-checked, no login, with last upload date and average views. Tested: 36 of 59 channels. $4 per 1,000 emails."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# YouTube Business Email Scraper - Bio, Website, Videos $4/1K

YouTube business email scraper: find more YouTube creator emails: from the bio, the creator's website and link page, and their latest videos, Steam and podcast pages. MX-checked, no login, with last upload date and average views. Tested: 36 of 59 channels. $4 per 1,000 emails.

**Run it on Apify:** [https://apify.com/om_kh/youtube-channel-email-scraper](https://apify.com/om_kh/youtube-channel-email-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | YouTube @handles, channel links, or a keyword such as `home workout` |
| **We do** | Read the channel bio, the creator's own website and link-in-bio page, their latest video descriptions, their Steam game page and their podcast feed, then check that the email's domain can receive mail |
| **You get** | One row per channel: the public email, where it was found, subscribers, country, social links, website, last upload date and average views of the latest videos. Expect an email for about 6 channels in 10 (36 of 59 in our public test of 2026-11-03) |
| **It costs** | $0.50 per 1,000 channels checked + $4 per 1,000 emails found, + $0.001 per run from Dec 1, 2026 (no start fee before). 1,000 channels with 250 emails = **$1.50**. The first 10 results of every run are free |
| **It does not** | Sign in to YouTube, solve CAPTCHAs, or read the email hidden behind YouTube's "View email address" button (those channels are flagged with `hasHiddenEmail`) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `channels` | array | YouTube channel URLs, @handles or channel IDs (UC...), one per line. Default: `["https://www.youtube.com/@mkbhd", "@veritasium"]`. |
| `searchTerms` | array | Optional keywords: the Actor runs YouTube's channel search and checks every channel found (up to 20 keywords). Default: `["home workout"]`. |
| `maxChannelsPerSearch` | integer | 1 to 500. Default: `50`. |
| `minSubscribers` | integer | Optional, keyword search only: skip channels below this size. |
| `maxSubscribers` | integer | Optional, keyword search only: skip channels above this size (micro-influencers). |
| `country` | string | Optional: keep only channels whose About page shows this country (e.g. United States, France). |
| `followWebsites` | boolean | When the bio has no email, open the creator's own links (website contact, about and legal pages, Linktree-type pages) and then the descriptions of the 5 latest videos to find a public email. Default: `true`. |
| `includeActivity` | boolean | Adds lastUploadAt, daysSinceLastUpload and recentAvgViews (average views of the 10 latest videos) to every channel, so you can skip inactive creators. Default: `true`. |
| `onlyWithEmail` | boolean | Hide checked channels without a public email from the results. Default: `false`. |
| `skipKnownChannels` | boolean | Remembers every channel your runs returned (in a key-value store of your own account) and skips them in later runs, so a repeated keyword search never charges the same channel twice. Default: `false`. |
| `memoryName` | string | Name of the key-value store that holds the remembered channels. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "channelId": "UCsLF0qPTpkYKq81HsjgzhwQ",
  "title": "growingannanas",
  "handle": "(hidden here)",
  "channelUrl": "https://www.youtube.com/@growingannanas",
  "email": "(hidden here)",
  "emailFoundIn": "(hidden here)",
  "emailSource": "(hidden here)",
  "emailVerification": "(hidden here)",
  "hasHiddenEmail": "(hidden here)",
  "allEmails": "(hidden here)",
  "subscribers": 8220000,
  "country": "Germany",
  "totalViews": 4673766124,
  "videoCount": 1359,
  "joinedAt": "2017-01-20",
  "socialLinks": [
    "https://instagram.com/growingannanas"
  ],
  "websiteLinks": [
    "https://growwithanna.com"
  ],
  "description": "I make people move\n",
  "searchQuery": "home workout",
  "lastUploadAt": "2026-11-02",
  "daysSinceLastUpload": 3,
  "recentAvgViews": 310900,
  "recentVideosCounted": 10
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/youtube-channel-email-scraper").call(run_input={
    "channels": [
        "https://www.youtube.com/@mkbhd",
        "@veritasium"
    ],
    "searchTerms": [
        "home workout"
    ],
    "maxChannelsPerSearch": 15
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~youtube-channel-email-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"channels": ["https://www.youtube.com/@mkbhd", "@veritasium"], "searchTerms": ["home workout"], "maxChannelsPerSearch": 15}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/youtube-channel-email-scraper` as a tool.

Full documentation, pricing and the latest changes: [YouTube Business Email Scraper - Bio, Website, Videos $4/1K](https://apify.com/om_kh/youtube-channel-email-scraper).

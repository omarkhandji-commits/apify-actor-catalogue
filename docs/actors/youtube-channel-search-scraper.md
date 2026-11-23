---
title: "YouTube Channel Search Scraper - Subscribers, Emails"
description: "YouTube channel search: find channels by keyword or through the videos that rank, up to 1,000 per search. Filters: subscribers, videos, verified, country. Optional country, total views, social links, public business email and latest uploads. $0.50 per 1,000 channels. API and MCP."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# YouTube Channel Search Scraper - Subscribers, Emails

YouTube channel search: find channels by keyword or through the videos that rank, up to 1,000 per search. Filters: subscribers, videos, verified, country. Optional country, total views, social links, public business email and latest uploads. $0.50 per 1,000 channels. API and MCP.

**Run it on Apify:** [https://apify.com/om_kh/youtube-channel-search-scraper](https://apify.com/om_kh/youtube-channel-search-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords (up to 500 per run) or YouTube search links |
| **We do** | Search YouTube for channels, through its channel filter or through the videos that rank |
| **You get** | One row per channel: name, handle, subscribers, description and link. Option: country, total views, video count, join date, social links, the public email from the bio (mail-checked), whether a business-email button exists, family-safe flag, the countries where the channel is available, and the latest uploads with views, date and length |
| **It costs** | $0.50 per 1,000 channels, + $0.002 per channel with the option on, + $0.001 per run. The first 10 channels of every run are free |
| **It does not** | Read emails hidden behind YouTube's "View email address" button, or keep channels that hide their subscriber count when you set a minimum |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchTerms` | array | Topics, products or types of creators to search YouTube for, one per line (up to 500 with the files and links below). Default: `["personal finance"]`. |
| `searchUrls` | array | Paste youtube.com/results links to run a search again exactly as you set it on YouTube, filters included. |
| `searchTermsFiles` | array | Up to 20 TXT or CSV files, one term per line (first column of a CSV). |
| `discoveryMode` | string | The channel filter returns channels YouTube matches by name and topic. Default: `"channelFilter"`. |
| `maxChannels` | integer | Channels saved per search term or search link, after filters (1 to 1,000). Default: `50`. |
| `minSubscribers` | integer | Optional: skip channels below this subscriber count. |
| `maxSubscribers` | integer | Optional: skip channels above this subscriber count (great for micro-influencers). |
| `minVideos` | integer | Optional: keep only channels with at least this many public videos. |
| `verifiedOnly` | boolean | Keep only channels YouTube marks as verified. Default: `false`. |
| `excludedChannels` | array | Channel links, @handles or channel IDs that must never be returned (your own channels, ones you already have). |
| `skipKnownChannels` | boolean | Remembers every channel your runs delivered (in a key-value store of your own account) and skips them in later runs, so a repeated search never charges the same channel twice. Default: `false`. |
| `memoryName` | string | Name of the key-value store that holds the remembered channels, one per campaign or client. |
| `maxTotalResults` | integer | Stop after this many channels over all searches. |
| `countryHint` | string | Two-letter country YouTube ranks the search for: US, FR, DE, BR... |
| `languageHint` | string | Two-letter language YouTube ranks the search for: en, fr, es, de... |
| `enrichChannels` | boolean | Adds country, exact subscribers, total views, join date, social and website links, and a public business email from the channel bio (MX-checked). +$0.002 per enriched channel. Default: `false`. |
| `includeRecentVideos` | boolean | Adds each channel's latest uploads (title, link, views, upload date, length) plus last upload date, days since and average recent views. Default: `false`. |
| `maxRecentVideos` | integer | How many latest uploads to add per channel when recent videos are on (1 to 30). Default: `10`. |
| `country` | string | Optional: keep only channels whose About page lists this country (e.g. United States, France). |
| `maxTotalChargeUsd` | number | Optional hard cap on what this run can cost you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "input_ref": "personal finance",
  "channelId": "UCMw07uiVxGULqePlrOZnx9A",
  "title": "Personal Finance with Leila - Debt Over It",
  "handle": "(hidden here)",
  "subscribers": 68500,
  "subscribersText": "68.5K subscribers",
  "description": "I help overwhelmed individuals get control of their money and build better habits so they can pay off debt, save consistently, and ...",
  "isVerified": false,
  "thumbnailUrl": "https://yt3.ggpht.com/jQWukM-SKjnmxhCuILiOXLCCBF8jAYgSqQUsyMFyoE7x_0HrSUweTFvALQVqEiAT5oBFhzvZDwc=s176-c-k-c0x00ffffff-no-rj-mo",
  "channelUrl": "https://www.youtube.com/@PersonalFinancewithLeila",
  "rank": 1,
  "searchQuery": "personal finance",
  "discoverySource": "channel",
  "videoCount": 1261,
  "country": "United States",
  "totalViews": 9769727,
  "joinedAt": "2019-12-04",
  "avatarUrl": "https://yt3.googleusercontent.com/jQWukM-SKjnmxhCuILiOXLCCBF8jAYgSqQUsyMFyoE7x_0HrSUweTFvALQVqEiAT5oBFhzvZDwc=s900-c-k-c0x00ffffff-no-rj",
  "bannerUrl": "https://yt3.googleusercontent.com/noGUeJA0fN9J5uuJY4mQ8N7mXyY6xomRS8HyOmNvSBasOJSDDO1YyAhWbPjb8y_z2K9iwX8clw=w2560-fcrop64=1,00005a57ffffa5a8-k-c0xffffffff-no-nd-rj",
  "totalViewsText": "9,769,727 views",
  "videoCountText": "1,261 videos",
  "joinedText": "Joined Dec 4, 2019",
  "hasBusinessEmailButton": true,
  "isFamilySafe": true,
  "availableCountryCodes": [
    "SI",
    "MY",
    "VG",
    "MD",
    "PR",
    "... 249 in total"
  ],
  "ownerUrls": [
    "http://www.youtube.com/@PersonalFinancewithLeila"
  ],
  "recentVideos": [
    {
      "videoId": "MuwCtxEZZM4",
      "title": "Another $10K+ month, over budget, lower net worth | 2026 Finance Update",
      "url": "https://www.youtube.com/watch?v=MuwCtxEZZM4",
      "views": 7000,
      "publishedText": "2 days ago",
      "publishedAt": "2026-11-09",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/youtube-channel-search-scraper").call(run_input={
    "searchTerms": [
        "personal finance"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~youtube-channel-search-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["personal finance"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/youtube-channel-search-scraper` as a tool.

Full documentation, pricing and the latest changes: [YouTube Channel Search Scraper - Subscribers, Emails](https://apify.com/om_kh/youtube-channel-search-scraper).

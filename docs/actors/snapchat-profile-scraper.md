---
title: "Snapchat Profile Scraper - Subscribers, Bio, Spotlight"
description: "Scrape public Snapchat profiles: name, subscribers, bio, website, bio emails, verified badge and related accounts. Public story snaps and highlights with media links, Spotlight views, and optionally every Spotlight video with views, date and hashtags. No login. $1.50 per 1,000 profiles."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Snapchat Profile Scraper - Subscribers, Bio, Spotlight

Scrape public Snapchat profiles: name, subscribers, bio, website, bio emails, verified badge and related accounts. Public story snaps and highlights with media links, Spotlight views, and optionally every Spotlight video with views, date and hashtags. No login. $1.50 per 1,000 profiles.

**Run it on Apify:** [https://apify.com/om_kh/snapchat-profile-scraper](https://apify.com/om_kh/snapchat-profile-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Snapchat usernames |
| **We do** | Read each public profile |
| **You get** | One row per profile: display name, subscribers, bio, website, emails written in the bio, verified badge, story, highlights, lenses, related accounts and Spotlight views; option: every Spotlight video with its link, views, shares, comments and boosts, plus its likes, top comments (up to 25) and transcript |
| **It costs** | $1.50 per 1,000 profiles, + $0.001 per Spotlight video if you ask for them, + $0.001 per run from Dec 2, 2026 (no start fee before). A username that does not exist is never charged. No supplier fee |
| **It does not** | Read private personal accounts or sign in to Snapchat |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `profiles` | array | Snapchat usernames or profile links (snapchat.com/add/...), one per line (up to 1,000). Default: `["kyliejenner", "https://www.snapchat.com/add/mrbeast"]`. |
| `includeSpotlightVideos` | boolean | Also return one row per public Spotlight video (views, upload date, thumbnail, video URL). +$0.001 per video. Default: `false`. |
| `includeSpotlightComments` | boolean | With Spotlight videos on: open each video's page for its like count and the top comments Snapchat shows (up to 25: text, date, author, replies). Default: `false`. |
| `includeTranscripts` | boolean | With Spotlight videos on: add the spoken transcript when Snapchat publishes one for the video (many videos have none). Default: `false`. |
| `includeStories` | boolean | Add to each profile its public story snaps and its highlights, with media links, previews and times. Default: `true`. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "profile",
  "username": "(hidden here)",
  "displayName": "(hidden here)",
  "profileUrl": "https://www.snapchat.com/add/kyliejenner",
  "subscribers": 28624200,
  "website": "https://kyliecosmetics.com",
  "isVerified": true,
  "createdAt": "2019-05-22T18:01:50Z",
  "lastUpdatedAt": "2026-10-24T21:32:39Z",
  "heroImageUrl": "https://cf-st.sc-cdn.net/aps/bolt/aHR0cHM6Ly9jZi1zdC5zYy1jZG4ubmV0L2QvakRGcnNVaW1ta2ZsamFPa1ZUTWVwP2JvPUVna3lBUVJJQWxBWllBRSUzRCZ1Yz0yNQ....",
  "isBusinessProfile": true,
  "spotlightHighlights": 16,
  "profilePictureUrl": "(hidden here)",
  "snapcodeUrl": "https://app.snapchat.com/web/deeplink/snapcode?username=kyliejenner&type=SVG&bitmoji=enable",
  "hasPublicStory": true,
  "publicStorySnaps": 211,
  "curatedHighlights": 18,
  "storySnaps": [
    {
      "index": 0,
      "mediaType": "video",
      "mediaUrl": "https://cf-st.sc-cdn.net/d/rUB1zo7dyhJGmM1UtDTQb.1034.IRZXSOY?mo=Gl8aGDIBBDoBfUIGCNSR2tYGSAJQS2ABaA1wAVCwAaIBOwiKCBIlCiMIh4Q1IAEw4AM4gAVA...",
      "previewUrl": "https://cf-st.sc-cdn.net/d/rUB1zo7dyhJGmM1UtDTQb.256.IRZXSOY?mo=GlMaDjICBH1IAlBLYAFoDXABUI4BWhBEZkxhcmdlVGh1bWJuYWlsogEUCIACIg8KAmgNEgAqB...",
      "postedAt": "2026-10-19T21:16:21Z"
    },
    {
      "index": 1,
      "mediaType": "video",
      "mediaUrl": "https://cf-st.sc-cdn.net/d/zhE0LAI96OEqqsnn1UqbH.1034.IRZXSOY?mo=Gl8aGDIBBDoBfUIGCMyR2tYGSAJQS2ABaA1wAVCwAaIBOwiKCBIlCiMI_8A8IAEw4AM4gAVA...",
      "previewUrl": "https://cf-st.sc-cdn.net/d/zhE0LAI96OEqqsnn1UqbH.256.IRZXSOY?mo=GlMaDjICBH1IAlBLYAFoDXABUI4BWhBEZkxhcmdlVGh1bWJuYWlsogEUCIACIg8KAmgNEgAqB...",
      "postedAt": "2026-10-19T21:16:24Z"
    }
  ],
  "highlights": [
    {
      "title": "my morning <3",
      "thumbnailUrl": "https://cf-st.sc-cdn.net/d/2c69RsW8eVxCmzNW3mvYh.410?mo=GjcaFjIBBDoBfUIGCP2answGSAJQXmABcAFQxQFaEERmTGFyZ2VUaHVtYm5haWyiAQcImgMiAhIA&uc=94",
      "snaps": [
        {
          "index": 0,
          "mediaType": "video",
          "mediaUrl": "https://cf-st.sc-cdn.net/d/2c69RsW8eVxCmzNW3mvYh.1322?mo=GlkaFjIBBDoBfUIGCP2answGSAJQXmABcAFQwgFaB0RmTWVkaWGiAS4IqgoSJQojCKf_KyABMOADONQG...",
          "previewUrl": "https://cf-st.sc-cdn.net/d/2c69RsW8eVxCmzNW3mvYh.410?mo=GjcaFjIBBDoBfUIGCP2answGSAJQXmABcAFQxQFaEERmTGFyZ2VUaHVtYm5haWyiAQcImgMiAhIA&uc=94",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/snapchat-profile-scraper").call(run_input={
    "profiles": [
        "kyliejenner",
        "https://www.snapchat.com/add/mrbeast"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~snapchat-profile-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"profiles": ["kyliejenner", "https://www.snapchat.com/add/mrbeast"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/snapchat-profile-scraper` as a tool.

Full documentation, pricing and the latest changes: [Snapchat Profile Scraper - Subscribers, Bio, Spotlight](https://apify.com/om_kh/snapchat-profile-scraper).

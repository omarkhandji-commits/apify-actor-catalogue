---
title: "Facebook Page Info Scraper - Followers, Contact, About"
description: "Facebook page info scraper: any public page's name, category, followers, likes, description, website, phone and address. Paste page URLs, export to JSON, CSV or Excel, or call it as an API. No login needed. For lead generation, enrichment and competitor research. $10/1K pages, $1.56/1K from 16 Dec."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Facebook Page Info Scraper - Followers, Contact, About

Facebook page info scraper: any public page's name, category, followers, likes, description, website, phone and address. Paste page URLs, export to JSON, CSV or Excel, or call it as an API. No login needed. For lead generation, enrichment and competitor research. $10/1K pages, $1.56/1K from 16 Dec.

**Run it on Apify:** [https://apify.com/om_kh/facebook-page-scraper](https://apify.com/om_kh/facebook-page-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Public Facebook page links |
| **We do** | Read each page's public profile, and compare with your last run |
| **You get** | One row per page: name, category, followers, likes, website, phone, creation date, ad status and confirmed owner, plus every field the supplier returns (`source_data`) |
| **It costs** | $10 per 1,000 pages today, $1.56 per 1,000 from 16 December 2026 + $0.001 per run. Optional scheduled monitoring: +$0.35 per check today, $0.005 from 16 December 2026 (one-off runs never pay it). Apify also bills the supplier Actor `apify/facebook-pages-scraper` that this robot runs for you, at its own price (about $12 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Facebook or read private profiles |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `pageUrls` | array | Facebook page URLs to monitor for follower/post changes. |
| `currentProfiles` | array | Skip the chained fetch and pass page data directly. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Facebook pages actor", "authorization": "`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "profile_id": "facebook:nike",
  "platform": "facebook",
  "username": "(hidden here)",
  "followers": 39000000,
  "website": "http://nike.com/",
  "facebookUrl": "https://www.facebook.com/nike",
  "categories": [
    "Page",
    "Sportswear Store"
  ],
  "info": [
    "Nike. 39,497,682 followers",
    "140,661 talking about this"
  ],
  "likes": 0,
  "title": "Nike",
  "pageId": "100044541544829",
  "pageName": "nike",
  "pageUrl": "https://www.facebook.com/nike",
  "websites": [
    "http://nike.com/"
  ],
  "CONFIRMED_OWNER_LABEL": "NIKE, Inc.",
  "phone": "(hidden here)",
  "followings": "(hidden here)",
  "profilePictureUrl": "(hidden here)",
  "coverPhotoUrl": "https://scontent-hou1-1.xx.fbcdn.net/v/t39.30808-6/285211224_10159903868008445_5477337468887983165_n.png?stp=dst-png&cstp=mx851x315&ctp=s...",
  "profilePhoto": "https://www.facebook.com/photo/?fbid=865378788290165&set=a.865378794956831",
  "category": "Sportswear Store",
  "creation_date": "May 21, 2008",
  "ad_status": "This Page is currently running ads.",
  "confirmed_owner": "NIKE, Inc. is responsible for this Page.",
  "facebookId": "100044541544829",
  "record_id": "facebook:nike",
  "change_type": "new",
  "why_it_matters": "A tracked item changed."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/facebook-page-scraper").call(run_input={
    "pageUrls": [
        "https://www.facebook.com/nike",
        "https://www.facebook.com/allbirds"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~facebook-page-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"pageUrls": ["https://www.facebook.com/nike", "https://www.facebook.com/allbirds"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/facebook-page-scraper` as a tool.

Full documentation, pricing and the latest changes: [Facebook Page Info Scraper - Followers, Contact, About](https://apify.com/om_kh/facebook-page-scraper).

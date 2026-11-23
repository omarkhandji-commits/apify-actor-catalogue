---
title: "LinkedIn Company Info Scraper - Employee Count, Size, HQ"
description: "LinkedIn company info scraper: name, tagline, industry, size, exact employee count, followers, headquarters, type, founded year, specialties, website, logo and latest post. Paste company links or names. $4 per 1,000 companies + $0.001 per run. No login, no cookies. JSON, CSV, API, MCP."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# LinkedIn Company Info Scraper - Employee Count, Size, HQ

LinkedIn company info scraper: name, tagline, industry, size, exact employee count, followers, headquarters, type, founded year, specialties, website, logo and latest post. Paste company links or names. $4 per 1,000 companies + $0.001 per run. No login, no cookies. JSON, CSV, API, MCP.

**Run it on Apify:** [https://apify.com/om_kh/linkedin-company-scraper](https://apify.com/om_kh/linkedin-company-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Company names or LinkedIn company links |
| **We do** | Read each company's public LinkedIn page |
| **You get** | One row per company: name, industry, size, employee count, followers, headquarters, founded year, specialties, website, description, every office, similar and affiliated pages, cover image and latest post, plus every field the supplier returns (`source_data`) |
| **It costs** | $4 per 1,000 companies, $3 per 1,000 from 7 December 2026, + $0.001 per run. A company that cannot be found is not charged. No supplier fee |
| **It does not** | Sign in to LinkedIn or list employees |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `companies` | array | Company names or LinkedIn company URLs to monitor. Default: `["Stripe", "Notion"]`. |
| `currentProfiles` | array | Skip the chained fetch and pass profile data directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained profile actor", "authorization": "public_`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |

## Example output

A row as shown in the Actor's README:

```json
{
  "profile_id": "linkedin:Stripe",
  "platform": "linkedin",
  "username": "(hidden here)",
  "followers": 1784465,
  "posts_count": 16694,
  "latest_post_id": "7519107159457038336",
  "bio": "Stripe builds programmable financial services. Millions of companies—from the world’s largest enterprises to the most ambitious startups—...",
  "website": "https://stripe.com",
  "companyName": "Stripe",
  "universalName": "stripe",
  "linkedinUrl": "https://www.linkedin.com/company/stripe",
  "tagline": "Help increase the GDP of the internet.",
  "description": "Stripe builds programmable financial services. Millions of companies—from the world’s largest enterprises to the most ambitious startups—...",
  "industry": "Technology, Information and Internet",
  "companySize": "5,001-10,000 employees",
  "employeeCount": 16694,
  "followerCount": 1784465,
  "headquarters": "South San Francisco, California",
  "organizationType": "Privately Held",
  "foundedYear": 2010,
  "logoUrl": "https://media.licdn.com/dms/image/v2/D560BAQE2ZfJyfn-VCg/company-logo_200_200/B56ZlyKwpUKIAI-/0/1758557047806/stripe_logo?e=2147483647&v=...",
  "latestPostId": "7519107159457038336",
  "latestPostText": "Toto Wolff of the Mercedes-AMG PETRONAS Formula One Team joins John Collison to discuss today’s Formula 1, why live sports are immune to...",
  "latestPostDate": "2026-10-22T18:47:25.068Z",
  "latestPostUrl": "https://www.linkedin.com/posts/stripe_toto-wolff-of-the-mercedes-amg-petronas-formula-activity-7519107159457038336-81L5",
  "latestPostLikes": 252,
  "recentPostUrls": [
    "https://www.linkedin.com/posts/stripe_toto-wolff-of-the-mercedes-amg-petronas-formula-activity-7519107159457038336-81L5",
    "https://www.linkedin.com/posts/stripe_new-perks-for-stripe-atlas-founders-supabase-activity-7519068795169071104-fiUp"
  ],
  "city": "South San Francisco",
  "region": "California",
  "country": "US",
  "postalCode": "94080",
  "street": "354 Oyster Point Blvd",
  "dataSource": "linkedin-public-page",
  "searchInput": "Stripe",
  "record_id": "linkedin:Stripe",
  "change_type": "new",
  "why_it_matters": "A tracked item changed."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/linkedin-company-scraper").call(run_input={
    "companies": [
        "Stripe",
        "Notion"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~linkedin-company-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"companies": ["Stripe", "Notion"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/linkedin-company-scraper` as a tool.

Full documentation, pricing and the latest changes: [LinkedIn Company Info Scraper - Employee Count, Size, HQ](https://apify.com/om_kh/linkedin-company-scraper).

---
title: "Glassdoor Reviews Scraper - Ratings, Pros, Cons, Job Title"
description: "Bulk-download Glassdoor employee reviews for any company: overall rating, every sub-rating, pros, cons, advice, job title, location, employment status, helpful votes and review link. Paste the reviews URL for the cheapest source. No login. Our fee $4.50 per 1,000 reviews + supplier."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Glassdoor Reviews Scraper - Ratings, Pros, Cons, Job Title

Bulk-download Glassdoor employee reviews for any company: overall rating, every sub-rating, pros, cons, advice, job title, location, employment status, helpful votes and review link. Paste the reviews URL for the cheapest source. No login. Our fee $4.50 per 1,000 reviews + supplier.

**Run it on Apify:** [https://apify.com/om_kh/glassdoor-reviews-scraper](https://apify.com/om_kh/glassdoor-reviews-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A company's Glassdoor reviews link (the cheapest way) or its name |
| **We do** | Read the company's employee reviews |
| **You get** | One row per review: overall rating and every sub-rating, pros, cons, advice, job title, location, current or former employee, helpful votes and link, plus every field the supplier returns (`source_data`) |
| **It costs** | $4.50 per 1,000 reviews, no start fee (lowered on 21 November 2026 from $20). Optional scheduled monitoring: +$0.005 per check (one-off runs never pay it). Apify also bills the supplier Actor `getdataforme/glassdoor-reviews-scraper` that this robot runs for you, at its own price (about $9 per 1,000 reviews). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Glassdoor |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `companies` | array | Paste the company's Glassdoor reviews URL (e.g. https://www.glassdoor.com/Reviews/Google-Reviews-E9079.htm): this uses a source that costs about $0.05 per 1,000 reviews. |
| `currentReviews` | array | Skip the chained fetch and pass review data directly (no upstream call, no fetch fee). |
| `previousReviews` | array | Prior-run reviews; used to compute the delta when not in persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Glassdoor reviews actor", "authorization"`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |

## Example output

A row as shown in the Actor's README:

```json
{
  "review_id": "104025813",
  "subject_id": "https://www.glassdoor.com/Reviews/Nucor-Reviews-E489.htm",
  "rating": 5,
  "text": "Great work-life balance with excellent perks | Great worklife balance, bonus, gym, nurses station | There are none that I can think of",
  "published_at": "2026-05-19T05:42:21.183",
  "reviewId": 104025813,
  "url": "https://www.glassdoor.com/Reviews/Employee-Review-Nucor-RVW104025813.htm",
  "postedAt": "2026-05-19T05:42:21.183",
  "content_summary": "Great work-life balance with excellent perks",
  "content_pros": "Great worklife balance, bonus, gym, nurses station",
  "content_cons": "There are none that I can think of",
  "content_languageId": "eng",
  "ratings_overall": 5,
  "ratings_workLifeBalance": 5,
  "ratings_cultureAndValues": 5,
  "ratings_seniorLeadership": 4,
  "ratings_compensationAndBenefits": 5,
  "ratings_careerOpportunities": 5,
  "ratings_diversityAndInclusion": 3,
  "ratings_ceo": "APPROVE",
  "ratings_outlook": "POSITIVE",
  "ratings_recommendation": "POSITIVE",
  "employment_isCurrentJob": false,
  "employment_status": "REGULAR",
  "employment_employmentLength": 20,
  "employment_jobEndingYear": 2025,
  "employment_jobTitle_id": 1083,
  "employment_jobTitle_text": "Contract Specialist",
  "employment_location_id": 1145705,
  "employment_location_name": "Cincinnati, OH",
  "employment_location_type": "CITY",
  "engagement_helpful": 0,
  "engagement_unhelpful": 0,
  "engagement_featured": false,
  "employer_id": 489,
  "employer_shortName": "Nucor",
  "employer_name": "Nucor Corporation",
  "employer_logoUrl": "https://media.glassdoor.com/sql/489/nucor-squareLogo-1645798378058.png",
  "employer_hasResponse": false,
  "meta_isLegal": true,
  "meta_isCovid19": false,
  "meta_isLanguageMismatch": false,
  "meta_reviewDetailUrl": "/Reviews/Employee-Review--RVW104025813.htm",
  "meta_topLevelDomainId": 1,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/glassdoor-reviews-scraper").call(run_input={
    "companies": [
        "https://www.glassdoor.com/Reviews/Google-Reviews-E9079.htm",
        "https://www.glassdoor.com/Reviews/Nucor-Reviews-E489.htm"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~glassdoor-reviews-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"companies": ["https://www.glassdoor.com/Reviews/Google-Reviews-E9079.htm", "https://www.glassdoor.com/Reviews/Nucor-Reviews-E489.htm"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/glassdoor-reviews-scraper` as a tool.

Full documentation, pricing and the latest changes: [Glassdoor Reviews Scraper - Ratings, Pros, Cons, Job Title](https://apify.com/om_kh/glassdoor-reviews-scraper).

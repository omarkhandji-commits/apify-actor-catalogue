---
title: "Indeed Jobs Scraper API - Descriptions, Post Dates"
description: "Indeed jobs scraper API: job listings for any title, keyword or location: job title, full description, posting date, urgent-hire and high-volume flags and the job URL. Export to JSON, CSV or Excel, or call it as an API. No login needed. For recruiting and hiring signals. $0.30 per 1,000 jobs."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Indeed Jobs Scraper API - Descriptions, Post Dates

Indeed jobs scraper API: job listings for any title, keyword or location: job title, full description, posting date, urgent-hire and high-volume flags and the job URL. Export to JSON, CSV or Excel, or call it as an API. No login needed. For recruiting and hiring signals. $0.30 per 1,000 jobs.

**Run it on Apify:** [https://apify.com/om_kh/indeed-jobs-scraper](https://apify.com/om_kh/indeed-jobs-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A job title or keyword and a location |
| **We do** | Search Indeed and read each listing |
| **You get** | One row per job: title, full description, posting date, urgent-hire and high-volume flags, and the link, plus every field the supplier returns (`source_data`) |
| **It costs** | **$0.30 per 1,000 jobs** + $0.001 per run. Optional scheduled monitoring: +$0.05 per check (one-off runs never pay it). Apify also bills the supplier Actor `valig/indeed-jobs-scraper` that this robot runs for you, at its own price (about $0.10 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Indeed or apply to jobs |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `jobQueries` | array | Job titles, roles, or company names to monitor on Indeed. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained upstream actor", "authorization": "public`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "https://www.indeed.com/viewjob?jk=17c64b92dcd11d37",
  "query_id": "software engineer",
  "title": "Embedded Software Engineer",
  "url": "https://www.indeed.com/viewjob?jk=17c64b92dcd11d37",
  "text": "Company Description\n\nAt Bosch Mobility Aftermarket, we believe in creating a work culture that embodies our core values of grow, enjoy, a...",
  "key": "17c64b92dcd11d37",
  "jobUrl": "https://jobs.smartrecruiters.com/BoschGroup/744000152270708-embedded-software-engineer",
  "refNum": "0e04366d-bfeb-4e97-9acb-fa37b6cf923d",
  "datePublished": "2026-09-28T20:42:47.755Z",
  "dateOnIndeed": "2026-09-17T18:55:31.693Z",
  "expired": false,
  "isPlacement": false,
  "isUrgentHire": false,
  "isHighVolumeHiring": false,
  "language": "en",
  "location_countryName": "United States",
  "location_countryCode": "US",
  "location_admin1Code": "MN",
  "location_admin2Code": "147",
  "location_city": "Owatonna",
  "location_postalCode": "55060",
  "location_streetAddress": "655 Eisenhower Drive NW",
  "location_latitude": 44.09325,
  "location_longitude": -93.241135,
  "employer_name": "Bosch",
  "employer_companyPageUrl": "https://www.indeed.com/cmp/Bosch",
  "employer_address": "Farmington Hills, MI",
  "employer_employeesCount": "10,000+",
  "employer_revenue": "more than $10B (USD)",
  "employer_ceoName": "Stefan Hartung",
  "employer_ceoPhotoUrl": "https://d2q79iu7y748jz.cloudfront.net/s/_ceophoto/512x512/aa2f076d5fa6b629660bd42e7a84ec82",
  "employer_corporateWebsite": "http://www.bosch.us",
  "employer_logoUrl": "https://d2q79iu7y748jz.cloudfront.net/s/_squarelogo/256x256/b4da1fd6d0fcd4336db4bf09d51ba040",
  "employer_headerImageUrl": "https://d2q79iu7y748jz.cloudfront.net/s/_headerimage/1960x400/5a0f409b68a1234402f2c3e3d7a35355",
  "employer_ratingsCount": 7520,
  "employer_ratingsValue": 4,
  "attributes_list": [
    "Inter-Integrated Circuit (I2C) protocol",
    "Controller area network (CAN) bus"
  ],
  "employerAttributes_list": [
    "Full-time"
  ],
  "jobTypes_list": [
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/indeed-jobs-scraper").call(run_input={
    "jobQueries": [
        "software engineer",
        "account executive"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~indeed-jobs-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"jobQueries": ["software engineer", "account executive"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/indeed-jobs-scraper` as a tool.

Full documentation, pricing and the latest changes: [Indeed Jobs Scraper API - Descriptions, Post Dates](https://apify.com/om_kh/indeed-jobs-scraper).

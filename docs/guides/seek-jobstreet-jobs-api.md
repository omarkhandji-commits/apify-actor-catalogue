---
title: "SEEK and JobStreet Jobs API — Australia, NZ and South-East Asia"
description: "Get job listings from SEEK (AU, NZ), JobStreet (MY, SG, ID, PH) and JobsDB (HK, TH) as JSON with parsed salary, company and full description."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# SEEK and JobStreet Jobs API — Australia, NZ and South-East Asia

## How do I get SEEK or JobStreet job listings with an API?

Use the **SEEK & JobStreet Jobs Scraper**. Pick countries (AU, NZ, MY, SG, ID, PH, HK, TH), add keywords and optional filters (location, posted within N days, work type). It returns one row per job with title, company, location, salary parsed into min / max / period, work type, category and posting date; optionally the full description, salary currency and the company profile (size, industry, website, rating). $1 per 1,000 jobs.

**Try it:** [SEEK & JobStreet Jobs Scraper on Apify](https://apify.com/om_kh/seek-jobstreet-jobs-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [SEEK & JobStreet Jobs Scraper](https://apify.com/om_kh/seek-jobstreet-jobs-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "searchTerms": [
    "data analyst"
  ],
  "countries": [
    "AU",
    "SG",
    "MY"
  ],
  "postedWithinDays": 7,
  "includeDetails": true
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/seek-jobstreet-jobs-scraper").call(run_input={
    "searchTerms": [
        "data analyst"
    ],
    "countries": [
        "AU",
        "SG",
        "MY"
    ],
    "postedWithinDays": 7,
    "includeDetails": True
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~seek-jobstreet-jobs-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["data analyst"], "countries": ["AU", "SG", "MY"], "postedWithinDays": 7, "includeDetails": true}'
```

## What you get

- `title`
- `company`
- `location`
- `country`
- `salary`
- `salaryMin`
- `salaryMax`
- `salaryPeriod`
- `salaryCurrency`
- `workType`
- `classification`
- `postedAt`
- `description`
- `companySize`
- `companyIndustry`
- `companyRating`
- `url`

## Price

$0.001 per job, +$0.001 per job with full details, no start fee. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- Salary benchmarks across Australia and South-East Asia
- Recruitment agency job feeds
- Job boards and aggregators
- Hiring signals for B2B sales

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/seek-jobstreet-jobs-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Which sites are covered?**  
seek.com.au, seek.co.nz, JobStreet Malaysia, Singapore, Indonesia, Philippines, JobsDB Hong Kong and Thailand.

**Can I get only new jobs?**  
Yes, turn on monitoring and schedule the Actor.

## Related

- [ATS Jobs API - Greenhouse, Lever, Ashby, Workday Jobs](https://apify.com/om_kh/ats-jobs-api)
- [Indeed Jobs Scraper - Listings, Companies, Salary Data](https://apify.com/om_kh/indeed-jobs-scraper)
- [Hiring Signals API - Companies Hiring Now by Role](https://apify.com/om_kh/company-hiring-signals)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I get SEEK or JobStreet job listings with an API?", "acceptedAnswer": {"@type": "Answer", "text": "Use the SEEK & JobStreet Jobs Scraper. Pick countries (AU, NZ, MY, SG, ID, PH, HK, TH), add keywords and optional filters (location, posted within N days, work type). It returns one row per job with title, company, location, salary parsed into min / max / period, work type, category and posting date; optionally the full description, salary currency and the company profile (size, industry, website, rating). $1 per 1,000 jobs."}}, {"@type": "Question", "name": "Which sites are covered?", "acceptedAnswer": {"@type": "Answer", "text": "seek.com.au, seek.co.nz, JobStreet Malaysia, Singapore, Indonesia, Philippines, JobsDB Hong Kong and Thailand."}}, {"@type": "Question", "name": "Can I get only new jobs?", "acceptedAnswer": {"@type": "Answer", "text": "Yes, turn on monitoring and schedule the Actor."}}]}
</script>

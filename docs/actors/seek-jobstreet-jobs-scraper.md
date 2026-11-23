---
title: "JobStreet & SEEK Jobs Scraper - Salary, Company, Asia AU"
description: "Job listings from SEEK (Australia, New Zealand), JobStreet (MY, SG, ID, PH) and JobsDB (HK, TH): title, company, parsed salary, work type, full description, company details, recruiter e-mail and phone. Salary, remote and radius filters. $1 per 1,000 jobs, + $0.001 per run from Dec 1, 2026."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# JobStreet & SEEK Jobs Scraper - Salary, Company, Asia AU

Job listings from SEEK (Australia, New Zealand), JobStreet (MY, SG, ID, PH) and JobsDB (HK, TH): title, company, parsed salary, work type, full description, company details, recruiter e-mail and phone. Salary, remote and radius filters. $1 per 1,000 jobs, + $0.001 per run from Dec 1, 2026.

**Run it on Apify:** [https://apify.com/om_kh/seek-jobstreet-jobs-scraper](https://apify.com/om_kh/seek-jobstreet-jobs-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords and countries (SEEK Australia and New Zealand, JobStreet Malaysia, Singapore, Indonesia and Philippines, JobsDB Hong Kong and Thailand) |
| **We do** | Search those 8 job boards |
| **You get** | One row per job: title, company, location, salary as min / max / period, work type, category and date; option: full description, company size, industry, website and rating |
| **It costs** | $1 per 1,000 jobs, + $1 per 1,000 for full details, + $0.001 per run from Dec 1, 2026 (no start fee before). 5,000 jobs with details = **$10**. The first 20 jobs of every run are free. No supplier fee |
| **It does not** | Sign in or apply to jobs |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchTerms` | array | Job keywords, one per line (up to 20), e.g. 'data analyst', 'nurse'. Default: `["data analyst"]`. |
| `startUrls` | array | Paste search links from seek.com.au, seek.co.nz, JobStreet or JobsDB: keywords, location and every filter of the link are used. |
| `countries` | array | AU = SEEK Australia, NZ = SEEK New Zealand, MY/SG/ID/PH = JobStreet, HK/TH = JobsDB. Default: `["AU"]`. |
| `location` | string | Optional city or region as typed on the site, e.g. 'Sydney NSW', 'Melbourne', 'Kuala Lumpur'. |
| `radiusKm` | integer | Search within this distance of the location. |
| `maxJobs` | integer | 1 to 5,000. Default: `100`. |
| `postedWithinDays` | integer | Optional: only jobs listed in the last N days (e.g. 1, 3, 7, 14, 31). |
| `workType` | string | Optional: full time, part time, contract/temp or casual. Default: `"any"`. |
| `workTypes` | array | Pick several work types at once. |
| `workArrangements` | array | Keep only on-site, hybrid or remote jobs. |
| `salaryMin` | integer | In the site's currency, for the salary type below. |
| `salaryMax` | integer | In the site's currency, for the salary type below. |
| `salaryType` | string | How the salary range above is counted. Default: `"annual"`. |
| `classification` | string | SEEK's number for a job family, as in a search link (classification=6281 is Information & Communication Technology). |
| `subClassification` | string | SEEK's number for a speciality, as in a search link (subclassification=6287). |
| `titleKeywords` | array | Keep jobs whose title contains at least one of these words. |
| `excludeTitleKeywords` | array | Drop jobs whose title contains one of these words. |
| `postedAfter` | string | YYYY-MM-DD. |
| `postedBefore` | string | YYYY-MM-DD. |
| `sortBy` | string | Newest first (default) or most relevant. Default: `"newest"`. |
| `includeDetails` | boolean | Adds the full description (text and HTML), salary with currency, expiry date, verified advertiser, company size/industry/website/rating, and emails or phones printed in the ad. +$0.001 per job. Default: `false`. |
| `requireContact` | string | Keep only jobs whose ad shows a recruiter's e-mail or phone. Default: `"off"`. |
| `minApplicants` | integer | Keep only jobs with at least this many applicants. |
| `maxApplicants` | integer | Keep only jobs with at most this many applicants, for example 20 to find jobs with little competition. |
| `monitorEnabled` | boolean | Schedule the Actor and get only jobs not seen in previous runs. Default: `false`. |
| `monitorId` | string | Optional name to keep separate monitoring baselines. |
| `discordWebhookUrl` | string | A Discord webhook link: a short summary of the jobs of each run is posted there. |
| `telegramToken` | string | Token of your own Telegram bot, to receive the same summary on Telegram. |
| `telegramChatId` | string | The chat or channel the bot writes to. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "jobId": "95469114",
  "title": "Project Coordinator",
  "company": "Curtin University",
  "advertiserId": "559343",
  "location": "Bentley, Perth WA",
  "country": "AU",
  "site": "SEEK Australia",
  "salary": "$109,277 - $117,331 (G07) pro rata + 17% super",
  "salaryMin": 109277,
  "salaryMax": 117331,
  "workType": "Part time",
  "workArrangement": "On-site",
  "classification": "Education & Training",
  "subClassification": "Research & Fellowships",
  "teaser": "Join Curtin to coordinate impactful research into drug use among young Australians and help shape practical harm reduction responses",
  "bulletPoints": [
    "Part time (0.8FTE), fixed term until 28 September 2029| based at Technology Park",
    "Competitive remuneration + 17% super contributions"
  ],
  "postedAt": "2026-10-23T13:21:40Z",
  "isFeatured": false,
  "companyLogo": "https://bx-branding-gateway.cloud.seek.com.au/1f323921-5b02-cf57-395b-01c4d44da1a8.1/jdpLogo",
  "url": "https://www.seek.com.au/job/95469114",
  "searchQuery": "data analyst",
  "totalMatches": 3061
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/seek-jobstreet-jobs-scraper").call(run_input={
    "searchTerms": [
        "data analyst"
    ],
    "countries": [
        "AU",
        "SG"
    ],
    "maxJobs": 50
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~seek-jobstreet-jobs-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["data analyst"], "countries": ["AU", "SG"], "maxJobs": 50}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/seek-jobstreet-jobs-scraper` as a tool.

Full documentation, pricing and the latest changes: [JobStreet & SEEK Jobs Scraper - Salary, Company, Asia AU](https://apify.com/om_kh/seek-jobstreet-jobs-scraper).

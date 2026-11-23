---
title: "LinkedIn Job Search Scraper - Salaries, Descriptions"
description: "LinkedIn job search scraper by keywords and location, with LinkedIn's filters (date, remote, job type, experience, Easy Apply). Up to 1,000 jobs per search, full description, seniority, applicants, apply type, recruiter, and the salary from the posting as numbers. No login. $0.35 per 1,000 jobs."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# LinkedIn Job Search Scraper - Salaries, Descriptions

LinkedIn job search scraper by keywords and location, with LinkedIn's filters (date, remote, job type, experience, Easy Apply). Up to 1,000 jobs per search, full description, seniority, applicants, apply type, recruiter, and the salary from the posting as numbers. No login. $0.35 per 1,000 jobs.

**Run it on Apify:** [https://apify.com/om_kh/linkedin-jobs-scraper](https://apify.com/om_kh/linkedin-jobs-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords and a location, or your own LinkedIn job search links, with LinkedIn's filters |
| **We do** | Search LinkedIn's public job pages and open every job |
| **You get** | One row per job (up to 1,000 per search): title, company, location, date, applicants, full description, seniority, employment type, industries, apply type, recruiter when shown, and the salary turned into numbers |
| **It costs** | $0.35 per 1,000 jobs, no start fee, no monitoring fee. The first 10 jobs of every run are free. Errors are never charged. No supplier fee |
| **It does not** | Sign in to LinkedIn, or give the external apply link (LinkedIn shows it only to signed-in members) |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | One search per line, e.g. 'data engineer'. Default: `["data engineer"]`. |
| `location` | string | City, region or country as you would type it on LinkedIn, e.g. 'United States', 'London', 'Remote'. Default: `"United States"`. |
| `locations` | array | Optional: several places. |
| `geoId` | string | Optional LinkedIn place number for exact targeting (the geoId= value in a LinkedIn search link, e.g. 103644278 for United States). |
| `splitByLocation` | boolean | Searches each big city of the country below, one by one, to go past LinkedIn's 1,000 jobs per search. Default: `false`. |
| `splitCountry` | string | Country whose big cities are searched when 'Split search by big city' is on. Default: `"US"`. |
| `searchUrls` | array | Links copied from linkedin.com/jobs/search with your filters already set. |
| `datePosted` | string | LinkedIn's date filter. Default: `"any"`. |
| `workplace` | array | Leave empty for all. |
| `jobTypes` | array | Leave empty for all. |
| `experienceLevels` | array | Leave empty for all. |
| `easyApply` | boolean | Only jobs with LinkedIn Easy Apply. Default: `false`. |
| `under10Applicants` | boolean | Only jobs with fewer than 10 applicants. Default: `false`. |
| `companyIds` | array | Optional LinkedIn company IDs (the f_C value of a company's job search link). |
| `distanceMiles` | integer | Radius around the location: 5, 10, 25, 50 or 100. |
| `sortBy` | string | Order of the results. Default: `"recent"`. |
| `maxJobsPerSearch` | integer | 1 to 1,000 (LinkedIn's limit per search). Default: `100`. |
| `limitPerSource` | integer | Alias of 'Max jobs per search', for people coming from other LinkedIn scrapers. |
| `includeDetails` | boolean | Description, seniority, employment type, job function, industries, applicants and the pay written in the posting. Default: `true`. |
| `includeCompany` | boolean | Adds the company description, number of employees, website, size, industry, headquarters and followers (one page per company). Default: `true`. |
| `onlyNewJobs` | boolean | Return only jobs this monitor has not returned before. Default: `false`. |
| `monitorEnabled` | boolean | Same as 'Only new jobs'; kept for existing tasks. Default: `false`. |
| `monitorId` | string | Optional name to keep separate 'only new' histories. |
| `maxTotalChargeUsd` | number | The run stops charging at this amount. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "job",
  "jobId": "4473512745",
  "title": "Senior Data Engineer",
  "companyName": "Faegre Drinker",
  "companyUrl": "https://www.linkedin.com/company/faegredrinker",
  "companyLogo": "https://media.licdn.com/dms/image/v2/D560BAQF36YOXj5UrZA/company-logo_100_100/B56ZfMszx0HEAQ-/0/1751485988648?e=2147483647&v=beta&t=UjiTM...",
  "location": "Minneapolis, MN",
  "postedDate": "2026-10-21",
  "postedAgo": "2 days ago",
  "benefits": "Actively Hiring",
  "jobUrl": "https://www.linkedin.com/jobs/view/4473512745",
  "searchQuery": "data engineer | United States",
  "applicants": "99 applicants",
  "applicantsCount": 99,
  "description": "Faegre Drinker is a firm designed for clients and designed for you. We understand that our people are critical to our success and we are...",
  "descriptionHtml": "<strong><em>Faegre Drinker is a firm designed for clients and designed for you. We understand that our people are critical to our success...",
  "seniorityLevel": "Not Applicable",
  "employmentType": "Full-time",
  "industries": "Law Practice",
  "applyType": "EXTERNAL",
  "salaryText": "$139,300 - $159,200",
  "salaryMin": 139300,
  "salaryMax": 159200,
  "salaryPeriod": "year",
  "salarySource": "posting_text"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/linkedin-jobs-scraper").call(run_input={
    "keywords": [
        "data engineer"
    ],
    "location": "United States",
    "maxJobsPerSearch": 10
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~linkedin-jobs-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["data engineer"], "location": "United States", "maxJobsPerSearch": 10}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/linkedin-jobs-scraper` as a tool.

Full documentation, pricing and the latest changes: [LinkedIn Job Search Scraper - Salaries, Descriptions](https://apify.com/om_kh/linkedin-jobs-scraper).

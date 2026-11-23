---
title: "Google Jobs Scraper - Salary, Apply Links, Descriptions"
description: "Scrape Google Jobs for any keyword and city, or paste a Google Jobs link: salary as numbers and yearly pay, remote/hybrid/on-site, contract type, city and country, benefits, posted date, description and every apply link. Only-new-jobs mode. $4 per 1,000 jobs, less on paid plans."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Google Jobs Scraper - Salary, Apply Links, Descriptions

Scrape Google Jobs for any keyword and city, or paste a Google Jobs link: salary as numbers and yearly pay, remote/hybrid/on-site, contract type, city and country, benefits, posted date, description and every apply link. Only-new-jobs mode. $4 per 1,000 jobs, less on paid plans.

**Run it on Apify:** [https://apify.com/om_kh/google-jobs-scraper](https://apify.com/om_kh/google-jobs-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A job title or keyword and a city, for example `software engineer` in `New York, NY` |
| **We do** | Search Google Jobs, which gathers LinkedIn, Indeed, Glassdoor, ZipRecruiter and company sites, and open every posting |
| **You get** | One row per job: title, company, location, posted date, job type, salary split into min / max / period when published, description and every "Apply on" link. In our test: salary as numbers on 16 of 30 jobs, posted date on 23 of 30 |
| **It costs** | $4 per 1,000 jobs on the free plan, $3.40 to $2.20 on paid plans, no start fee. Free plan: 5 jobs free on every run. A search Google cannot answer costs nothing |
| **It does not** | Return more than a few hundred jobs per search (split by city for more), work in every country (see the country list under Tips and limits), or invent a salary the employer did not publish |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `queries` | array | Job titles or keywords: 'data analyst', 'registered nurse', 'python developer remote' (up to 50 with locations). Default: `["data analyst"]`. |
| `startUrls` | array | Paste Google or Google Jobs search links (the address bar after searching 'nurse jobs Chicago' on Google). |
| `locations` | array | Cities, states or countries: 'Chicago', 'Texas', 'London'. Default: `["Chicago"]`. |
| `radiusKm` | integer | Asks Google to search within this distance of each location, 1 to 300 km. |
| `strictLocation` | boolean | Google sometimes adds jobs from other places. Default: `true`. |
| `maxJobsPerSearch` | integer | 1 to 140. Default: `50`. |
| `postedWithin` | string | Only recent postings. Default: `"any"`. |
| `scheduleType` | string | Keep only this job type. Default: `"any"`. |
| `onlyWithSalary` | boolean | Keep only postings that show a salary. Default: `false`. |
| `workArrangements` | array | Keep only these work arrangements. |
| `countries` | array | Keep only jobs in these countries: names or 2-letter codes (United States, US, Germany, DE...). |
| `excludeTitleKeywords` | array | Drop jobs whose TITLE has any of these words (e.g. senior, intern, manager), even if the description mentions them. |
| `excludeCompanies` | array | Drop jobs from these companies (part of the name is enough). |
| `excludeAgencies` | boolean | Drop jobs posted by staffing or recruitment agencies for a client. Default: `false`. |
| `onlyNewJobs` | boolean | Deliver only the jobs this same search has not delivered before (remembered in your own Apify account). Default: `false`. |
| `memoryName` | string | Give the 'only new jobs' memory a name to share it between tasks or keep it when you change the search. |
| `includeDescription` | boolean | Turn off for lighter rows. Default: `true`. |
| `country` | string | Two-letter country code of the Google Jobs market: us, gb, ca, au, in, de, fr... Default: `"us"`. |
| `language` | string | Interface language, e.g. en. Default: `"en"`. |
| `googleDomain` | string | Which Google site to search: google.com, google.co.uk, google.ca, google.de, google.fr, google.com.au.. Default: `"google.com"`. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "title": "Data Business Systems Analyst",
  "companyName": "Kemper",
  "jobId": "\nO7fIRI6fLFuHPOR7AAAAAA==\nXBRX1njWoDQAAAAAAAAAAA\nyrcpCkrlsxkAAAAAAAAAAA\nhJp4MkyBDi4AAAAAAAAAAA\n34ii14s47VYAAAAAAAAAAA\nfzQArKreRggAAAAAAAA...",
  "applyLinks": [
    {
      "source": "builtinchicago.org",
      "url": "https://www.builtinchicago.org/job/data-business-systems-analyst/11781085"
    },
    {
      "source": "indeed.com",
      "url": "https://www.indeed.com/viewjob?jk=4ce799da94c0f717"
    }
  ],
  "location": "Chicago, IL",
  "via": "Built In Chicago",
  "postedAgo": "4 days ago",
  "postedAt": "2026-10-19",
  "scheduleType": "Full-time",
  "salary": "89K–148K a year",
  "salaryMin": 89000,
  "salaryMax": 148000,
  "salaryPeriod": "year",
  "salarySource": "google",
  "isRemote": false,
  "benefits": [
    "Paid time off",
    "Dental insurance"
  ],
  "extensions": [
    "4 days ago",
    "89K–148K a year"
  ],
  "qualifications": [
    "The ideal candidate possesses strong expertise in data analysis, data warehousing, systems analysis, business process validation, testing...",
    "Bachelor's degree in Information Systems, Computer Science, Data Analytics, Business Analytics, or a related field; equivalent work exper..."
  ],
  "responsibilities": [
    "Kemper is seeking a highly analytical and detail-oriented Senior Data Business Systems Analyst to provide independent validation and qual...",
    "This role is responsible for ensuring the accuracy, completeness, reliability, and regulatory compliance of critical business data and en..."
  ],
  "benefitsHighlights": [
    "The range for this position is $89,000 to $148,100",
    "When determining candidate offers, we consider experience, skills, education, certifications, and geographic location among other factors..."
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-jobs-scraper").call(run_input={
    "queries": [
        "data analyst"
    ],
    "locations": [
        "Chicago"
    ],
    "maxJobsPerSearch": 20
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-jobs-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"queries": ["data analyst"], "locations": ["Chicago"], "maxJobsPerSearch": 20}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-jobs-scraper` as a tool.

Full documentation, pricing and the latest changes: [Google Jobs Scraper - Salary, Apply Links, Descriptions](https://apify.com/om_kh/google-jobs-scraper).

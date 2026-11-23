---
title: "Ashby Jobs Scraper API - Title, Location, Department"
description: "Ashby jobs scraper API: every open job from any jobs.ashbyhq.com board as clean data, with title, location, department, date, full description, salary, skills, apply link, seniority and remote flags. $1.50 per 1,000 jobs, first 3 per run free. Filters run before billing. No login."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Ashby Jobs Scraper API - Title, Location, Department

Ashby jobs scraper API: every open job from any jobs.ashbyhq.com board as clean data, with title, location, department, date, full description, salary, skills, apply link, seniority and remote flags. $1.50 per 1,000 jobs, first 3 per run free. Filters run before billing. No login.

**Run it on Apify:** [https://apify.com/om_kh/ashby-jobs-api](https://apify.com/om_kh/ashby-jobs-api) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Ashby company handles or board links (`ramp`), up to 100 per run, with optional keyword, location and remote filters |
| **We do** | Read each company's official public Ashby job feed; filters run before billing |
| **You get** | One row per open job: title, location, department, posted date, apply link and description, plus job function, seniority and remote flags |
| **It costs** | $1.50 per 1,000 jobs + $0.001 per run. A company with 35 open roles costs about **$0.05**. The first 3 jobs of every run are free. No supplier fee |
| **It does not** | Scrape LinkedIn, Indeed or job boards, or read pages behind a login |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `ashbyCompanies` | array | Ashby company handles - the  in jobs.ashbyhq.com/. Default: `["ramp", "linear"]`. |
| `keywords` | array | Keep only jobs whose title, department, company or location contains one of these words. |
| `excludeKeywords` | array | Drop jobs matching any of these words, e.g. intern, senior, sales. |
| `locations` | array | Keep only jobs whose location contains one of these, e.g. Berlin, United Kingdom. |
| `remoteOnly` | boolean | Keep only roles whose location says remote, anywhere or distributed. Default: `false`. |
| `postedAfter` | string | Keep only jobs posted on or after this date (YYYY-MM-DD). |
| `includeDescription` | boolean | Add the full job description (plain text), salary, contract type, workplace type and apply link when the system publishes them, plus facts read from the text: years of experience, skills, visa sponsorship, degree. Default: `true`. |
| `maxTotalChargeUsd` | number | Optional extra ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "source_url": "https://jobs.ashbyhq.com/ramp/b9568fb8-a47e-4738-87fb-a6d88c3a505f",
  "title": "Account Manager | Commercial",
  "company": "ramp",
  "location": "New York, NY (HQ)",
  "department": "Sales",
  "posted_at": "2025-12-10T14:44:21.253+00:00",
  "source": "ashby",
  "salary": "$160K – $230K • Offers Equity • Offers Commission • Multiple Ranges",
  "job_id": "b9568fb8-a47e-4738-87fb-a6d88c3a505f",
  "description": "ABOUT RAMP\n\nRamp is building the smart infrastructure for finance teams, embedded in the transaction flow of every dollar a business spen...",
  "employment_type": "FullTime",
  "workplace_type": "remote",
  "apply_url": "https://jobs.ashbyhq.com/ramp/b9568fb8-a47e-4738-87fb-a6d88c3a505f/application",
  "handle": "(hidden here)",
  "ats": "ashby",
  "function": "Sales",
  "seniority": "Manager",
  "is_remote": false,
  "posted_within_days": 317,
  "is_recent": false,
  "experience_years": 3,
  "skills": [
    "Salesforce",
    "NetSuite"
  ],
  "education": "Bachelor",
  "salary_min": 160000,
  "salary_max": 230000,
  "salary_currency": "USD"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/ashby-jobs-api").call(run_input={
    "ashbyCompanies": [
        "ramp",
        "linear"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~ashby-jobs-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"ashbyCompanies": ["ramp", "linear"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/ashby-jobs-api` as a tool.

Full documentation, pricing and the latest changes: [Ashby Jobs Scraper API - Title, Location, Department](https://apify.com/om_kh/ashby-jobs-api).

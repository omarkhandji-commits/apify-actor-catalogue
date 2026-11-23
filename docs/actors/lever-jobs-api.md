---
title: "Lever.co Jobs API - Title, Location, Department, Salary"
description: "Lever jobs API: every open job from any jobs.lever.co board as clean data, with title, location, team, date, full description, salary, skills, apply link, seniority and remote flags. $1.50 per 1,000 jobs, first 3 per run free. Filters run before billing. No login."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Lever.co Jobs API - Title, Location, Department, Salary

Lever jobs API: every open job from any jobs.lever.co board as clean data, with title, location, team, date, full description, salary, skills, apply link, seniority and remote flags. $1.50 per 1,000 jobs, first 3 per run free. Filters run before billing. No login.

**Run it on Apify:** [https://apify.com/om_kh/lever-jobs-api](https://apify.com/om_kh/lever-jobs-api) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Lever company handles or board links (`spotify`), up to 100 per run, with optional keyword, location and remote filters |
| **We do** | Read each company's official public Lever job feed; filters run before billing |
| **You get** | One row per open job: title, location, department, posted date, apply link and description, plus job function, seniority and remote flags |
| **It costs** | $1.50 per 1,000 jobs + $0.001 per run. A company with 35 open roles costs about **$0.05**. The first 3 jobs of every run are free. No supplier fee |
| **It does not** | Scrape LinkedIn, Indeed or job boards, or read pages behind a login |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `leverCompanies` | array | Lever company handles - the  in jobs.lever.co/. Default: `["spotify", "netflix"]`. |
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
  "source_url": "https://jobs.lever.co/spotify/4310f31c-90e1-4e8d-bdcf-dce39c145b8c",
  "title": "Associate – Audiobook Licensing & Author Partnerships",
  "company": "spotify",
  "location": "New York, NY",
  "department": "Operations and Business Support",
  "posted_at": "2026-07-09T14:55:35.950000+00:00",
  "source": "lever",
  "job_id": "4310f31c-90e1-4e8d-bdcf-dce39c145b8c",
  "description": "The Audiobooks Mission is a team in the Product & Technology organisation focused on the ecosystem and strategies of Audiobooks on Spotif...",
  "employment_type": "Permanent",
  "workplace_type": "remote",
  "apply_url": "https://jobs.lever.co/spotify/4310f31c-90e1-4e8d-bdcf-dce39c145b8c/apply",
  "handle": "(hidden here)",
  "ats": "lever",
  "function": "Sales",
  "seniority": "Mid",
  "is_remote": false,
  "posted_within_days": 106,
  "is_recent": false,
  "experience_years": 3,
  "education": "Master",
  "salary_min": 74000,
  "salary_max": 106000,
  "salary_currency": "USD"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/lever-jobs-api").call(run_input={
    "leverCompanies": [
        "spotify",
        "netflix"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~lever-jobs-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"leverCompanies": ["spotify", "netflix"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/lever-jobs-api` as a tool.

Full documentation, pricing and the latest changes: [Lever.co Jobs API - Title, Location, Department, Salary](https://apify.com/om_kh/lever-jobs-api).

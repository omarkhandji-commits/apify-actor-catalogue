---
title: "Greenhouse Jobs Scraper - Title, Location, Salary API"
description: "Greenhouse jobs scraper and API: every open job from any Greenhouse board as clean data, with title, location, department, date, full description, salary, skills, apply link, seniority and remote flags. $1.50 per 1,000 jobs, first 3 per run free. Filters run before billing. No login."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Greenhouse Jobs Scraper - Title, Location, Salary API

Greenhouse jobs scraper and API: every open job from any Greenhouse board as clean data, with title, location, department, date, full description, salary, skills, apply link, seniority and remote flags. $1.50 per 1,000 jobs, first 3 per run free. Filters run before billing. No login.

**Run it on Apify:** [https://apify.com/om_kh/greenhouse-jobs-api](https://apify.com/om_kh/greenhouse-jobs-api) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Greenhouse company handles or board links (board tokens such as `figma`), up to 100 per run, with optional keyword, location and remote filters |
| **We do** | Read each company's official public Greenhouse job feed; filters run before billing |
| **You get** | One row per open job: title, location, department, posted date, apply link and description, plus job function, seniority and remote flags |
| **It costs** | $1.50 per 1,000 jobs + $0.001 per run. A company with 35 open roles costs about **$0.05**. The first 3 jobs of every run are free. No supplier fee |
| **It does not** | Scrape LinkedIn, Indeed or job boards, or read pages behind a login |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `greenhouseBoards` | array | Greenhouse board tokens - the  in boards.greenhouse.io/. Default: `["stripe", "gitlab"]`. |
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
  "source_url": "https://stripe.com/jobs/search?gh_jid=8172510",
  "title": "Abuse Investigator",
  "company": "stripe",
  "location": "Seattle, San Francisco, New York City",
  "posted_at": "2026-09-09T10:50:29-04:00",
  "source": "greenhouse",
  "job_id": "8172510",
  "description": "Who we are\nAbout Stripe\nStripe is a financial infrastructure platform for businesses. Millions of companies - from the world’s largest en...",
  "department": "8611 Security Analytics",
  "company_name": "Stripe",
  "updated_at": "2026-10-22T09:17:09-04:00",
  "apply_url": "https://stripe.com/jobs/search?gh_jid=8172510",
  "handle": "(hidden here)",
  "ats": "greenhouse",
  "function": "Other",
  "seniority": "Mid",
  "is_remote": false,
  "posted_within_days": 44,
  "is_recent": false,
  "experience_years": 10,
  "skills": [
    "Python",
    "SQL"
  ],
  "education": "Master"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/greenhouse-jobs-api").call(run_input={
    "greenhouseBoards": [
        "stripe",
        "gitlab"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~greenhouse-jobs-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"greenhouseBoards": ["stripe", "gitlab"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/greenhouse-jobs-api` as a tool.

Full documentation, pricing and the latest changes: [Greenhouse Jobs Scraper - Title, Location, Salary API](https://apify.com/om_kh/greenhouse-jobs-api).

---
title: "Workday Jobs API - Title, Location, Seniority, Remote"
description: "Workday jobs API: every open job from any myworkdayjobs.com careers site as clean data, with title, location, date, apply link, job function, seniority and remote flags. $0.10 per 1,000 jobs from Nov 24 (was $1.50), 3 free per run. Filters run before billing. No login."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Workday Jobs API - Title, Location, Seniority, Remote

Workday jobs API: every open job from any myworkdayjobs.com careers site as clean data, with title, location, date, apply link, job function, seniority and remote flags. $0.10 per 1,000 jobs from Nov 24 (was $1.50), 3 free per run. Filters run before billing. No login.

**Run it on Apify:** [https://apify.com/om_kh/workday-jobs-api](https://apify.com/om_kh/workday-jobs-api) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Workday company handles or board links (a myworkdayjobs.com careers link), up to 100 per run, with optional keyword, location and remote filters |
| **We do** | Read each company's official public Workday job feed; filters run before billing |
| **You get** | One row per open job: title, location, department, posted date, apply link and description, plus job function, seniority and remote flags |
| **It costs** | $0.10 per 1,000 jobs + $0.001 per run, from Nov 24, 2026 (was $1.50 per 1,000). A company with 35 open roles costs about **$0.004**. The first 3 jobs of every run are free. No supplier fee |
| **It does not** | Scrape LinkedIn, Indeed or job boards, or read pages behind a login |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `workdayBoards` | array | Full Workday careers URLs, e.g. https://.wd1.myworkdayjobs.com/. Default: `["https://nvidia.wd5.myworkdayjobs.com/NVIDIAExternalCareerS`. |
| `keywords` | array | Keep only jobs whose title, department, company or location contains one of these words. |
| `excludeKeywords` | array | Drop jobs matching any of these words, e.g. intern, senior, sales. |
| `locations` | array | Keep only jobs whose location contains one of these, e.g. Berlin, United Kingdom. |
| `remoteOnly` | boolean | Keep only roles whose location says remote, anywhere or distributed. Default: `false`. |
| `postedAfter` | string | Keep only jobs posted on or after this date (YYYY-MM-DD). |
| `maxTotalChargeUsd` | number | Optional extra ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "source_url": "https://nvidia.wd5.myworkdayjobs.com/NVIDIAExternalCareerSite/job/US-CA-Santa-Clara/Manager--Data-and-AI-Engineering_JR2028501",
  "title": "Manager, Data and AI Engineering",
  "company": "nvidia",
  "location": "US, CA, Santa Clara",
  "posted_at": "2026-10-23",
  "source": "workday",
  "handle": "(hidden here)",
  "ats": "workday",
  "function": "Data & AI",
  "seniority": "Manager",
  "is_remote": false,
  "posted_within_days": 0,
  "is_recent": true
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/workday-jobs-api").call(run_input={
    "workdayBoards": [
        "https://nvidia.wd5.myworkdayjobs.com/NVIDIAExternalCareerSite"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~workday-jobs-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"workdayBoards": ["https://nvidia.wd5.myworkdayjobs.com/NVIDIAExternalCareerSite"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/workday-jobs-api` as a tool.

Full documentation, pricing and the latest changes: [Workday Jobs API - Title, Location, Seniority, Remote](https://apify.com/om_kh/workday-jobs-api).

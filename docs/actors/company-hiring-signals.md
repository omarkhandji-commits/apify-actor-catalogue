---
title: "Hiring Signals API - Companies Hiring Now by Role"
description: "Hiring signals API for sales and recruiting prospecting. Give a company and get a hiring-activity score back, built from its live open roles, so you can find accounts actively hiring for a given function and use that activity as a buying-intent or prospecting signal. $0.005 per company checked."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Hiring Signals API - Companies Hiring Now by Role

Hiring signals API for sales and recruiting prospecting. Give a company and get a hiring-activity score back, built from its live open roles, so you can find accounts actively hiring for a given function and use that activity as a buying-intent or prospecting signal. $0.005 per company checked.

**Run it on Apify:** [https://apify.com/om_kh/company-hiring-signals](https://apify.com/om_kh/company-hiring-signals) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | The company websites you want to watch (`stripe.com`), up to 200 per run |
| **We do** | Read each company's own hiring page and compare it with your last run |
| **You get** | One row per company, scored 0 to 100 with the reason for every point: started hiring, first sales hire, new office, hiring faster, hiring freeze. Option: only the companies that changed |
| **It costs** | $0.005 per company checked (was $0.02 until 20 November 2026) + $0.001 per run, even when nothing changed (the check is the work). The first 5 companies of every run are free |
| **It does not** | Give the job rows themselves (that is [ATS Jobs API](https://apify.com/om_kh/ats-jobs-api)), or read companies whose hiring page is not public |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `companyDomains` | array | The companies to score. Default: `["stripe.com", "figma.com", "ramp.com", "notion.so"]`. |
| `onlyTriggers` | boolean | Return only companies with at least one change event since your last run - first sales hire, started hiring, new location, accelerating, executive hire. Default: `false`. |
| `minIntentScore` | integer | Drop companies scoring below this (0-100). Default: `0`. |
| `trackChanges` | boolean | Remember this run so the next one can report what changed. Default: `true`. |
| `trackingId` | string | Pin the history to a name of your choosing. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/company-hiring-signals").call(run_input={
    "companyDomains": [
        "stripe.com",
        "figma.com",
        "ramp.com",
        "notion.so"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~company-hiring-signals/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"companyDomains": ["stripe.com", "figma.com", "ramp.com", "notion.so"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/company-hiring-signals` as a tool.

Full documentation, pricing and the latest changes: [Hiring Signals API - Companies Hiring Now by Role](https://apify.com/om_kh/company-hiring-signals).

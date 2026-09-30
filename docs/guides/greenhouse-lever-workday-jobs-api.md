---
title: "Jobs API for Greenhouse, Lever, Ashby and Workday — One Call"
description: "Get current job listings from any company's ATS (Greenhouse, Lever, Ashby, Workday, SmartRecruiters, Personio, Rippling) as clean JSON, filtered by keyword and location."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Jobs API for Greenhouse, Lever, Ashby and Workday — One Call

## How do I get all open jobs from a company's Greenhouse, Lever or Workday career page?

Use the **ATS Jobs API** Actor. Give it company domains (it finds the ATS for you) or board names per provider. It reads the ATS's official public job-board endpoints and returns one clean row per job: title, company, location, department, salary when published, posting date and link. Filter by keywords, locations, remote-only or posting date. $1.50 per 1,000 jobs.

**Try it:** [ATS Jobs API on Apify](https://apify.com/om_kh/ats-jobs-api) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [ATS Jobs API](https://apify.com/om_kh/ats-jobs-api) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "companyDomains": [
    "stripe.com",
    "figma.com"
  ],
  "keywords": [
    "engineer"
  ],
  "remoteOnly": false
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/ats-jobs-api").call(run_input={
    "companyDomains": [
        "stripe.com",
        "figma.com"
    ],
    "keywords": [
        "engineer"
    ],
    "remoteOnly": False
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~ats-jobs-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"companyDomains": ["stripe.com", "figma.com"], "keywords": ["engineer"], "remoteOnly": false}'
```

## What you get

- `title`
- `company`
- `location`
- `department`
- `salary`
- `posted_at`
- `source` (greenhouse / lever / ashby / workday ...)
- `source_url`

## Price

$0.0015 per job listing. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- Job boards and aggregators
- Recruiting and sourcing tools
- Hiring signals for B2B sales (who is hiring which roles)
- Labour-market research

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/ats-jobs-api` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Do I need to know which ATS a company uses?**  
No, pass the company domain and the Actor detects it.

**Is this LinkedIn or Indeed?**  
No, it reads the company's own career board, which is usually fresher and complete. For LinkedIn and Indeed there are separate Actors.

**Can I get only new jobs?**  
Yes, turn on monitoring to receive only jobs that appeared since the last run.

## Related

- [Company Careers Page Scraper - Jobs from Any Career Site](https://apify.com/om_kh/careers-page-scraper)
- [Hiring Signals API - Companies Hiring Now by Role](https://apify.com/om_kh/company-hiring-signals)
- [Greenhouse Job Listings API - Title, Location, Salary](https://apify.com/om_kh/greenhouse-jobs-api)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I get all open jobs from a company's Greenhouse, Lever or Workday career page?", "acceptedAnswer": {"@type": "Answer", "text": "Use the ATS Jobs API Actor. Give it company domains (it finds the ATS for you) or board names per provider. It reads the ATS's official public job-board endpoints and returns one clean row per job: title, company, location, department, salary when published, posting date and link. Filter by keywords, locations, remote-only or posting date. $1.50 per 1,000 jobs."}}, {"@type": "Question", "name": "Do I need to know which ATS a company uses?", "acceptedAnswer": {"@type": "Answer", "text": "No, pass the company domain and the Actor detects it."}}, {"@type": "Question", "name": "Is this LinkedIn or Indeed?", "acceptedAnswer": {"@type": "Answer", "text": "No, it reads the company's own career board, which is usually fresher and complete. For LinkedIn and Indeed there are separate Actors."}}, {"@type": "Question", "name": "Can I get only new jobs?", "acceptedAnswer": {"@type": "Answer", "text": "Yes, turn on monitoring to receive only jobs that appeared since the last run."}}]}
</script>

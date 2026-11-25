---
title: "Google Jobs API — Salary, Apply Links and Job Postings as JSON"
description: "Get Google Jobs results by API for any keyword and city: salary as numbers, posted date, remote or on-site, company, description and every apply link, as JSON or CSV."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Google Jobs API — Salary, Apply Links and Job Postings as JSON

## Is there a Google Jobs API?

Google does not sell a public API that returns the Google Jobs search results, so use the **Google Jobs API** robot on Apify. Give it a job title or keyword and a city; it searches Google Jobs (which gathers LinkedIn, Indeed, Glassdoor, ZipRecruiter and company sites) and returns one row per job: title, company, location, posted date, job type, salary split into min / max / period when the employer published it, description and every "Apply on" link. An only-new-jobs mode returns just the jobs you have not seen yet.

**Try it:** [Google Jobs API on Apify](https://apify.com/om_kh/google-jobs-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [Google Jobs API](https://apify.com/om_kh/google-jobs-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "queries": [
    "data analyst"
  ],
  "locations": [
    "Chicago"
  ],
  "maxJobsPerSearch": 20
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

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

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-jobs-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"queries": ["data analyst"], "locations": ["Chicago"], "maxJobsPerSearch": 20}'
```

## What you get

- `title`
- `companyName`
- `location`
- `jobCity`
- `jobCountry`
- `workArrangement`
- `employmentType`
- `salaryYearlyMin`
- `salaryYearlyMax`
- `salaryPeriod`
- `postedAt`
- `via`
- `applyUrl`

## Price

Pay per job delivered; see the Pricing tab of the robot for today's price. A few jobs are free on every run on the free Apify plan, and a search Google cannot answer costs nothing. Set `maxTotalChargeUsd` to cap a run.

## Use cases

- Job boards and aggregators that need fresh listings
- Salary benchmarks by city and title
- Daily alerts on new jobs for a search
- AI agents that look up open roles

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-jobs-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Does it invent salaries?**  
No. Salary fields are filled only when the employer or Google published a salary.

**How many jobs per search?**  
Up to a few hundred per search; split a big search by city for more.

**Do I need a Google account or API key?**  
No.

## Related

- [ATS Jobs API - 123 ATS: Greenhouse, Lever, Workday Jobs](https://apify.com/om_kh/ats-jobs-api)
- [Company Careers Page Scraper - Jobs from Any Career Site](https://apify.com/om_kh/careers-page-scraper)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "Is there a Google Jobs API?", "acceptedAnswer": {"@type": "Answer", "text": "Google does not sell a public API that returns the Google Jobs search results, so use the Google Jobs API robot on Apify. Give it a job title or keyword and a city; it searches Google Jobs (which gathers LinkedIn, Indeed, Glassdoor, ZipRecruiter and company sites) and returns one row per job: title, company, location, posted date, job type, salary split into min / max / period when the employer published it, description and every \"Apply on\" link. An only-new-jobs mode returns just the jobs you have not seen yet."}}, {"@type": "Question", "name": "Does it invent salaries?", "acceptedAnswer": {"@type": "Answer", "text": "No. Salary fields are filled only when the employer or Google published a salary."}}, {"@type": "Question", "name": "How many jobs per search?", "acceptedAnswer": {"@type": "Answer", "text": "Up to a few hundred per search; split a big search by city for more."}}, {"@type": "Question", "name": "Do I need a Google account or API key?", "acceptedAnswer": {"@type": "Answer", "text": "No."}}]}
</script>

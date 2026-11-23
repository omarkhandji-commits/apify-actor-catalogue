---
title: "Company Careers Page Scraper - Jobs from Any Career Site"
description: "Company careers page scraper: paste company websites, get every open job with remote/hybrid/on-site, contract type, city, country, yearly salary, benefits, skills and apply link. Finds the ATS behind each site (123 systems, each tested on a real employer). $2.50 per 1,000 jobs, first 3 free."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Company Careers Page Scraper - Jobs from Any Career Site

Company careers page scraper: paste company websites, get every open job with remote/hybrid/on-site, contract type, city, country, yearly salary, benefits, skills and apply link. Finds the ATS behind each site (123 systems, each tested on a real employer). $2.50 per 1,000 jobs, first 3 free.

**Run it on Apify:** [https://apify.com/om_kh/careers-page-scraper](https://apify.com/om_kh/careers-page-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Company websites (`stripe.com`), up to 100 per run, or tick **Search all companies** with a keyword and/or a city |
| **We do** | Find which hiring system sits behind each careers page and read that system's official public feed |
| **You get** | One row per open job: title, company, location, department, posted date, salary when published (with `has_salary` and a readable `salary_text` such as "USD 248,000-310,000 per year"), apply link, full description, plus facts read from the text (years of experience, skills, remote or office, visa) |
| **It costs** | **$2.50 per 1,000 jobs** + $0.005 per run ($2.13 to $1.38 on paid plans). A company with 35 open roles costs about $0.09. The first 3 jobs of every run are free |
| **It does not** | Scrape LinkedIn, Indeed or job boards, or read pages behind a login. Workday is capped at 200 roles per company |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `companyDomains` | array | The company websites you want jobs from. Default: `["stripe.com", "figma.com", "notion.so"]`. |
| `searchAllCompanies` | boolean | Search the open roles of thousands of companies at once, without giving any company: set at least one keyword or location below (e.g. keywords 'data engineer', locations 'Berlin'). Default: `false`. |
| `keywords` | array | Keep only jobs whose title, department, company or location contains one of these words. |
| `excludeKeywords` | array | Drop jobs matching any of these words, e.g. intern, senior, sales. |
| `descriptionKeywords` | array | Keep jobs whose title or description contains one of these words or phrases, e.g. Kubernetes, visa sponsorship, 4-day week. |
| `locations` | array | Keep only jobs whose location contains one of these, e.g. Berlin, United Kingdom. |
| `remoteOnly` | boolean | Keep only roles whose location says remote, anywhere or distributed. Default: `false`. |
| `postedAfter` | string | Keep only jobs posted on or after this date (YYYY-MM-DD). |
| `employmentTypes` | array | Keep only these contract types (read from the job system's own field, the title, or a clear phrase in the text). |
| `workArrangements` | array | Keep only these work arrangements. |
| `countries` | array | Keep only jobs in these countries: names or 2-letter codes (United States, US, Germany, DE...). |
| `excludeTitleKeywords` | array | Drop jobs whose TITLE has any of these words (e.g. senior, intern, manager), even if the description mentions them. |
| `excludeCompanies` | array | Drop jobs from these companies (part of the name is enough). |
| `excludeLocations` | array | Drop jobs whose location contains any of these words (e.g. India, Remote - EMEA). |
| `departments` | array | Keep only these departments or teams (e.g. Engineering, Sales). |
| `excludeAgencies` | boolean | Drop jobs posted by staffing or recruitment agencies for a client. Default: `false`. |
| `onlyWithSalary` | boolean | Keep only jobs that publish a pay range (as numbers, with the pay period and a yearly equivalent). Default: `false`. |
| `minYearlySalary` | integer | Keep only jobs paying at least this much per year (hourly, daily and monthly pay converted to yearly). |
| `postedWithin` | string | Keep only jobs posted in this window. |
| `maxYearlySalary` | integer | Drop jobs whose yearly pay starts above this (hourly, daily and monthly pay converted to yearly). |
| `jobFunctions` | array | Keep only these job families, read from the title (Engineering, Sales, Data & AI...). |
| `seniorities` | array | Keep only these levels, read from the title. |
| `skills` | array | Keep only jobs asking for at least one of these skills (read from the description, or the title), e.g. Python, Salesforce, SQL. |
| `excludeSkills` | array | Drop jobs asking for any of these skills. |
| `visaSponsorship` | string | Keep only jobs whose description says this about visa or work-permit sponsorship. |
| `maxExperienceYears` | integer | Drop jobs asking for more years of experience than this (jobs that ask for none are kept). |
| `excludeDescriptionKeywords` | array | Drop jobs whose title or description contains any of these words, e.g. clearance, commission only. |
| `languages` | array | Keep only postings written in these languages (read from the text). |
| `onlyCompanies` | array | With "search all companies": keep only jobs of companies whose name contains one of these words. |
| `onlyNewJobs` | boolean | Deliver only the jobs this same search has not delivered before (remembered in your own Apify account). Default: `false`. |
| `memoryName` | string | Give the 'only new jobs' memory a name to share it between tasks or keep it when you change the search. |
| `includeDescription` | boolean | Add the full job description (plain text), salary, contract type, workplace type and apply link when the company's ATS publishes them (Greenhouse, Lever, Ashby). Default: `true`. |
| `includeCompanyProfile` | boolean | Add each company's industry, employee count, size band (1-10 ... 10,001+), headquarters and founding year, from Wikidata by the company's website. Default: `true`. |
| `industries` | array | Keep only companies whose industry contains one of these words (software, retail, insurance, financial...). |
| `companySizes` | array | Keep only companies of these sizes (employees). |
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
  "domain": "stripe.com",
  "ats_match": "guessed",
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
run = client.actor("om_kh/careers-page-scraper").call(run_input={
    "companyDomains": [
        "stripe.com",
        "figma.com",
        "notion.so"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~careers-page-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"companyDomains": ["stripe.com", "figma.com", "notion.so"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/careers-page-scraper` as a tool.

Full documentation, pricing and the latest changes: [Company Careers Page Scraper - Jobs from Any Career Site](https://apify.com/om_kh/careers-page-scraper).

[← Catalogue home](../../README.md) · [Jobs & Hiring family](../jobs.md)

# Get current jobs from a company without knowing its ATS

## Problem

You have a list of company domains and want their current job openings. You don't know (and don't want to figure out) whether each one runs Greenhouse, Lever, Ashby, or Workday.

## Actors used

1. [Career Site Job Listing API](https://apify.com/om_kh/careers-page-scraper) — required
2. [Hiring Signals](https://apify.com/om_kh/company-hiring-signals) — optional, if you want a change signal instead of (or alongside) raw listings

## Inputs

```json
{
  "companyDomains": ["stripe.com"],
  "maxTotalChargeUsd": 1
}
```

## Steps

1. Run **Career Site Job Listing API** with your company domain(s). It auto-detects the ATS behind each domain and returns current listings.
2. (Optional) Run **Hiring Signals** on the same domain(s) if what you actually want is a change/trend signal rather than the raw list.

## Sample result shape

*Illustrative — derived from the Actor's real dataset schema, not live data.*

```json
{
  "title": "Account Executive, Enterprise",
  "company": "stripe",
  "location": "US-Remote",
  "postedDate": "2026-08-19T14:02:07-04:00",
  "applyUrl": "https://stripe.com/jobs/search?gh_jid=8130725",
  "atsProvider": "greenhouse"
}
```

## Try it live

[Public Task example (Stripe)](https://apify.com/om_kh/careers-page-scraper/examples/careers-page-scraper-single-company)

## Code

### curl

```bash
curl "https://api.apify.com/v2/actor-tasks/om_kh~careers-page-scraper-single-company/run-sync-get-dataset-items?token=$APIFY_TOKEN" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"companyDomains": ["stripe.com"], "maxTotalChargeUsd": 1}'
```

### Python

```python
import os, requests

token = os.environ["APIFY_TOKEN"]
url = "https://api.apify.com/v2/actor-tasks/om_kh~careers-page-scraper-single-company/run-sync-get-dataset-items"
resp = requests.post(url, params={"token": token}, json={"companyDomains": ["stripe.com"], "maxTotalChargeUsd": 1})
jobs = resp.json()
```

### JavaScript

```javascript
const token = process.env.APIFY_TOKEN;
const res = await fetch(
  `https://api.apify.com/v2/actor-tasks/om_kh~careers-page-scraper-single-company/run-sync-get-dataset-items?token=${token}`,
  {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ companyDomains: ["stripe.com"], maxTotalChargeUsd: 1 }),
  }
);
const jobs = await res.json();
```

## Next step

Found a company worth reaching out to? See [Leads & Verification](../leads-verification.md) to get a verified contact email for it.

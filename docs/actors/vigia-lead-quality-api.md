---
title: "Business Email Finder API - Verify, Score, Confidence"
description: "Business email finder and verifier for CRM-ready lead lists. Give company domains or names and get back verified emails with a confidence score, MX validity, role type and evidence source for each. Only verified leads are charged, and the first 5 of every run are free. $0.01 per verified lead."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Business Email Finder API - Verify, Score, Confidence

Business email finder and verifier for CRM-ready lead lists. Give company domains or names and get back verified emails with a confidence score, MX validity, role type and evidence source for each. Only verified leads are charged, and the first 5 of every run are free. $0.01 per verified lead.

**Run it on Apify:** [https://apify.com/om_kh/vigia-lead-quality-api](https://apify.com/om_kh/vigia-lead-quality-api) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Company domains or names |
| **We do** | Find and verify business emails for each company |
| **You get** | One row per company: verified business emails with a confidence score, mail-server check, role type and the source where each was found |
| **It costs** | $0.01 per verified lead (was $0.035 until 20 November 2026) + $0.001 per run. Only verified leads are charged; the first 5 of every run are free |
| **It does not** | Send emails for you |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `websiteUrls` | array | Optional HTTP(S) URLs. |
| `candidates` | array | Optional pre-collected candidates. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Customer CRM export", "authorization": "customer_`. |
| `monitorEnabled` | boolean | On the first monitored run, Vigia saves a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |
| `maxTotalChargeUsd` | number | Hard cap for Vigia qualified-lead events. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "74cdb620132a538f2ddaee5c",
  "entity_type": "company",
  "legal_name": "basecamp.com",
  "website": "https://basecamp.com",
  "business_contacts": [
    {
      "email": "(hidden here)",
      "kind": "published_business",
      "verification_level": "mx_valid",
      "isDeliverable": true,
      "isDisposable": false,
      "isRoleAccount": false,
      "isSafeToSend": true
    }
  ],
  "confidence": 0.9
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/vigia-lead-quality-api").call(run_input={
    "websiteUrls": [
        "https://basecamp.com",
        "https://www.gnu.org"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~vigia-lead-quality-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"websiteUrls": ["https://basecamp.com", "https://www.gnu.org"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/vigia-lead-quality-api` as a tool.

Full documentation, pricing and the latest changes: [Business Email Finder API - Verify, Score, Confidence](https://apify.com/om_kh/vigia-lead-quality-api).

---
title: "Netherlands Company Registry Scraper - Name, KVK, Status"
description: "Verify Dutch companies against the KVK Handelsregister: legal name, KVK number, status, legal form, registered address and trade names, with the source for every field. Search by name or number, export to JSON, CSV or Excel. Our fee $0.012 per company + supplier. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Netherlands Company Registry Scraper - Name, KVK, Status

Verify Dutch companies against the KVK Handelsregister: legal name, KVK number, status, legal form, registered address and trade names, with the source for every field. Search by name or number, export to JSON, CSV or Excel. Our fee $0.012 per company + supplier. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/netherlands-company-registry-scraper](https://apify.com/om_kh/netherlands-company-registry-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Dutch company names or KVK numbers |
| **We do** | Look each one up in the Dutch business registry (KVK) and check the match |
| **You get** | One row per company: KVK number, legal name, status, legal form and registered address, with a warning when names could be confused, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.012 per company, $0.002 from 6 December 2026, + $0.001 per run. Apify also bills the supplier Actor `dltik/netherlands-kvk-company-scraper` that this robot runs for you, at its own price (about $5 per 1,000 results). An item that returns an error is never charged |
| **It does not** | Sign in to KVK or buy paid registry extracts |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `companyNames` | array | Company names to verify against the KVK Handelsregister. Default: `["ASML"]`. |
| `kvkNumbers` | array | KVK registration numbers, if you have them instead of names. |
| `includeOfficers` | boolean | Reserved for future use — the current source does not expose officer records. Default: `false`. |
| `includeFilings` | boolean | Reserved for future use — the current source does not expose filing history. Default: `false`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only companies not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "company_number": "17085815",
  "legal_name": "ASML Holding",
  "company_status": "active",
  "legal_form": "Naamloze Vennootschap",
  "registered_address": "De Run 6501 5504DR Veldhoven",
  "name_collision_risk": true,
  "name_collision_reason": "searched 'ASML', closest match on file is 'ASML Holding' -- not an exact name match, verify this is the intended company before trusting it"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/netherlands-company-registry-scraper").call(run_input={
    "companyNames": [
        "ASML"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~netherlands-company-registry-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"companyNames": ["ASML"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/netherlands-company-registry-scraper` as a tool.

Full documentation, pricing and the latest changes: [Netherlands Company Registry Scraper - Name, KVK, Status](https://apify.com/om_kh/netherlands-company-registry-scraper).

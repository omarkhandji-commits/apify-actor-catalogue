---
title: "ThomasNet Supplier Scraper - Name, Address, Verified Status"
description: "Verify US industrial suppliers against ThomasNet: legal name, address, year established, employee range, product and service categories and public contact. One failed lookup never stops your batch. Export to JSON, CSV or Excel. Our fee $0.011 per supplier + source. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# ThomasNet Supplier Scraper - Name, Address, Verified Status

Verify US industrial suppliers against ThomasNet: legal name, address, year established, employee range, product and service categories and public contact. One failed lookup never stops your batch. Export to JSON, CSV or Excel. Our fee $0.011 per supplier + source. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/thomasnet-supplier-scraper](https://apify.com/om_kh/thomasnet-supplier-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Company names |
| **We do** | Find and check each company's ThomasNet listing |
| **You get** | One row per supplier: legal name, website, address, year founded, employee range, products, capabilities and a public contact, plus every field the supplier returns (`source_data`) |
| **It costs** | $0.011 per verified supplier, $0.0025 from 2 December 2026, + $0.001 per run. Apify also bills the supplier Actor `zen-studio/thomasnet-suppliers-scraper` that this robot runs for you, at its own price (about $4.99 per 1,000 results). An item that returns an error is never charged |
| **It does not** | Sign in to ThomasNet or send quote requests |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `companyNames` | array | Company names to verify against ThomasNet. Default: `["Boeing"]`. |
| `supplierUrls` | array | ThomasNet supplier profile URLs, if you have them. |
| `keywords` | array | Secondary: product or service keywords, if you don't have exact company names. |
| `includeContacts` | boolean | Look for a public business email on the supplier's own website, in addition to the phone number ThomasNet lists. Default: `false`. |
| `maxResults` | integer | Stop after this many suppliers. Default: `20`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only suppliers not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "supplier_id": "10005409",
  "legal_name": "Boeing",
  "website": "https://www.boeing.com/",
  "address": {
    "line1": "100 N. Riverside Dr.",
    "city": "Chicago",
    "state": "IL",
    "zip": "60606",
    "country": "USA"
  },
  "year_established": "1916",
  "employee_range": "1000+",
  "capabilities": [
    "Air Jets",
    "Aircraft"
  ],
  "products": [
    "Air Jets",
    "Aircraft"
  ],
  "public_contact": {
    "phone": "(hidden here)",
    "source": "https://www.boeing.com/"
  },
  "description": "Manufacturer of jetliners and military aircraft for commercial, space and defense sectors. Helicopters, jets, missiles, satellites and sp...",
  "supplier_type": "Manufacturer",
  "latitude": 41.88304038,
  "longitude": -87.6370655,
  "annual_sales": "$250 Mil. and over",
  "logo_url": "https://cdn.thomasnet.com/ritekit/boeing.com.png",
  "is_claimed": true,
  "is_advertiser": false,
  "xometry_verified": false,
  "location_count": 4,
  "location_types": [
    "Corporate/Admin Office"
  ],
  "locations": [
    {
      "name": "(hidden here)",
      "phone": "(hidden here)",
      "city": "Chicago",
      "state": "Illinois"
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/thomasnet-supplier-scraper").call(run_input={
    "companyNames": [
        "Boeing"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~thomasnet-supplier-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"companyNames": ["Boeing"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/thomasnet-supplier-scraper` as a tool.

Full documentation, pricing and the latest changes: [ThomasNet Supplier Scraper - Name, Address, Verified Status](https://apify.com/om_kh/thomasnet-supplier-scraper).

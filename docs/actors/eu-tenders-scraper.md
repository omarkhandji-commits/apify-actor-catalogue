---
title: "TED Europa Tenders Scraper - EU Public Procurement, Winners"
description: "TED Europa tenders scraper: scrape EU public tenders from TED, the official EU journal: open calls with deadline, value, buyer email and documents, plus awards with winners. Filter by keyword, country, CPV, buyer, procedure, nature, value, date. Optional AI summary with your own key."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# TED Europa Tenders Scraper - EU Public Procurement, Winners

TED Europa tenders scraper: scrape EU public tenders from TED, the official EU journal: open calls with deadline, value, buyer email and documents, plus awards with winners. Filter by keyword, country, CPV, buyer, procedure, nature, value, date. Optional AI summary with your own key.

**Run it on Apify:** [https://apify.com/om_kh/eu-tenders-scraper](https://apify.com/om_kh/eu-tenders-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords, countries, CPV codes and dates |
| **We do** | Read TED, the official journal of EU public procurement, through its official API |
| **You get** | One row per notice: open calls with deadline, estimated value, buyer email, documents and submission links; contract awards with the winning companies, their emails and the contract value |
| **It costs** | $1.50 per 1,000 notices + $0.001 per run. The first 20 notices of every run are free; a query TED rejects is never charged. No supplier fee |
| **It does not** | Cover tenders below the EU thresholds (those are on each country's own portal), or return more than 15,000 notices per query |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Words searched in the full notice text (any language), e.g. software, cleaning, construction. Default: `["software"]`. |
| `countries` | array | Two-letter codes of the buying country, e.g. FR, DE, IT, ES, NL, PL, IE. Default: `["FR", "DE"]`. |
| `cpvCodes` | array | EU procurement categories. |
| `buyerName` | string | Part of the buyer's name, e.g. Ministère, Bundesamt, Comune di. |
| `procedureTypes` | array | Keep only these procedures. |
| `contractNatures` | array | Keep only these kinds of contract. |
| `minValue` | integer | Keep only notices whose estimated or awarded value is at least this amount. |
| `noticeKind` | string | Open calls for tenders, contract awards (with winners), planned (prior information), or all. Default: `"all"`. |
| `onlyOpenDeadlines` | boolean | Keep only calls whose submission deadline is today or later. Default: `false`. |
| `publishedAfter` | string | YYYY-MM-DD. |
| `publishedBefore` | string | YYYY-MM-DD. |
| `language` | string | Preferred language for titles and descriptions when available (otherwise the original language). Default: `"en"`. |
| `maxNotices` | integer | Newest first, 1 to 15,000. Default: `100`. |
| `customQuery` | string | A TED expert query that replaces the filters above, e.g. FT~"cloud" AND buyer-country IN (FRA) AND publication-date>=20260901. |
| `analyzeWithAi` | boolean | Add an ai object to each notice: plain summary, deliverables, and a 0-100 fit score with a recommended action when you describe your company below. Default: `false`. |
| `anthropicApiKey` | string | Needed only for the AI analysis. |
| `aiModel` | string | Claude model ID, e.g. claude-opus-5-5 (default), claude-sonnet-5-5 or claude-haiku-4-5 for a lower cost. Default: `"claude-opus-5-5"`. |
| `maxAiRows` | integer | The AI reads at most this many results per run (1 to 500), to keep your model bill predictable. Default: `100`. |
| `businessProfile` | string | What your company sells or does, e.g. 'Cloud infrastructure and DevOps consulting for public bodies, 40 people, France and Belgium'. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "noticeId": "735326-2026",
  "title": "Germany – IT services: consulting, software development, Internet and support – KI-Prototypenentwicklung",
  "description": "Das Jobcenter Neue Wege Kreis Bergstraße ist Eigenbetrieb des Kreis Bergstraße. Es führt für den Kreis das Förderprojekt KI_Hub Kommunal...",
  "noticeType": "cn-standard",
  "procedureType": "open",
  "contractNature": "services",
  "publicationDate": "2026-10-23",
  "deadline": "2026-11-23",
  "buyerName": "Neue Wege Kreis Bergstraße - Kommunales Jobcenter -",
  "buyerCountry": "DEU",
  "buyerCity": "Heppenheim",
  "buyerEmail": "(hidden here)",
  "buyerWebsite": "https://www.neue-wege.org",
  "estimatedValue": 88235.29,
  "estimatedValueCurrency": "EUR",
  "totalValue": 88235.29,
  "totalValueCurrency": "EUR",
  "cpvCodes": [
    "72000000"
  ],
  "placeOfPerformance": [
    "DE715",
    "DEU"
  ],
  "documentsUrl": "https://www.had.de/NetServer/TenderingProcedureDetails?function=_Details&TenderOID=54321-Tender-1a163043be1-4c0979b5cbac8ea1",
  "submissionUrl": "https://www.had.de",
  "noticeUrl": "https://ted.europa.eu/en/notice/-/detail/735326-2026",
  "pdfUrl": "https://ted.europa.eu/en/notice/735326-2026/pdf",
  "query": "(FT~\"software\") AND buyer-country IN (FRA DEU) AND notice-type IN (cn-standard cn-social cn-desg qu-sy subco) AND publication-date>=20260923",
  "totalMatching": 919
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/eu-tenders-scraper").call(run_input={
    "keywords": [
        "software"
    ],
    "countries": [
        "FR",
        "DE"
    ],
    "noticeKind": "open",
    "maxNotices": 50
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~eu-tenders-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["software"], "countries": ["FR", "DE"], "noticeKind": "open", "maxNotices": 50}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/eu-tenders-scraper` as a tool.

Full documentation, pricing and the latest changes: [TED Europa Tenders Scraper - EU Public Procurement, Winners](https://apify.com/om_kh/eu-tenders-scraper).

---
title: "France Company Registry Scraper - Search, SIREN, VAT"
description: "French company registry API (Sirene): look up a name or SIREN, or search 26M companies by text, place, activity, size, revenue, director or radius. Officers, 10 years of accounts and ratios, VAT + VIES check, BODACC notices. $2.50 per 1,000 companies. Official sources, no key."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# France Company Registry Scraper - Search, SIREN, VAT

French company registry API (Sirene): look up a name or SIREN, or search 26M companies by text, place, activity, size, revenue, director or radius. Officers, 10 years of accounts and ratios, VAT + VIES check, BODACC notices. $2.50 per 1,000 companies. Official sources, no key.

**Run it on Apify:** [https://apify.com/om_kh/france-company-registry-scraper](https://apify.com/om_kh/france-company-registry-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | French company names or SIREN numbers |
| **We do** | Read the French State's official Sirene registry |
| **You get** | One row per company: legal name, status, legal form, head-office address and SIRET, activity (NAF) code, officers (role, birth year-month, nationality), employee band, size, creation date, VAT number, and **up to 10 years of accounts** (revenue, net income, EBITDA, EBIT, margins, debt, liquidity and equity ratios) with revenue growth |
| **It costs** | $2.50 per 1,000 companies (since 21 Nov 2026; was $4) + $0.001 per run. A lookup that fails, or that comes back with a name-collision doubt, is never charged. No supplier fee |
| **It does not** | Need an API key or sign in |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `companyNames` | array | Company names to verify against the French Sirene registry. Default: `["Danone"]`. |
| `sirenNumbers` | array | SIREN registration numbers, if you have them instead of names. |
| `includeOfficers` | boolean | Reserved for future use pending live schema confirmation. Default: `false`. |
| `includeFilings` | boolean | Reserved for future use pending live schema confirmation. Default: `false`. |
| `includeFinancialHistory` | boolean | Add up to 10 years of filed accounts per company: revenue, net income, EBITDA, EBIT, gross margin, debt, liquidity and equity ratios, customer and supplier credit days. Default: `true`. |
| `searchQuery` | string | Search the whole register by name, address or director: boulangerie Lyon, Bernard Arnault. |
| `department` | string | Two-digit code: 75 Paris, 69 Rhône, 13 Bouches-du-Rhône. |
| `postalCode` | string | Five digits, e.g. 75009. |
| `cityCode` | string | e.g. 75109 for Paris 9th. |
| `region` | string | Two-digit code: 11 Île-de-France, 84 Auvergne-Rhône-Alpes. |
| `nafCode` | string | e.g. 62.01Z software, 56.10A restaurants. |
| `nafSection` | string | One letter: A agriculture, C manufacturing, F construction, G trade, J information, K finance, M consulting. |
| `companyCategory` | string | The official size category. |
| `employeeBand` | string | INSEE code: 00=0, 01=1-2, 02=3-5, 03=6-9, 11=10-19, 12=20-49, 21=50-99, 22=100-199, 31=200-249, 32=250-499, 41=500-999, 42=1000-1999, 51=2000-4999, 52=5000-9999, 53=10000+. |
| `companyStatus` | string | For searches. Default: `"active"`. |
| `personLastName` | string | e.g. ARNAULT. |
| `personFirstName` | string | Used with the last name. |
| `personType` | string | Used with the name fields. |
| `revenueMin` | integer | Only companies that filed accounts have a revenue. |
| `revenueMax` | integer | Only companies that filed accounts have a revenue. |
| `latitude` | string | With longitude and radius: every company around a point, e.g. 48.8566. |
| `longitude` | string | e.g. 2.3522. |
| `radiusKm` | number | 0.1 to 50 km. Default: `5`. |
| `rgeOnly` | boolean | Reconnu Garant de l'Environnement (eco-construction). Default: `false`. |
| `qualiopiOnly` | boolean | Training quality certification. Default: `false`. |
| `organicOnly` | boolean | Agence Bio. Default: `false`. |
| `socialEconomyOnly` | boolean | Économie sociale et solidaire. Default: `false`. |
| `associationsOnly` | boolean | Loi 1901 associations. Default: `false`. |
| `trainingOrganizationsOnly` | boolean | Registered training providers. Default: `false`. |
| `missionCompaniesOnly` | boolean | Sociétés à mission. Default: `false`. |
| `maxResults` | integer | 1 to 10,000 (the register's own limit per search). Default: `100`. |
| `validateVat` | boolean | Every company gets its intra-EU VAT number (vat_number). Default: `false`. |
| `checkBodacc` | boolean | Add the number of gazette notices and the date and kind of the latest one: a quick risk and activity signal. Default: `false`. |
| `analyzeWithAi` | boolean | Add an ai object: what the company does, and a 0-100 fit score when you describe what you sell. Default: `false`. |
| `anthropicApiKey` | string | Needed only for the AI analysis. |
| `aiModel` | string | Claude model ID, e.g. claude-opus-5-5 (default), claude-sonnet-5-5 or claude-haiku-4-5 for a lower cost. Default: `"claude-opus-5-5"`. |
| `businessProfile` | string | Used by the AI to score how well each company fits you. |
| `maxAiRows` | integer | 1 to 500 per run. Default: `100`. |
| `monitorEnabled` | boolean | On later runs with the same Monitor ID, deliver only companies not seen before. Default: `false`. |
| `monitorId` | string | Groups runs into one monitored target. |
| `maxTotalChargeUsd` | number | Hard ceiling on what this run can bill you. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "company_number": "552032534",
  "legal_name": "DANONE",
  "company_status": "active",
  "legal_form": "5599",
  "registered_address": {
    "street": "59-61 RUE LA FAYETTE 75009 PARIS",
    "postal_code": "75009",
    "city": "PARIS",
    "country": "France"
  },
  "activity_description": "70.10Z",
  "officers": [
    {
      "name": "(hidden here)",
      "role": "Directeur Général"
    },
    {
      "name": "(hidden here)",
      "role": "Administrateur"
    }
  ],
  "hq_siret": "55203253400703",
  "created_on": "1955-01-01",
  "company_category": "GE",
  "employees": "1000-1999",
  "establishments_open": 3,
  "financial_year": "2025",
  "revenue_eur": 27376000000,
  "net_income_eur": 2100000000,
  "latitude": "48.8763540066087",
  "longitude": "2.34353640229216",
  "vat_number": "FR27552032534",
  "name_collision_risk": false
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/france-company-registry-scraper").call(run_input={
    "companyNames": [
        "Danone"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~france-company-registry-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"companyNames": ["Danone"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/france-company-registry-scraper` as a tool.

Full documentation, pricing and the latest changes: [France Company Registry Scraper - Search, SIREN, VAT](https://apify.com/om_kh/france-company-registry-scraper).

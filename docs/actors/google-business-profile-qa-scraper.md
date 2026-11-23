---
title: "Google Business Profile Q&A Scraper - Questions, Answers"
description: "Scrape questions and answers from any Google Business Profile: question, answers, author type, date and unanswered flag. Export to JSON, CSV or Excel, or call it as an API. No login needed. For local SEO, reputation management and customer-intent research. $7.50 per 1,000 unanswered questions."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Google Business Profile Q&A Scraper - Questions, Answers

Scrape questions and answers from any Google Business Profile: question, answers, author type, date and unanswered flag. Export to JSON, CSV or Excel, or call it as an API. No login needed. For local SEO, reputation management and customer-intent research. $7.50 per 1,000 unanswered questions.

**Run it on Apify:** [https://apify.com/om_kh/google-business-profile-qa-scraper](https://apify.com/om_kh/google-business-profile-qa-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Google Maps places (business names or links) |
| **We do** | Read the questions and answers on each Google Business Profile |
| **You get** | One row per question: the question, its answers, who answered (owner or public), the date and an unanswered flag, plus every field the supplier returns (`source_data`) |
| **It costs** | $7.50 per 1,000 unanswered questions, + $0.001 per run. Optional scheduled monitoring: +$0.03 per check (one-off runs never pay it). Apify also bills the supplier Actor `compass/crawler-google-places` that this robot runs for you, at its own price (about $4 per 1,000 results). The first 10 results of every run are free of this robot's fee. |
| **It does not** | Sign in to Google or post answers for you |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `placeUrls` | array | Google Maps URLs for the business listing(s) whose public Q&A you want monitored. |
| `currentQuestions` | array | Skip the chained Google Maps fetch and pass Q&A data directly. |
| `previousQuestions` | array | Questions from the prior run; used to identify new ones when not using persistent monitor mode. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Chained Google Maps actor", "authorization": "pub`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "question_id": "172ab7a97fe567557afee194",
  "place_id": "ChIJN1t_tDeuEmsRUsoyG83frY4",
  "question_text": "$ taken from my account by Google\nAust pty Ltd  . I did not buy anything. What do I do about it?",
  "answered": false,
  "question": "$ taken from my account by Google\nAust pty Ltd  . I did not buy anything. What do I do about it?",
  "askDate": "8 years ago",
  "askedBy_name": "Ann Soley",
  "askedBy_url": "https://lh3.googleusercontent.com/a-/ALV-UjWkTzVpUspqZgzm7SWCSBVNaq-B7bijQWMcGPXBZujrhtzt-Z05=s120-c-rp-mo-ba12-br100",
  "record_id": "172ab7a97fe567557afee194",
  "change_type": "new",
  "actionable": true,
  "signals": [
    "needs_answer"
  ],
  "why_it_matters": "New customer question posted with no answer yet — reply before it costs you a sale."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-business-profile-qa-scraper").call(run_input={
    "placeUrls": [
        "https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-business-profile-qa-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"placeUrls": ["https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-business-profile-qa-scraper` as a tool.

Full documentation, pricing and the latest changes: [Google Business Profile Q&A Scraper - Questions, Answers](https://apify.com/om_kh/google-business-profile-qa-scraper).

---
title: "Review Cleaner & Deduplicator - Fakes, Duplicates, Score"
description: "Clean review exports from any source into one schema: rating, title, text, author, date and ID, with duplicates removed and fake-looking rows scored. Compare two exports to isolate genuinely new reviews. Bring your own data; no scraping. For analysts and reputation teams. $0.02 per review row."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Review Cleaner & Deduplicator - Fakes, Duplicates, Score

Clean review exports from any source into one schema: rating, title, text, author, date and ID, with duplicates removed and fake-looking rows scored. Compare two exports to isolate genuinely new reviews. Bring your own data; no scraping. For analysts and reputation teams. $0.02 per review row.

**Run it on Apify:** [https://apify.com/om_kh/reviews-cleaner-deduplicator](https://apify.com/om_kh/reviews-cleaner-deduplicator) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Your own review exports (from any site), one or two of them |
| **We do** | Put them into one format, remove duplicates, score fake-looking reviews, and with two exports keep only the new ones |
| **You get** | One row per review: rating, title, text, author, date, ID, topic, severity and the signals behind the fake score |
| **It costs** | $0.02 per review row delivered + $0.001 per run. The first 10 results of every run are free. No scraping, so no supplier fee |
| **It does not** | Collect reviews from websites: you bring the data |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `previousReviews` | array | Reviews from the prior run; used to identify new feedback. |
| `currentReviews` | array | Current authorized review data to analyse. Default: `[{"reviewId": "r1", "rating": 2, "text": "Package arrived la`. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Customer-authorized input", "authorization": "cus`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "reviewId": "r1",
  "rating": 2,
  "text": "Package arrived late and damaged.",
  "author": "(hidden here)",
  "record_id": "902c051b3cd8bb0e8161598e",
  "change_type": "new",
  "actionable": true,
  "signals": [
    "response_needed"
  ],
  "topic": "shipping",
  "severity": "moderate",
  "why_it_matters": "New 2-star negative review needs attention. Worth a quick reply."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/reviews-cleaner-deduplicator").call(run_input={
    "currentReviews": [
        {
            "reviewId": "r1",
            "rating": 2,
            "text": "Package arrived late and damaged.",
            "author": "Sam"
        }
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~reviews-cleaner-deduplicator/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"currentReviews": [{"reviewId": "r1", "rating": 2, "text": "Package arrived late and damaged.", "author": "Sam"}]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/reviews-cleaner-deduplicator` as a tool.

Full documentation, pricing and the latest changes: [Review Cleaner & Deduplicator - Fakes, Duplicates, Score](https://apify.com/om_kh/reviews-cleaner-deduplicator).

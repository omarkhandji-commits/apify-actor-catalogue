---
title: "Stack Overflow Scraper - Questions, Answers, Vote Count"
description: "Stack Overflow scraper for every Stack Exchange site: search by text or tag, fetch questions by id, sort by date, votes or activity, add the answers. Up to 2,500 per search. Official Stack Exchange API, so it never breaks. $2 per 1,000 questions."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Stack Overflow Scraper - Questions, Answers, Vote Count

Stack Overflow scraper for every Stack Exchange site: search by text or tag, fetch questions by id, sort by date, votes or activity, add the answers. Up to 2,500 per search. Official Stack Exchange API, so it never breaks. $2 per 1,000 questions.

**Run it on Apify:** [https://apify.com/om_kh/stack-overflow-scraper](https://apify.com/om_kh/stack-overflow-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords, tags or question IDs, on Stack Overflow or any Stack Exchange site |
| **We do** | Read the official Stack Exchange API |
| **You get** | One row per question: title, link, score, answer count, answered flag, views, tags, author and reputation, date; option: the answers |
| **It costs** | $2 per 1,000 questions + $0.001 per run. Optional scheduled monitoring: +$0.002 per check (one-off runs never pay it). The first 10 results of every run are free. No supplier fee |
| **It does not** | Sign in, vote or post |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `tags` | array | Tags to monitor (e.g. 'python', 'react', 'your-product'). Default: `["your-product", "react"]`. |
| `searchTerms` | array | Full-text searches, e.g. pandas merge, docker compose. |
| `questionIds` | array | Specific questions to fetch, by number or by link. |
| `site` | string | stackoverflow, superuser, serverfault, askubuntu, math, unix... (the name in the site's address). Default: `"stackoverflow"`. |
| `sortBy` | string | Order of the questions. Default: `"newest"`. |
| `maxItems` | integer | 1 to 2,500. Default: `100`. |
| `includeAnswers` | boolean | Add each question's answers (score, accepted flag, body, author) in an answers field. Default: `false`. |
| `dateFrom` | string | YYYY-MM-DD, inclusive. |
| `dateTo` | string | YYYY-MM-DD, inclusive. |
| `minScore` | integer | Keep only questions with at least this score. |
| `answeredOnly` | boolean | For text searches: keep only questions that have an accepted answer. Default: `false`. |
| `apiKey` | string | Without a key Stack Exchange allows about 300 calls a day per address, which is enough for most runs. |
| `currentItems` | array | Skip the chained fetch and pass records directly (no upstream call, no fetch fee). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Stack Exchange official API (first-party)", "auth`. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice, so separate targets never share state. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "80011381",
  "query_id": "tag:react",
  "title": "Redux-Toolkit Query and setting state in `useEffect`",
  "url": "https://stackoverflow.com/questions/80011381/redux-toolkit-query-and-setting-state-in-useeffect",
  "text": "<p>I'm running into a new-to-me linting error from <a href=\"https://react.dev/reference/eslint-plugin-react-hooks\" rel=\"nofollow noreferr...",
  "author": "(hidden here)",
  "published_at": "2026-10-20T17:12:28+00:00",
  "score": 0,
  "question_id": "80011381",
  "tags": [
    "best-practices",
    "reactjs"
  ],
  "answer_count": 3,
  "is_answered": true,
  "view_count": 119,
  "accepted_answer_id": 80011540,
  "author_reputation": "(hidden here)",
  "site": "stackoverflow",
  "extra_tags": [
    "best-practices",
    "reactjs"
  ],
  "extra_is_answered": true
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/stack-overflow-scraper").call(run_input={
    "tags": [
        "your-product",
        "react"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~stack-overflow-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"tags": ["your-product", "react"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/stack-overflow-scraper` as a tool.

Full documentation, pricing and the latest changes: [Stack Overflow Scraper - Questions, Answers, Vote Count](https://apify.com/om_kh/stack-overflow-scraper).

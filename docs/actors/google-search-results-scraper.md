---
title: "Google Search Results Scraper - Rankings, SERP, Position"
description: "Scrape Google search results for any keyword: position, title, URL, domain and snippet, and where your own site ranks. No login or Google API key needed. For SEO rank checks, keyword research and competitor analysis. $7 per 1,000 keywords. All supplier fields included."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Google Search Results Scraper - Rankings, SERP, Position

Scrape Google search results for any keyword: position, title, URL, domain and snippet, and where your own site ranks. No login or Google API key needed. For SEO rank checks, keyword research and competitor analysis. $7 per 1,000 keywords. All supplier fields included.

**Run it on Apify:** [https://apify.com/om_kh/google-search-results-scraper](https://apify.com/om_kh/google-search-results-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords, and optionally your own website |
| **We do** | Search Google for each keyword and record every ranking result |
| **You get** | One row per result: position, title, link, domain and snippet, plus where your site ranks and what moved since your last run, plus every field the supplier returns (`source_data`) |
| **It costs** | **$7 per 1,000 keywords checked** (all ranking rows of a keyword included), + $0.001 per run from Dec 1, 2026 (no start fee before). Optional scheduled monitoring: +$0.02 per check (one-off runs never pay it). Apify also bills the supplier Actor `apify/google-search-scraper` that this robot runs for you, at its own price (about $4.50 per 1,000 results). The first 3 keywords of every run are free of this robot's fee. |
| **It does not** | Need a Google API key, or give search volumes |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `keywords` | array | Search keywords/queries to check on Google. |
| `trackedDomains` | array | Optional. |
| `countryCode` | string | Google country to search from, e.g. "us", "ca", "fr". Default: `"us"`. |
| `languageCode` | string | Search language, e.g. "en", "fr". Default: `"en"`. |
| `currentResults` | array | Bring your own organicResults (e.g. from a prior Google Search Results Scraper run) instead of Vigia fetching them. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run's own rank-change events may charge. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Google Search Results (via apify/google-search-sc`. |

## Example output

A row as shown in the Actor's README:

```json
{
  "record_id": "project management software::icagile.com",
  "keyword": "project management software",
  "domain": "icagile.com",
  "position": 2,
  "url": "https://www.icagile.com/resources/honest-review-of-6-personal-project-management-tools-with-kanban-view",
  "title": "Honest Review of 6 Personal Project Management Tools ...",
  "description": "Comparing 6 Popular Tools for Personal Project Management with Kanban View · 1. Clickup · 2. Trello · 3. Asana · 4. Wrike · 5. Monday.com...",
  "site_name": "ICAgile | International Consortium for Agile",
  "displayed_url": "https://www.icagile.com › resources › honest-review-of...",
  "published_at": "2024-09-13T12:00:00.000Z",
  "result_type": "organic",
  "emphasized_keywords": [
    "1. Clickup"
  ],
  "page_ads_count": 2,
  "page_ad_domains": [
    "google.com"
  ],
  "page_ad_titles": [
    "Project Mgmt & Help Desk | IT Task managementProject Management Software | Preferred by 3 Million UsersSmarter IT, Less Overhead | Get Ex...",
    "Project Mgmt & Help Desk | The Control Center of Your ITProject Management Software"
  ],
  "page_people_also_ask": [
    "What is the most used project management software?",
    "What is the best software for project management?"
  ],
  "page_related_searches": [
    "Project management software free",
    "Top 10 project management tools"
  ],
  "page_has_ai_overview": true,
  "page_ai_overview": "Project management software helps teams plan, track, collaborate on, and deliver projects from start to finish.Asana: Best for marketing,...",
  "page_ai_overview_sources": [
    "https://www.teamwork.com/blog/best-project-management-tools/",
    "https://www.reddit.com/r/projectmanagement/comments/1r7dr5i/project_management_tools_ranked_comparison_table/"
  ],
  "change_type": "new_entry",
  "magnitude": "unknown",
  "why_it_matters": "Newly ranking for this keyword."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-search-results-scraper").call(run_input={
    "keywords": [
        "running shoes",
        "project management software"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-search-results-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["running shoes", "project management software"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-search-results-scraper` as a tool.

Full documentation, pricing and the latest changes: [Google Search Results Scraper - Rankings, SERP, Position](https://apify.com/om_kh/google-search-results-scraper).

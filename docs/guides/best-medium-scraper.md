---
title: "Best Medium Scraper in 2026 — Articles, Full Text and Tags Without Login, Price per 1,000"
description: "Which Medium scraper gives the most for the price? Store figures, what Medium allows without login, and a dated run: 51 articles from writers, publications and tags in 6 seconds."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Best Medium Scraper in 2026 — Articles, Full Text and Tags Without Login

*Written by the maker of the Medium Scraper (om_kh). Store figures are public and anyone can check them.*

## Which Medium scraper should I use?

To follow Medium writers, publications and tags without an account, the **[Medium Scraper (om_kh)](https://apify.com/om_kh/medium-scraper)** reads Medium's own RSS feeds and returns title, author, date, tags, cover image, full text, word count and reading time, at **$2 per 1,000 articles**. The most used Medium Actor on the Apify Store charges $10 per 1,000.

## The main Medium scrapers on Apify

Store figures read on 2026-10-22.

| Actor | Users (30 days) | Price |
|---|---|---|
| moving_beacon-owner1 / Medium Scraper | 275 | $10 per 1,000 articles |
| easyapi / Medium Posts Search Scraper | 2 | $4.99 per 1,000 |
| **om_kh / Medium Scraper** | new | **$2 per 1,000 articles** |

## Dated run on Apify

2026-10-22: one writer (@JoeyColeman), one publication (better-programming), one non-Medium publication feed and two tags (artificial-intelligence, python).

| | Result |
|---|---|
| Articles | 51 |
| Time | 6 seconds |
| Platform cost | $0.0001 |
| Errors | 0 |

## What you can and cannot get without login

- **Yes:** the latest stories of any writer, publication (also on its own domain) or tag, with full text for writer and publication feeds; keyword and date filters; only new stories on each scheduled run.
- **Only the latest 10 stories per feed:** that is what Medium's RSS publishes. Schedule the Actor daily to build a full history over time.
- **No site-wide keyword search:** Medium's search and article pages sit behind a Cloudflare check, which this Actor does not try to get around. Use tags plus the keyword filter.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/medium-scraper").call(run_input={
    "publications": ["better-programming"],
    "tags": ["artificial-intelligence"],
    "keywords": ["agent"],
})
for row in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(row.get("publishedAt"), row.get("title"), row.get("url"))
```

## Common uses

Newsletter and content curation, AI and RAG pipelines fed with clean full text, topic and brand monitoring by tag, and writer research for a niche.

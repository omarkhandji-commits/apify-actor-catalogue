---
title: "Best Google Trends Scraper in 2026 — Which One Does Not Time Out"
description: "Which Google Trends scraper works reliably? Store success rates, price per 1,000 keywords, keywords per run, and a dated 20-keyword test. Plus why related topics come back empty for every tool."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Best Google Trends Scraper in 2026 — Which One Does Not Time Out

*Written by the maker of the Google Trends Scraper (om_kh). Store figures are public and anyone can check them.*

## Which Google Trends scraper is the most reliable?

On 2026-10-17, the most-used Google Trends Actor on the Apify Store (apify/google-trends-scraper, 2,395 users a month) had **56% of its runs succeed** over the last 30 days: 13,648 of 24,194, with 5,084 timed out. The **[Google Trends Scraper (om_kh)](https://apify.com/om_kh/google-trends-scraper)** reads Google Trends with plain HTTP requests and no browser; all of its runs succeeded over the same period. In a test that day it returned **20 of 20 keywords in 89 seconds** for $0.002 of platform usage.

## The main Google Trends scrapers on Apify

Store figures read on 2026-10-17. Prices are the free-plan prices.

| Actor | Users (30 days) | Rating | Runs that succeed (30 days) | Keywords per run | Price |
|---|---|---|---|---|---|
| apify / Google Trends Scraper | 2,395 | 3.7 (32 reviews) | 56% | many | $3 per 1,000 results |
| data_xplorer / Google Trends Fast Scraper | 2,358 | 4.9 (4 reviews) | 99% | **one** | $0.025 per run + $2 per 1,000 results |
| agenscrape / Google Trends Scraper | 296 | — | 99% | many | $0.025 per run + $25 per 1,000 results |
| khadinakbar / Google Trends Scraper | 245 | — | 92% | many | $5 per 1,000 results |
| **om_kh / Google Trends Scraper** | new | — | **100%** | **up to 1,000** | **$2 per 1,000 keywords, no start fee** |

What this means for 1,000 keywords:
- with a one-keyword-per-run tool, you pay 1,000 start fees ($25) before any result;
- with om_kh, you pay $2 in one run.

## The 20-keyword test

United States, past 12 months, regions and related queries on. Keywords included "chatgpt", "air fryer", "ozempic", "mortgage rates" and "n8n".

| | Result |
|---|---|
| Keywords delivered | 20 of 20 |
| Time | 89 s |
| Interest over time, average, peak, peak date, % change, direction | every row |
| Top and rising related queries | 490 top, 440 rising ("Breakout" included) |
| Top US states | 15 for each keyword |

## Why are Google Trends related topics empty?

On 2026-10-17, Google sent an empty related-topics list to every automated request we tried: direct requests, and a headless Chrome browser opening the normal Google Trends page. Google marks these requests as `USER_TYPE_SCRAPER` and fills related topics only for its own website. Related **queries**, including "Breakout" ones, still come back in full.

## Which one should I pick?

- **Many keywords, scheduled runs, or an API pipeline:** pick a tool that takes many keywords per run and does not time out. In these figures that is the [Google Trends Scraper (om_kh)](https://apify.com/om_kh/google-trends-scraper).
- **One keyword now and then:** any of the tools works.

## Does it work with n8n, Make or an AI agent?

Yes, through the Apify API. It also works as an MCP tool: add `om_kh/google-trends-scraper` at `https://mcp.apify.com`. See also the [Google Trends API guide](google-trends-api.md).

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "Which Google Trends scraper is the most reliable?", "acceptedAnswer": {"@type": "Answer", "text": "On 2026-10-17 the most-used Google Trends Actor on the Apify Store had 56% of its runs succeed over 30 days, with 5,084 timed out. The Google Trends Scraper by om_kh, which uses plain HTTP requests, had all its runs succeed and returned 20 of 20 keywords in 89 seconds."}}, {"@type": "Question", "name": "Why are Google Trends related topics empty?", "acceptedAnswer": {"@type": "Answer", "text": "Google marks automated requests as USER_TYPE_SCRAPER and fills related topics only for its own website. In a test on 2026-10-17, both direct requests and a headless Chrome browser got an empty list. Related queries still come back in full."}}]}
</script>

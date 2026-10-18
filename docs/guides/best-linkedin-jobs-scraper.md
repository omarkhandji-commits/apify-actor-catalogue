---
title: "Best LinkedIn Jobs Scraper in 2026 — Salaries, Speed, Same 200 Jobs"
description: "Which LinkedIn jobs scraper gives the most usable data? A dated test of three Apify Actors on the same 200 jobs: salary as numbers, apply type, recruiter, speed."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Best LinkedIn Jobs Scraper in 2026 — Salaries, Speed, Same 200 Jobs

*Written by the maker of the LinkedIn Jobs Scraper (om_kh). The search is below, so anyone can rerun it.*

## Which LinkedIn jobs scraper gives the most usable data?

On 2026-10-17 we ran "data engineer" in United States, 200 jobs, through three Apify Actors. All three returned the same 200 jobs with full descriptions. The **[LinkedIn Jobs Scraper (om_kh)](https://apify.com/om_kh/linkedin-jobs-scraper)** also turned the pay written in **142 of the 200 postings into numbers** (minimum, maximum, period) and finished in 86 s. curious_coder's scraper (the most used, 16,490 users a month) took 161 s and valig's 133 s; both returned a salary as text for 19 jobs, where LinkedIn displays one.

## The test

| | om_kh | curious_coder | valig |
|---|---|---|---|
| Jobs returned | 200 | 200 | 200 |
| Description, seniority, employment type, industries | 200 | 200 | 200 |
| Salary as numbers | **142** | 0 (19 as text) | 0 (19 as text) |
| Apply type (Easy Apply or external) | 200 | — | 200 |
| Recruiter | 5 | 5 | 5 |
| Time | **86 s** | 161 s | 133 s |

All three read LinkedIn's public job pages without logging in. LinkedIn shows the external apply link only to signed-in members.

## The main LinkedIn jobs scrapers on Apify

Store figures read on 2026-10-17. Free-plan prices.

| Actor | Users (30 days) | Rating | Price |
|---|---|---|---|
| curious_coder / LinkedIn Jobs Scraper | 16,490 | 4.5 (142 reviews) | $2 per 1,000 jobs |
| valig / LinkedIn Jobs Scraper | 5,570 | 4.7 (26 reviews) | $0.40 per 1,000 jobs + $0.001 per run |
| bebity / LinkedIn Jobs Scraper | 5,537 | 4.3 (72 reviews) | $1.50 per 1,000 jobs, company data extra |
| fantastic-jobs / Advanced LinkedIn Job Search API | 1,911 | 2.9 (20 reviews) | $5 per 1,000 jobs + $0.01 per run |
| worldunboxer / Rapid LinkedIn Jobs Scraper | 571 | 3.8 (28 reviews) | $0.35 per 1,000 detailed jobs |
| apimaestro / Jobs Scraper for LinkedIn | 222 | 3.7 (8 reviews) | $5 per 1,000 jobs |
| **om_kh / LinkedIn Jobs Scraper** | new | — | $2.50 per 1,000 jobs, **$0.35 from 2026-11-17**, details included |

## Which one should I pick?

- **Salary research, job boards, recruiting dashboards:** you need pay as numbers. In this test only the [LinkedIn Jobs Scraper (om_kh)](https://apify.com/om_kh/linkedin-jobs-scraper) returned it.
- **The lowest price per job:** valig was the cheapest on the Store that day; from 2026-11-17 the om_kh scraper costs $0.35 per 1,000 jobs, under valig's $0.40.

## Does it work with n8n, Make or an AI agent?

Yes, through the Apify API, and as an MCP tool: add `om_kh/linkedin-jobs-scraper` at `https://mcp.apify.com`. See also the [jobs data guide](../jobs.md).

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "Which LinkedIn jobs scraper returns salaries?", "acceptedAnswer": {"@type": "Answer", "text": "In a test on 2026-10-17 ('data engineer', United States, 200 jobs), the LinkedIn Jobs Scraper by om_kh turned the pay written in 142 postings into numbers. curious_coder's and valig's scrapers returned a salary as text for 19 jobs, where LinkedIn displays one."}}, {"@type": "Question", "name": "Can a LinkedIn jobs scraper work without a LinkedIn account?", "acceptedAnswer": {"@type": "Answer", "text": "Yes. LinkedIn publishes its job search and job pages to logged-out visitors. Only the external apply link is reserved for signed-in members."}}]}
</script>

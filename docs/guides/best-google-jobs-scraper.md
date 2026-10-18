---
title: "Best Google Jobs Scraper in 2026 — Tested on the Same Search"
description: "Which Google Jobs scraper returns the most usable job data? A dated test on the same search: salary as numbers, posted date, apply links, location accuracy, speed and price."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Best Google Jobs Scraper in 2026 — Tested on the Same Search

*Written by the maker of the Google Jobs Scraper (om_kh). Anyone can rerun the search below.*

## Which Google Jobs scraper gives the most usable data?

On 2026-10-17 we ran "software engineer" in New York, NY, for 30 jobs, through two working scrapers. The **[Google Jobs Scraper (om_kh)](https://apify.com/om_kh/google-jobs-scraper)** returned **16 of 30 jobs with a salary as numbers** and **23 with a posted date**, for $2.50 per 1,000 jobs on a paid plan. **johnvc's Google Jobs Scraper** returned the same 30 jobs count with no structured salary and no posted date, for $4.50 per 1,000 jobs ($0.045 per page of 10). The Store's first result, epctex's scraper, had 0% of its runs succeed over the last 30 days.

## The test

| | Google Jobs Scraper (om_kh) | johnvc Google Jobs Scraper |
|---|---|---|
| Jobs returned | 30 | 30 |
| Salary as numbers (min / max / period) | **16 of 30** | 0 (salary only inside the text) |
| Posted date | **23 of 30** | 0 |
| Apply links | 30 of 30 | 30 of 30 |
| In the searched city | 27, plus 1 suburb and 2 with no place | 20, the rest nearby |
| Price per 1,000 jobs on a paid plan | **$2.50** | $4.50 |
| Time | 64 s | **25 s** |

How the 16 salaries were found:
- 10 come from Google's own salary tag;
- 6 come from the pay written in the posting itself, such as "Base Salary Range $137,100—$201,600". The field `salarySource` says which.

A second search, "registered nurse" in Houston, TX, gave 30 jobs: 10 with a salary, 23 with a posted date, and all in Texas.

## The main Google Jobs scrapers on Apify

Store figures read on 2026-10-17.

| Actor | Users (30 days) | Rating | Runs that succeed (30 days) |
|---|---|---|---|
| epctex / Google Jobs Scraper | 100 | 2.9 (13 reviews) | 0% |
| johnvc / Google Jobs Scraper | 458 | 4.5 (13 reviews) | 91% |
| orgupdate / Google Jobs Scraper | 96 | 4.6 (2 reviews) | 93% |
| johnvc / Google Jobs Scraper (pay per result) | 94 | 5.0 (2 reviews) | 98% |
| **om_kh / Google Jobs Scraper** | new | — | 100% |

## Which one should I pick?

- **Salary analysis, job-market research or recruiting leads:** pick the one that turns salaries and dates into fields. In this test that was the [Google Jobs Scraper (om_kh)](https://apify.com/om_kh/google-jobs-scraper), at about half the price per job.
- **Raw speed on a single page:** johnvc's scraper finished in 25 s, against our 64 s. We read more pages so that every job is in the place you asked for.

## Does it work with n8n, Make or an AI agent?

Yes, through the Apify API. It also works as an MCP tool: add `om_kh/google-jobs-scraper` at `https://mcp.apify.com`.

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "Which Google Jobs scraper gives the most usable data?", "acceptedAnswer": {"@type": "Answer", "text": "On 2026-10-17, for 'software engineer' in New York (30 jobs), the Google Jobs Scraper by om_kh returned 16 jobs with a salary as numbers and 23 with a posted date, at $2.50 per 1,000 jobs on a paid plan. johnvc's scraper returned no structured salary and no posted date, at $4.50 per 1,000 jobs."}}, {"@type": "Question", "name": "Does Google Jobs show salaries?", "acceptedAnswer": {"@type": "Answer", "text": "For some postings Google shows a salary tag. Others write the pay inside the description. In the test, 10 of 30 jobs had a Google salary tag and 6 more had the pay in their text."}}]}
</script>

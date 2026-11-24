[← Catalogue home](index.md)

# Jobs & Hiring data

## What problem this solves

Getting current job openings — or knowing when a company's hiring activity changes — usually means either scraping a career page yourself or paying for an expensive HR-tech data feed. This family pulls live job listings straight from a company's career page or its underlying applicant tracking system (ATS: Greenhouse, Lever, Ashby, Workday), and layers hiring-signal intelligence on top.

## New on 2026-10-28: more facts than the market leader, at a fraction of its price

ATS Jobs API, Company Careers Page Scraper and Google Jobs Scraper now return on every job, read by rules at no extra cost: contract type (full-time, part-time, contract, internship...), remote / hybrid / on-site with office days, city, region and country as separate fields, salary as numbers with its pay period and a yearly equivalent, benefits, the posting's language, contact emails written in the posting, a staffing-agency flag, and (ATS and careers) the company's website, logo and number of open roles.

New filters, applied before you pay: contract type, work arrangement, countries, title words, companies, places and departments to exclude, staffing agencies, only jobs with a salary, minimum yearly salary. And an **only new jobs since my last run** switch for daily or hourly schedules: jobs already delivered are never charged again.

| Per job | ATS Jobs API / Careers | Google Jobs Scraper | Career-site leader | Google Jobs leader |
| --- | --- | --- | --- | --- |
| Price | $0.0015 | $0.003 | $0.012 | up to $0.009 |

## When to use it

- You have a **list of companies** (by domain) and want their current openings.
- You have a **specific ATS board** (Greenhouse/Lever/Ashby/Workday) and want just that provider.
- You want a **hiring-trend signal** (first sales hire, hiring freeze, exec hire) rather than raw listings.
- You want **LinkedIn's or Indeed's own listings** as a second, independent source.

## Actors in this family

| Actor | Best for | Pricing |
|---|---|---|
| [Career Site Job Listing API](https://apify.com/om_kh/careers-page-scraper) | Any company, ATS auto-detected from just the domain or a job-board link (74 systems, incl. Phenom and Radancy sites of big employers), or search all companies at once by keyword, with full job description, salary and apply link | **$2.50 per 1,000 jobs** + $0.005 per run ($2.13 to $1.38 on paid plans) |
| [ATS Jobs Search API](https://apify.com/om_kh/ats-jobs-api) | Querying 74 ATS providers (Greenhouse, Lever, Ashby, Workday, Recruitee, Workable...) in one call, with full job description, salary and skills | $1.50 per 1,000 jobs (down to $0.90 on larger Apify plans), + $0.001 per run |
| [Greenhouse Job Listings API](https://apify.com/om_kh/greenhouse-jobs-api) | You already know it's a Greenhouse board; full description, salary and skills included | $1.50 per 1,000 jobs + $0.001 per run |
| [Lever.co Jobs API](https://apify.com/om_kh/lever-jobs-api) | You already know it's a Lever board; full description, salary and skills included | $1.50 per 1,000 jobs + $0.001 per run |
| [Ashby Jobs API](https://apify.com/om_kh/ashby-jobs-api) | You already know it's an Ashby board; full description, salary and skills included | $1.50 per 1,000 jobs + $0.001 per run |
| [Workday Jobs API](https://apify.com/om_kh/workday-jobs-api) | You already know it's a Workday tenant | $0.10 per 1,000 jobs + $0.001 per run (from Nov 24, 2026) |
| [Hiring Signals](https://apify.com/om_kh/company-hiring-signals) | Trend/change detection instead of raw listings | $0.005 per company checked (was $0.02 until 20 November 2026) + $0.001 per run, even when nothing changed (the check is the work) |
| [LinkedIn Jobs Scraper](https://apify.com/om_kh/linkedin-jobs-scraper) | LinkedIn search by keywords and place, no login: description, applicants, apply type, salary as numbers | $0.35 per 1,000 jobs, no start fee, no monitoring fee |
| [Indeed Jobs Scraper](https://apify.com/om_kh/indeed-jobs-scraper) | Indeed's own postings, a second source | **$0.30 per 1,000 jobs** + $0.001 per run |

## Telling the siblings apart

The four single-provider Actors (Greenhouse/Lever/Ashby/Workday) do exactly one ATS each — use them when you already know which one a company runs. **ATS Jobs Search API** is the multi-provider version of the same idea: one call across several boards. **Career Site Job Listing API** goes one level up — give it a bare company domain and it auto-detects the ATS for you, so you don't need to know it at all. **Hiring Signals** doesn't return job listings; it returns a *change* ("first sales hire this week," "hiring freeze") derived from watching listings over time. **LinkedIn** and **Indeed** are independent sources, not ATS boards — useful for postings a company's own career page doesn't list.

## Recommended starting point

[**Career Site Job Listing API**](https://apify.com/om_kh/careers-page-scraper) — works from just a company domain, no need to know the ATS. Try it: [live example (Stripe)](https://apify.com/om_kh/careers-page-scraper/examples/careers-page-scraper-single-company).

## Workflow example

See [Get current jobs from a company without knowing its ATS](examples/jobs-example.md) for the full walkthrough (domain → jobs → optional hiring-signal layer).

## Related family

Found a hiring company you want to reach? See [Leads & Verification](leads-verification.md) to turn a company domain into a verified contact email.

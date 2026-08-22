[← Catalogue home](index.md)

# Jobs & Hiring data

## What problem this solves

Getting current job openings — or knowing when a company's hiring activity changes — usually means either scraping a career page yourself or paying for an expensive HR-tech data feed. This family pulls live job listings straight from a company's career page or its underlying applicant tracking system (ATS: Greenhouse, Lever, Ashby, Workday), and layers hiring-signal intelligence on top.

## When to use it

- You have a **list of companies** (by domain) and want their current openings.
- You have a **specific ATS board** (Greenhouse/Lever/Ashby/Workday) and want just that provider.
- You want a **hiring-trend signal** (first sales hire, hiring freeze, exec hire) rather than raw listings.
- You want **LinkedIn's or Indeed's own listings** as a second, independent source.

## Actors in this family

| Actor | Best for | Pricing |
|---|---|---|
| [Career Site Job Listing API](https://apify.com/om_kh/careers-page-scraper) | Any company, ATS auto-detected from just the domain | 3 free, then per listing |
| [ATS Jobs Search API](https://apify.com/om_kh/ats-jobs-api) | Querying multiple ATS providers (Greenhouse + Lever, etc.) in one call | $2/1K |
| [Greenhouse Job Listings API](https://apify.com/om_kh/greenhouse-jobs-api) | You already know it's a Greenhouse board | $2/1K |
| [Lever.co Jobs API](https://apify.com/om_kh/lever-jobs-api) | You already know it's a Lever board | $2/1K |
| [Ashby Jobs API](https://apify.com/om_kh/ashby-jobs-api) | You already know it's an Ashby board | $2/1K |
| [Workday Jobs API](https://apify.com/om_kh/workday-jobs-api) | You already know it's a Workday tenant | $2/1K |
| [Hiring Signals](https://apify.com/om_kh/company-hiring-signals) | Trend/change detection instead of raw listings | $0.02/company |
| [LinkedIn Jobs Scraper](https://apify.com/om_kh/vigia-linkedin-jobs-monitor) | LinkedIn's own postings, a second source | $0.06 + $0.01 |
| [Indeed Jobs Scraper](https://apify.com/om_kh/vigia-indeed-hiring-monitor) | Indeed's own postings, a second source | $0.05 + $8/1K |

## Telling the siblings apart

The four single-provider Actors (Greenhouse/Lever/Ashby/Workday) do exactly one ATS each — use them when you already know which one a company runs. **ATS Jobs Search API** is the multi-provider version of the same idea: one call across several boards. **Career Site Job Listing API** goes one level up — give it a bare company domain and it auto-detects the ATS for you, so you don't need to know it at all. **Hiring Signals** doesn't return job listings; it returns a *change* ("first sales hire this week," "hiring freeze") derived from watching listings over time. **LinkedIn** and **Indeed** are independent sources, not ATS boards — useful for postings a company's own career page doesn't list.

## Recommended starting point

[**Career Site Job Listing API**](https://apify.com/om_kh/careers-page-scraper) — works from just a company domain, no need to know the ATS. Try it: [live example (Stripe)](https://apify.com/om_kh/careers-page-scraper/examples/careers-page-scraper-single-company).

## Workflow example

See [Get current jobs from a company without knowing its ATS](../examples/jobs-example.md) for the full walkthrough (domain → jobs → optional hiring-signal layer).

## Related family

Found a hiring company you want to reach? See [Leads & Verification](leads-verification.md) to turn a company domain into a verified contact email.

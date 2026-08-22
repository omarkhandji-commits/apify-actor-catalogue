[← Catalogue home](index.md) · [Local Business family](local-business.md)

# Automate local business intelligence with Apify

Finding local businesses, watching for newly-opened ones, catching a listing's unanswered public questions, and tracking home-listing price changes — then turning any of that into a qualified contact — usually means stitching together several manual checks. This guide covers the whole Local/Maps family as one connected workflow, not four separate tools.

## The Actors

| Actor | Job | Public Task |
|---|---|---|
| [Google Maps Business Scraper](https://apify.com/om_kh/vigia-local-business-monitor) | Discover the current full set of businesses for a category+area | [single search](https://apify.com/om_kh/vigia-local-business-monitor/examples/vigia-local-business-monitor-quickstart) · [multi-location](https://apify.com/om_kh/vigia-local-business-monitor/examples/vigia-local-business-monitor-multi-location) |
| [Google Maps New Business Scraper](https://apify.com/om_kh/vigia-maps-new-business-monitor) | Report only businesses newly detected since your last check | [quickstart](https://apify.com/om_kh/vigia-maps-new-business-monitor/examples/vigia-maps-new-business-monitor-quickstart) |
| [Google Business Profile Q&A Scraper](https://apify.com/om_kh/vigia-gbp-qa-monitor) | Catch new unanswered public questions on a listing | [quickstart](https://apify.com/om_kh/vigia-gbp-qa-monitor/examples/vigia-gbp-qa-monitor-quickstart) |
| [Zillow Listings Scraper](https://apify.com/om_kh/vigia-zillow-realestate-monitor) | Home listings, price/status delta | [quickstart](https://apify.com/om_kh/vigia-zillow-realestate-monitor/examples/vigia-zillow-realestate-monitor-quickstart) |

## 1. Discover businesses

Start with **Google Maps Business Scraper** for the full current picture of a category+area. Two Task shapes exist depending on scope: a single search, or [multiple locations in one run](https://apify.com/om_kh/vigia-local-business-monitor/examples/vigia-local-business-monitor-multi-location) for teams tracking a franchise or several competitors at once.

## 2. Track newly-detected businesses

**Google Maps New Business Scraper** answers a different question: not "what exists," but "what's new since I last checked." With `monitorEnabled: true`, the first run silently establishes a baseline (no false "new" claims), and every run after that reports only genuinely new listings — the Actor already does this delta computation, so no external diffing logic is needed downstream.

## 3. Catch what a listing's audience is asking

**Google Business Profile Q&A Scraper** watches a specific listing's public Q&A tab — a channel where a slow response visibly costs a business a lead.

## 4. Track a different vertical: real estate

**Zillow Listings Scraper** covers home listings rather than businesses, with the same price/status-delta pattern as the business Actors above.

## 5. Automate delivery

All four Actors are built to run on a schedule and hand off their output, not just produce a one-time dump:

- **n8n**: 4 individual workflows plus one flagship multi-Actor pipeline — see [`docs/workflows/n8n/`](workflows/n8n/). Import any `.json` file directly into n8n (Workflows → Import from File).
- **Make**: the same 5 workflows, as ready-to-recreate module specs — see [`docs/workflows/make/README.md`](workflows/make/README.md).
- **API/Postman**: one shared collection covering all 4 Actors plus the qualification step — see [`docs/workflows/postman/`](workflows/postman/).

## The flagship workflow: discover → monitor → qualify

The strongest automation in this family chains three Actors end to end:

```
Google Maps New Business Scraper (new listings, delta already computed)
        ↓  (only businesses with a public website)
Business Email Finder & Verifier (verified contact email)
        ↓
Google Sheets (ready-to-work lead list, updated daily)
```

This is [`docs/workflows/n8n/flagship-local-lead-pipeline.json`](workflows/n8n/flagship-local-lead-pipeline.json) — 4 nodes total. Each Actor already does its own hard part (delta detection, email verification), so the workflow itself is orchestration, not custom logic. See the [Leads & Verification family](leads-verification.md) for the qualification Actor on its own.

## API example

```bash
curl "https://api.apify.com/v2/actor-tasks/om_kh~vigia-maps-new-business-monitor-quickstart/run-sync-get-dataset-items?token=$APIFY_TOKEN" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"searches": ["coffee shops in Austin, TX"], "maxPlacesPerSearch": 10, "monitorEnabled": true, "maxTotalChargeUsd": 1}'
```

## Agent / MCP

Natural-language requests this family's Actors already support: "find Google Maps businesses in Austin," "show new local businesses detected since my last check." No discovery ambiguity was found for any of these four Actors during review — the existing MCP tool descriptions already match these requests correctly.

## Related

- [Local Business family page](local-business.md) for the fuller sibling comparison
- [Leads & Verification](leads-verification.md) for the qualification step used in the flagship workflow
- [Workflow example: Find newly discovered local businesses and qualify them](examples/local-business-example.md)

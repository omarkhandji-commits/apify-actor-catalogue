[← Catalogue home](index.md)

# Reviews & Reputation monitoring

## What problem this solves

Reviews live scattered across a dozen platforms — Google, Yelp, Trustpilot, G2, TripAdvisor, Glassdoor, Amazon, app stores. This family pulls reviews from a specific platform as clean rows (rating, text, author, date), and a separate cleanup Actor handles deduplication and "what's new" detection once you have review data from any source.

## When to use it

- You need reviews from **one specific platform** for a business, product, or app.
- You want **reputation monitoring**: know when a new review lands, not just a one-time dump.
- You already have review exports (from any of these, or your own) and just need **dedup + new-review detection**.

## Actors in this family

| Actor | Source | Pricing |
|---|---|---|
| [Google Maps Reviews Scraper](https://apify.com/om_kh/vigia-google-review-monitor) | Google Maps listings | $0.05 + $0.02 |
| [Yelp Reviews Scraper](https://apify.com/om_kh/vigia-yelp-review-monitor) | Yelp business pages | $0.15 + $0.02 |
| [Trustpilot Reviews Scraper](https://apify.com/om_kh/vigia-trustpilot-review-monitor) | Trustpilot company pages | $0.06 + $0.02 |
| [G2 Software Reviews Scraper](https://apify.com/om_kh/vigia-g2-review-monitor) | G2 product pages (B2B software) | $0.15/run |
| [TripAdvisor Reviews Scraper](https://apify.com/om_kh/vigia-tripadvisor-review-monitor) | Hotels/restaurants/attractions | $0.05 + $0.02 |
| [Glassdoor Reviews Scraper](https://apify.com/om_kh/vigia-glassdoor-review-monitor) | Employer/workplace reviews | $0.20/run |
| [Amazon Reviews Scraper](https://apify.com/om_kh/vigia-amazon-review-intelligence) | Amazon product reviews, with a review-velocity flag | $0.45 + $0.02 |
| [App Store & Google Play Reviews Scraper](https://apify.com/om_kh/vigia-app-review-radar) | Mobile app reviews, both stores in one run | $0.03 + $0.02 |

Plus one companion utility, not a source:

| Actor | Purpose | Pricing |
|---|---|---|
| [Review Cleaner & Deduplicator](https://apify.com/om_kh/vigia-reviews-delta) | Feed it review data from anywhere; get back deduped rows + a "what's new" flag | $0.02 |

## Telling the siblings apart

Each platform Actor is scoped to exactly one source — pick the one matching where your business/product actually has reviews. None of them do deduplication *across* runs beyond their own monitor state; **Review Cleaner & Deduplicator** is the one to reach for when you already have a review export (from one of these, a CSV, or anywhere else) and just need it cleaned and diffed. It does not scrape anything itself.

## Recommended starting point

[**Google Maps Reviews Scraper**](https://apify.com/om_kh/vigia-google-review-monitor) — the broadest-coverage source (any business with a Google Maps listing). Try it: [live example](https://apify.com/om_kh/vigia-google-review-monitor/examples/vigia-google-review-monitor-quickstart).

## Workflow example

See [Monitor reviews and detect what changed](examples/reviews-example.md) for the full walkthrough (source Actor → Review Cleaner & Deduplicator).

## Related family

Reviews often come from the same listing as core business data — see [Local Business](local-business.md) for the Google Maps profile itself (address, hours, category).

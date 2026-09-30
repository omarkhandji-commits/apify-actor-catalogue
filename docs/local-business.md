[← Catalogue home](index.md)

# Local Business intelligence

## What problem this solves

Finding and monitoring local businesses on Google Maps — the full current set for a category+area, only what's newly appeared, or the public Q&A on a specific listing.

## When to use it

- You want the **current full set** of businesses matching a category+location.
- You only want **newly-appeared listings** since your last check (not a re-scrape of everything).
- You want a listing's **public Q&A tab**, not its profile data.
- You're monitoring **real estate listings** rather than businesses.

## Actors in this family

| Actor | Best for | Pricing |
|---|---|---|
| [Google Maps Business Scraper](https://apify.com/om_kh/google-maps-business-scraper) | Current full set of businesses for a category+area (or [multiple locations at once](https://apify.com/om_kh/google-maps-business-scraper/examples/vigia-local-business-monitor-multi-location)) | $0.009 / place change + $0.1 / source check |
| [Google Maps New Business Scraper](https://apify.com/om_kh/google-maps-new-business-scraper) | Only businesses newly detected since your last check | $0.01 / new business alert + $0.08 / monitored subject re-checked |
| [Google Business Profile Q&A Scraper](https://apify.com/om_kh/google-business-profile-qa-scraper) | Public questions asked on a listing | $0.015 / unanswered question alert + $0.03 / monitored subject re-checked |
| [Zillow Listings Scraper](https://apify.com/om_kh/zillow-listings-scraper) | Home listings, price/status changes | $0.01 / listing change + $0.18 / monitored subject re-checked |

## Telling the siblings apart

**Google Maps Business Scraper** gives you *everything currently matching* your search — the discovery tool. **Google Maps New Business Scraper** answers a different question: what's *new since last time* — the monitoring tool, built for lead generation where a fresh listing matters more than the full set. **Google Business Profile Q&A Scraper** is scoped to one specific listing's public Q&A tab, not the broader business data. **Zillow Listings Scraper** covers a different vertical entirely (residential real estate, not businesses).

## Recommended starting point

[**Google Maps Business Scraper**](https://apify.com/om_kh/google-maps-business-scraper) for discovery, or go straight to [**Google Maps New Business Scraper**](https://apify.com/om_kh/google-maps-new-business-scraper) if you specifically want new-listing alerts. Try it: [live example (coffee shops, Austin TX)](https://apify.com/om_kh/google-maps-new-business-scraper/examples/vigia-maps-new-business-monitor-quickstart).

## Workflow example

See [Find newly discovered local businesses and qualify them](examples/local-business-example.md) for the full walkthrough (discovery → new-business monitoring → contact qualification).

## Automation examples

This is the fleet's most automated family: [Automate local business intelligence with Apify](automate-local-business-intelligence.md) covers all four Actors together, including the flagship discover → monitor → qualify pipeline, with ready-to-import [n8n workflows](workflows/n8n/), [Make scenario specs](workflows/make/README.md), and a shared [Postman collection](workflows/postman/local-maps-collection.json).

## Related family

Once you've found a business worth contacting, see [Leads & Verification](leads-verification.md) to qualify a real contact email for it. Want its reviews too? See [Reviews & Reputation](reviews-reputation.md).

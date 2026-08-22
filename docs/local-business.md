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
| [Google Maps Business Scraper](https://apify.com/om_kh/vigia-local-business-monitor) | Current full set of businesses for a category+area | $0.10 + $9/1K, 10 free |
| [Google Maps New Business Scraper](https://apify.com/om_kh/vigia-maps-new-business-monitor) | Only businesses newly detected since your last check | $0.08 + $0.01 |
| [Google Business Profile Q&A Scraper](https://apify.com/om_kh/vigia-gbp-qa-monitor) | Public questions asked on a listing | $0.03 + $0.015 |
| [Zillow Listings Scraper](https://apify.com/om_kh/vigia-zillow-realestate-monitor) | Home listings, price/status changes | $0.18 + $0.01 |

## Telling the siblings apart

**Google Maps Business Scraper** gives you *everything currently matching* your search — the discovery tool. **Google Maps New Business Scraper** answers a different question: what's *new since last time* — the monitoring tool, built for lead generation where a fresh listing matters more than the full set. **Google Business Profile Q&A Scraper** is scoped to one specific listing's public Q&A tab, not the broader business data. **Zillow Listings Scraper** covers a different vertical entirely (residential real estate, not businesses).

## Recommended starting point

[**Google Maps Business Scraper**](https://apify.com/om_kh/vigia-local-business-monitor) for discovery, or go straight to [**Google Maps New Business Scraper**](https://apify.com/om_kh/vigia-maps-new-business-monitor) if you specifically want new-listing alerts. Try it: [live example (coffee shops, Austin TX)](https://apify.com/om_kh/vigia-maps-new-business-monitor/examples/vigia-maps-new-business-monitor-quickstart).

## Workflow example

See [Find newly discovered local businesses and qualify them](examples/local-business-example.md) for the full walkthrough (discovery → new-business monitoring → contact qualification).

## Related family

Once you've found a business worth contacting, see [Leads & Verification](leads-verification.md) to qualify a real contact email for it. Want its reviews too? See [Reviews & Reputation](reviews-reputation.md).

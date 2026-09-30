[← Catalogue home](index.md)

# Ads & Competitive Intelligence

## What problem this solves

Seeing what a competitor is currently advertising — and, more usefully, what changed: which creatives are new, which disappeared.

## When to use it

- You want a competitor's **current ads** from Facebook's Ads Library or Google's Ads Transparency Center.
- You want to know **what changed** since your last pull — new, removed, or edited creatives — not just today's snapshot.

## Actors in this family

| Actor | Best for | Pricing |
|---|---|---|
| [Facebook Ads Library Scraper](https://apify.com/om_kh/facebook-ads-library-scraper) | Current Facebook/Instagram ad creatives for a Page | $0.02 / actionable ad change + $0.45 / monitored subject re-checked |
| [Google Ads Transparency Scraper](https://apify.com/om_kh/google-ads-transparency-scraper) | Current Google ad creatives for an advertiser | $0.02 / actionable ad change + $0.1 / monitored subject re-checked |
| [Ad Creative Change Detector](https://apify.com/om_kh/facebook-ad-creative-tracker) | Diff two ad-data snapshots — new/removed/changed | $0.02 / actionable ad change |

## Telling the siblings apart

**Facebook Ads Library Scraper** and **Google Ads Transparency Scraper** each pull current ads from one specific source. **Ad Creative Change Detector** doesn't scrape anything — it's a diff utility: feed it two snapshots (from either of the above, or your own data) and it returns exactly what changed. Use the source Actors first if you don't have current ad data yet.

## Recommended starting point

[**Facebook Ads Library Scraper**](https://apify.com/om_kh/facebook-ads-library-scraper) to get current ads, then [**Ad Creative Change Detector**](https://apify.com/om_kh/facebook-ad-creative-tracker) once you have two runs to compare. Try it: [live example](https://apify.com/om_kh/facebook-ads-library-scraper/examples/vigia-ads-library-monitor-quickstart).

## Workflow example

See [Track new and removed competitor ad creatives](examples/ads-example.md) for the full walkthrough.

## Related family

Also tracking a competitor's hiring or product launches? See [Jobs & Hiring](jobs.md) and [News & Community](news-community.md).

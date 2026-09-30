# om_kh Apify Actor Catalogue

Ready-to-run [Apify](https://apify.com) Actors for pulling and monitoring data that normally lives behind a browser: job boards, review sites, Google Maps, social platforms, YouTube, ad libraries, and e-commerce marketplaces. Every Actor is pay-per-result — you're billed for what actually changed or got delivered, not for the run.

**Start an Actor from your browser, an HTTP request, or an AI agent (MCP).** No infrastructure to run — Apify hosts everything, you just call it.

## Who this is for

- **Developers & automation builders** wiring data pulls into an app, workflow, or agent
- **Recruiters & talent teams** tracking job postings and hiring signals across ATS platforms
- **Researchers & analysts** monitoring reviews, forums, and social mentions
- **Agencies** doing local-business and reputation work for clients
- **Data teams** feeding e-commerce, ad, or competitive-intelligence pipelines

## What problems this solves

| Family | Problem it solves | Start here |
|---|---|---|
| [Jobs & Hiring](jobs.md) | Get current job listings or hiring signals for any company, across any ATS | [Career Site Job Listing API](https://apify.com/om_kh/careers-page-scraper) |
| [Reviews & Reputation](reviews-reputation.md) | Monitor reviews across review platforms, catch what's new | [Google Maps Reviews Scraper](https://apify.com/om_kh/google-maps-reviews-scraper) |
| [YouTube & Video](youtube-video.md) | Turn videos into transcripts and text for AI/RAG pipelines | [YouTube Transcript Scraper](https://apify.com/om_kh/youtube-transcript-api) |
| [Social Monitoring](social-monitoring.md) | Track accounts, keywords, and hashtags across social platforms | [X (Twitter) Search Scraper](https://apify.com/om_kh/twitter-x-search-scraper) |
| [Local Business](local-business.md) | Discover and monitor local businesses on Google Maps | [Google Maps Business Scraper](https://apify.com/om_kh/google-maps-business-scraper) |
| [Ecommerce & Pricing](ecommerce-pricing.md) | Track prices, stock, and marketplace listings | [Amazon Price & Stock Scraper](https://apify.com/om_kh/amazon-price-stock-tracker) |
| [Ads & Competitive Intel](ads-competitive-intelligence.md) | See what competitors are advertising, and what changed | [Facebook Ads Library Scraper](https://apify.com/om_kh/facebook-ads-library-scraper) |
| [News & Community](news-community.md) | Monitor Reddit, Hacker News, Stack Overflow, Product Hunt, Google News | [Reddit Posts & Comments Scraper](https://apify.com/om_kh/reddit-posts-comments-scraper) |
| [Leads & Verification](leads-verification.md) | Turn discovered businesses/companies into verified contacts | [Business Email Finder & Verifier](https://apify.com/om_kh/vigia-lead-quality-api) |

## New this month

- [Google Trends Scraper](https://apify.com/om_kh/google-trends-scraper) — interest over time, average / peak / % change, top regions, rising and **Breakout** queries, compare mode, and daily **Trending now** searches for any country. $0.002 per keyword.
- [YouTube Channel Search Scraper](https://apify.com/om_kh/youtube-channel-search-scraper) — find YouTube channels by keyword with subscriber filters; optional country, total views, social links and public business email. $0.0005 per channel.

**See every Actor with its current price: [All Actors](all-actors.md).**

## Guides

Answer-first guides with code: [YouTube transcript API](guides/youtube-transcript-api-python.md) · [Google Trends API](guides/google-trends-api.md) · [Find YouTube channels with email](guides/find-youtube-channels-with-email.md) · [Greenhouse / Lever / Workday jobs API](guides/greenhouse-lever-workday-jobs-api.md) · [Google News API](guides/google-news-api.md) · [Export YouTube comments](guides/export-youtube-comments.md) · [Export an Instagram following list](guides/export-instagram-following-list.md) · [New businesses on Google Maps](guides/new-businesses-google-maps.md) — [all guides](guides/index.md)

## Try a workflow, not just an Actor

- [Get current jobs from a company without knowing its ATS](examples/jobs-example.md)
- [Find newly discovered local businesses and qualify them](examples/local-business-example.md)
- [Monitor reviews and detect what changed](examples/reviews-example.md)
- [Turn YouTube videos into transcripts for AI workflows](examples/youtube-example.md)
- [Track new and removed competitor ad creatives](examples/ads-example.md)

## Automate a whole family

- [Automate local business intelligence with Apify](automate-local-business-intelligence.md) — discovery, new-business monitoring, Q&A alerts, and lead qualification, with ready-to-import n8n/Make/Postman assets.
- [Turn YouTube into text, at any scale](automate-youtube-transcripts.md) — get a transcript, feed it into AI/RAG, scale to a whole channel, or monitor for new uploads.

## Agent / MCP access

Several Actors in this catalogue also expose an [MCP](https://apify.com/mcp) tool, so an AI agent can call them directly from a natural-language request. For common asks like "get the transcript of this YouTube video" or "find current jobs from this company," the matching Actor is generally discoverable — see each family page for specifics.

## Running an Actor

Every Actor page on Apify has a **Try for free** button and a **Public Task** with a working example input already filled in. Family pages link to the strongest Public Task for that Actor where one exists.

---

Built and maintained by **[om_kh](https://apify.com/om_kh)** on Apify. [Repository home](../README.md).

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
| [Reviews & Reputation](reviews-reputation.md) | Monitor reviews across review platforms, catch what's new | [Google Maps Reviews Scraper](https://apify.com/om_kh/vigia-google-review-monitor) |
| [YouTube & Video](youtube-video.md) | Turn videos into transcripts and text for AI/RAG pipelines | [YouTube Transcript Scraper (free)](https://apify.com/om_kh/youtube-transcript-api) |
| [Social Monitoring](social-monitoring.md) | Track accounts, keywords, and hashtags across social platforms | [X (Twitter) Search Scraper](https://apify.com/om_kh/vigia-x-keyword-monitor) |
| [Local Business](local-business.md) | Discover and monitor local businesses on Google Maps | [Google Maps Business Scraper](https://apify.com/om_kh/vigia-local-business-monitor) |
| [Ecommerce & Pricing](ecommerce-pricing.md) | Track prices, stock, and marketplace listings | [Amazon Price & Stock Scraper](https://apify.com/om_kh/vigia-price-stock-delta) |
| [Ads & Competitive Intel](ads-competitive-intelligence.md) | See what competitors are advertising, and what changed | [Facebook Ads Library Scraper](https://apify.com/om_kh/vigia-ads-library-monitor) |
| [News & Community](news-community.md) | Monitor Reddit, Hacker News, Stack Overflow, Product Hunt, Google News | [Reddit Posts & Comments Scraper](https://apify.com/om_kh/vigia-reddit-brand-monitor) |
| [Leads & Verification](leads-verification.md) | Turn discovered businesses/companies into verified contacts | [Business Email Finder & Verifier](https://apify.com/om_kh/vigia-lead-quality-api) |

## Try a workflow, not just an Actor

- [Get current jobs from a company without knowing its ATS](examples/jobs-example.md)
- [Find newly discovered local businesses and qualify them](examples/local-business-example.md)
- [Monitor reviews and detect what changed](examples/reviews-example.md)
- [Turn YouTube videos into transcripts for AI workflows](examples/youtube-example.md)
- [Track new and removed competitor ad creatives](examples/ads-example.md)

## Automate a whole family

- [Automate local business intelligence with Apify](automate-local-business-intelligence.md) — discovery, new-business monitoring, Q&A alerts, and lead qualification, with ready-to-import n8n/Make/Postman assets.

## Agent / MCP access

Several Actors in this catalogue also expose an [MCP](https://apify.com/mcp) tool, so an AI agent can call them directly from a natural-language request. For common asks like "get the transcript of this YouTube video" or "find current jobs from this company," the matching Actor is generally discoverable — see each family page for specifics.

## Running an Actor

Every Actor page on Apify has a **Try for free** button and a **Public Task** with a working example input already filled in. Family pages link to the strongest Public Task for that Actor where one exists.

---

Built and maintained by **[om_kh](https://apify.com/om_kh)** on Apify. [Repository home](../README.md).

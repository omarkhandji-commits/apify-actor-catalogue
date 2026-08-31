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
| [Jobs & Hiring](docs/jobs.md) | Get current job listings or hiring signals for any company, across any ATS | [Career Site Job Listing API](https://apify.com/om_kh/careers-page-scraper) |
| [Reviews & Reputation](docs/reviews-reputation.md) | Monitor reviews across review platforms, catch what's new | [Google Maps Reviews Scraper](https://apify.com/om_kh/vigia-google-review-monitor) |
| [YouTube & Video](docs/youtube-video.md) | Turn videos into transcripts and text for AI/RAG pipelines | [YouTube Transcript Scraper (free)](https://apify.com/om_kh/youtube-transcript-api) |
| [Social Monitoring](docs/social-monitoring.md) | Track accounts, keywords, and hashtags across social platforms | [X (Twitter) Search Scraper](https://apify.com/om_kh/vigia-x-keyword-monitor) |
| [Local Business](docs/local-business.md) | Discover and monitor local businesses on Google Maps | [Google Maps Business Scraper](https://apify.com/om_kh/vigia-local-business-monitor) |
| [Ecommerce & Pricing](docs/ecommerce-pricing.md) | Track prices, stock, and marketplace listings | [Amazon Price & Stock Scraper](https://apify.com/om_kh/vigia-price-stock-delta) |
| [Ads & Competitive Intel](docs/ads-competitive-intelligence.md) | See what competitors are advertising, and what changed | [Facebook Ads Library Scraper](https://apify.com/om_kh/vigia-ads-library-monitor) |
| [News & Community](docs/news-community.md) | Monitor Reddit, Hacker News, Stack Overflow, Product Hunt, Google News | [Reddit Posts & Comments Scraper](https://apify.com/om_kh/vigia-reddit-brand-monitor) |
| [Leads & Verification](docs/leads-verification.md) | Turn discovered businesses/companies into verified contacts | [Business Email Finder & Verifier](https://apify.com/om_kh/vigia-lead-quality-api) |

## Try a workflow, not just an Actor

These walk through a real multi-step problem, start to finish:

- [Get current jobs from a company without knowing its ATS](docs/examples/jobs-example.md)
- [Find newly discovered local businesses and qualify them](docs/examples/local-business-example.md)
- [Monitor reviews and detect what changed](docs/examples/reviews-example.md)
- [Turn YouTube videos into transcripts for AI workflows](docs/examples/youtube-example.md)
- [Track new and removed competitor ad creatives](docs/examples/ads-example.md)

## Automate a whole family

- [Automate local business intelligence with Apify](docs/automate-local-business-intelligence.md) — discovery, new-business monitoring, Q&A alerts, and lead qualification, with ready-to-import n8n/Make/Postman assets.
- [Turn YouTube into text, at any scale](docs/automate-youtube-transcripts.md) — get a transcript, feed it into AI/RAG, scale to a whole channel, or monitor for new uploads.

## Agent / MCP access

Several Actors in this catalogue also expose an [MCP](https://apify.com/mcp) tool, so an AI agent can call them directly from a natural-language request instead of you writing the integration by hand. Not every request maps automatically — the agent still needs a tool description that matches your intent — but for common asks like:

- "Get the transcript of this YouTube video."
- "Find current jobs from this company."
- "Find Google Maps businesses in Austin."
- "Show new local businesses detected since my last check."

the matching Actor is generally discoverable. See each family page for the specific Actors that support this.

## Running an Actor

Every Actor page on Apify has a **Try for free** button (no code) and a **Public Task** with a working example input already filled in — the fastest way to see real output before you integrate anything. Family pages below link to the strongest Public Task for that Actor where one exists.

For programmatic access, see the code examples on each workflow page — minimal `curl` / Python / JavaScript snippets using your own `APIFY_TOKEN`.

## About

Built and maintained by **[om_kh](https://apify.com/om_kh)** on Apify. Questions or bug reports: use the **Issues** tab on the relevant Actor's Apify Store page.

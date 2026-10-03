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
| [Reviews & Reputation](docs/reviews-reputation.md) | Monitor reviews across review platforms, catch what's new | [Google Maps Reviews Scraper](https://apify.com/om_kh/google-maps-reviews-scraper) |
| [YouTube & Video](docs/youtube-video.md) | Turn videos into transcripts and text for AI/RAG pipelines | [YouTube Transcript Scraper](https://apify.com/om_kh/youtube-transcript-api) |
| [Social Monitoring](docs/social-monitoring.md) | Track accounts, keywords, and hashtags across social platforms | [X (Twitter) Search Scraper](https://apify.com/om_kh/twitter-x-search-scraper) |
| [Local Business](docs/local-business.md) | Discover and monitor local businesses on Google Maps | [Google Maps Business Scraper](https://apify.com/om_kh/google-maps-business-scraper) |
| [Ecommerce & Pricing](docs/ecommerce-pricing.md) | Track prices, stock, and marketplace listings | [Amazon Price & Stock Scraper](https://apify.com/om_kh/amazon-price-stock-tracker) |
| [Ads & Competitive Intel](docs/ads-competitive-intelligence.md) | See what competitors are advertising, and what changed | [Facebook Ads Library Scraper](https://apify.com/om_kh/facebook-ads-library-scraper) |
| [News & Community](docs/news-community.md) | Monitor Reddit, Hacker News, Stack Overflow, Product Hunt, Google News | [Reddit Posts & Comments Scraper](https://apify.com/om_kh/reddit-posts-comments-scraper) |
| [Leads & Verification](docs/leads-verification.md) | Turn discovered businesses/companies into verified contacts | [Business Email Finder & Verifier](https://apify.com/om_kh/vigia-lead-quality-api) |

## New this month

- [Google Jobs Scraper](https://apify.com/om_kh/google-jobs-scraper) — Google Jobs postings for any keyword and city (LinkedIn, Indeed, Glassdoor, career sites): title, company, location, **salary min/max**, posted date, full description and every apply link. $0.003 per job.
- [Google Hotels Scraper](https://apify.com/om_kh/google-hotels-scraper) — Google Hotels for any city and dates: nightly and total price, star class, rating, reviews, GPS, photos, plus optional **prices from every booking site** (Booking.com, Expedia, Agoda). $0.002 per property, $0.004 with every site's prices.
- [EU Tenders Scraper (TED)](https://apify.com/om_kh/eu-tenders-scraper) — EU public tenders from TED, the official procurement journal: open calls with deadline, value, buyer email and documents, plus contract awards with **winning companies**. Filter by keyword, country, CPV, date. $0.0015 per notice.
- [Craigslist Scraper](https://apify.com/om_kh/craigslist-scraper) — Craigslist listings from any city, category or search link: title, price, date, neighborhood, GPS, photos, optional description and attributes. Goes beyond the 360-result limit. $0.001 per listing, $0.0015 with details.
- [Substack Scraper](https://apify.com/om_kh/substack-scraper) — Substack newsletters and posts: subscriber count, paid prices, author socials, plus posts with likes, comments, restacks and optional full text. $0.002 per newsletter, $0.0005 per post, $0.001 per post with full text.
- [Telegram Channel Scraper](https://apify.com/om_kh/telegram-channel-scraper) — public Telegram channel posts with text, date, views, reactions, photos, links and forwards, plus channel title and subscriber count. No login, no phone. $0.0005 per post.
- [Snapchat Profile Scraper](https://apify.com/om_kh/snapchat-profile-scraper) — public Snapchat profiles: subscriber count, bio, website, emails in bio, verified badge, related accounts, plus every Spotlight video with views. $0.0015 per profile, $0.001 per Spotlight video.
- [Google Play Store Scraper](https://apify.com/om_kh/google-play-store-scraper) — Google Play apps by ID, URL or keyword: exact installs, rating histogram, reviews count, **developer email**, website, price, ads and in-app purchases. $0.0015 per app.
- [Truth Social Scraper](https://apify.com/om_kh/truth-social-scraper) — every post of public Truth Social accounts with text, date, replies, ReTruths, likes, media, hashtags and mentions, plus followers. $0.001 per post.
- [LinkedIn Ad Library Scraper](https://apify.com/om_kh/linkedin-ad-library-scraper) — ads from LinkedIn's public Ad Library by keyword, advertiser or country: full ad text, landing page, media, run dates, **impressions by country** and targeting. $0.001 per ad.
- [YouTube Channel Email Scraper](https://apify.com/om_kh/youtube-channel-email-scraper) — public business emails of YouTube channels from the bio or the creator's website, MX-checked, with socials and country. $0.004 per email found.
- [SEEK & JobStreet Jobs Scraper](https://apify.com/om_kh/seek-jobstreet-jobs-scraper) — jobs from SEEK (AU, NZ), JobStreet (MY, SG, ID, PH) and JobsDB (HK, TH) with parsed salary and company profile. $0.001 per job.
- [Kalshi & Polymarket Scraper](https://apify.com/om_kh/kalshi-polymarket-scraper) — live prediction-market odds from both exchanges in one table. $0.001 per market.
- [Google Trends Scraper](https://apify.com/om_kh/google-trends-scraper) — interest over time, average / peak / % change, top regions, rising and **Breakout** queries, compare mode, and daily **Trending now** searches for any country. $0.002 per keyword.
- [YouTube Channel Search Scraper](https://apify.com/om_kh/youtube-channel-search-scraper) — find YouTube channels by keyword with subscriber filters; optional country, total views, social links and public business email. $0.0005 per channel.

**See every Actor with its current price: [All Actors](docs/all-actors.md).**

## Guides

Answer-first guides with code: [YouTube transcript API](docs/guides/youtube-transcript-api-python.md) · [Google Trends API](docs/guides/google-trends-api.md) · [Find YouTube channels with email](docs/guides/find-youtube-channels-with-email.md) · [Greenhouse / Lever / Workday jobs API](docs/guides/greenhouse-lever-workday-jobs-api.md) · [Google News API](docs/guides/google-news-api.md) · [Export YouTube comments](docs/guides/export-youtube-comments.md) · [Export an Instagram following list](docs/guides/export-instagram-following-list.md) · [New businesses on Google Maps](docs/guides/new-businesses-google-maps.md) · [YouTube channel email finder](docs/guides/youtube-channel-email-finder.md) · [SEEK / JobStreet jobs API](docs/guides/seek-jobstreet-jobs-api.md) · [Kalshi / Polymarket API](docs/guides/kalshi-polymarket-api.md) — [all guides](docs/guides/index.md)

Free **n8n workflow templates** (Google Sheets, Slack): [docs/workflows](docs/workflows/index.md)

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

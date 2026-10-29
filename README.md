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


## Use these Actors from an AI agent (MCP)

Five ready-made remote MCP servers, listed in the official MCP Registry (`io.github.omarkhandji-commits/*`): jobs, travel and events, articles and AI models, YouTube, Asia shopping. Endpoints and client configs: [github.com/omarkhandji-commits/apify-data-mcp](https://github.com/omarkhandji-commits/apify-data-mcp). Example, travel: `https://mcp.apify.com/?tools=om_kh/flixbus-scraper,om_kh/google-hotels-scraper,om_kh/eventbrite-scraper`

## New this month

- [Redfin Scraper](https://apify.com/om_kh/redfin-scraper) — **every home for sale** in a Redfin city, county, neighborhood or ZIP code, plus rentals (Austin: 5,796 homes in one run): price, beds, baths, sq ft, HOA, days on market, photos, and **price per sq ft compared with the area median** to spot possible deals. Price, size, ZIP and keyword filters. $0.40 per 1,000 homes.
- [Civitai Scraper](https://apify.com/om_kh/civitai-scraper) — Civitai AI image models by **keyword, creator or tag**, filtered by type and **base model** (SDXL, Flux, Pony): downloads, likes, tips, **trigger words**, file size, download link and **licence**. First Civitai Actor on the Store, **$0.35 per 1,000 models**.
- [FlixBus Scraper](https://apify.com/om_kh/flixbus-scraper) — FlixBus and FlixTrain rides for **any route and date**: **price**, **seats left**, times, duration, stations, transfers and amenities, as a **90-day price calendar** with the cheapest ride of each day flagged. First FlixBus Actor on the Store, **$1 per 1,000 trips**.
- [HelloFresh Recipes Scraper](https://apify.com/om_kh/hellofresh-recipes-scraper) — HelloFresh recipes in **18 countries**: **ingredients with quantities**, **calories and nutrition**, allergens, steps, times, cuisine and rating, with time and calorie filters. First HelloFresh Actor on the Store, **$2 per 1,000 recipes**.
- [Medium Scraper](https://apify.com/om_kh/medium-scraper) — Medium articles from **writers, publications and tags**, many at once: title, author, date, tags, cover image, **full text**, word count and reading time; keyword and date filters, only-new mode for schedules. **$2 per 1,000 articles**, 5 times cheaper than the most used Medium Actor.
- [Google Jobs Scraper](https://apify.com/om_kh/google-jobs-scraper) — Google Jobs postings for any keyword and city (LinkedIn, Indeed, Glassdoor, career sites): title, company, location, **salary min/max**, posted date, full description and every apply link. $0.003 per job.
- [Eventbrite Scraper](https://apify.com/om_kh/eventbrite-scraper) — Eventbrite events for **any city or online**, by keyword or category, with date and free-only filters: date and time, venue, address, **GPS**, category and format, **ticket price range**, sold-out and sales status, and the **organizer's followers, website and social links**, plus optional organizer profile (events hosted, attendees, years on Eventbrite). $0.002 per event.
- [Google Hotels Scraper](https://apify.com/om_kh/google-hotels-scraper) — Google Hotels for any city and dates: nightly and total price, star class, rating, **review themes**, **amenities**, eco-certified flag, nearby places with travel times, GPS, photos, Google's own sort and filters (price, stars, amenities, free cancellation), plus optional **prices from every booking site** (Booking.com, Expedia, Agoda) with room rates, free-cancellation dates and sponsored flag. $0.002 per property, $0.004 with every site's prices.
- [EU Tenders Scraper (TED)](https://apify.com/om_kh/eu-tenders-scraper) — EU public tenders from TED, the official procurement journal: open calls with deadline, value, buyer email and documents, plus contract awards with **winning companies**. Filter by keyword, country, CPV, date. $0.0015 per notice.
- [Craigslist Scraper](https://apify.com/om_kh/craigslist-scraper) — Craigslist listings from any city, category or search link: title, price, date, neighborhood, GPS, photos, optional description and attributes. Goes beyond the 360-result limit. $0.001 per listing, $0.0015 with details.
- [Substack Scraper](https://apify.com/om_kh/substack-scraper) — Substack newsletters and posts: subscriber count, paid prices, author socials, plus posts with likes, comments, restacks and optional full text. $0.002 per newsletter, $0.0005 per post, $0.001 per post with full text. Search posts by topic across Substack; comments and HTML on request.
- [Threads Replies Scraper](https://apify.com/om_kh/threads-replies-scraper) — every reply under any public Threads post: text, author, verified badge, likes, date, links, media. Top, most recent or all (up to 10,000 per post), optional sub-replies, no login. $0.002 per reply, first 20 free per run.
- [Telegram Channel Scraper](https://apify.com/om_kh/telegram-channel-scraper) — public Telegram channel posts with text, date, views, reactions, photos, links and forwards, plus channel title and subscriber count. No login, no phone. $0.0005 per post.
- [Snapchat Profile Scraper](https://apify.com/om_kh/snapchat-profile-scraper) — public Snapchat profiles: subscriber count, bio, website, emails in bio, verified badge, related accounts, plus every Spotlight video with views. $0.0015 per profile, $0.001 per Spotlight video.
- [Google Play Store Scraper](https://apify.com/om_kh/google-play-store-scraper) — Google Play **reviews** (filters by rating, date, language, device, version, keyword; $0.10 per 1,000) and apps by ID, URL or keyword: exact installs, rating histogram, reviews count, **developer email**, website, price, ads and in-app purchases. $0.0015 per app.
- [Coles Australia Scraper](https://apify.com/om_kh/coles-australia-scraper) — Coles supermarket prices, was-prices and specials from any search, aisle or link, with per-store prices, brand and dietary filters, sort by unit price, and optional barcode, ingredients and nutrition ($0.003 per product with those details). $0.001 per product, no start fee.
- [11st Korea Product Scraper](https://apify.com/om_kh/11st-korea-product-scraper) — products from **11st (11번가)**, a top South Korean marketplace, for any search in Korean or English: price in won, list price, discount, brand, seller, **sales count**, rating, delivery and lowest-price flags; 7 sort orders, price filter, ads flagged. $0.004 per product.
- [AliExpress Search Scraper](https://apify.com/om_kh/aliexpress-search-scraper) — AliExpress products for any keyword with the **seller's real price** (the new-shopper teaser kept apart), list price, discount, rating, **units sold**, Choice flag, delivery estimate and badges; filters on price, rating and units sold, up to 3,000 per search. $0.003 per product.
- [Truth Social Scraper](https://apify.com/om_kh/truth-social-scraper) — every post of public Truth Social accounts (or single posts), with replies-only, media-only and only-new-since-last-run filters, with text, date, replies, ReTruths, likes, media, hashtags and mentions, plus followers. $0.001 per post.
- [LinkedIn Ad Library Scraper](https://apify.com/om_kh/linkedin-ad-library-scraper) — ads from LinkedIn's public Ad Library by keyword, advertiser, company page, pasted search link or country: full ad text, landing page, media, run dates, **impressions by country** and targeting. $0.001 per ad.
- [YouTube Email Scraper](https://apify.com/om_kh/youtube-channel-email-scraper) — public business emails of YouTube creators from the bio, their website and link page, or their latest video descriptions, MX-checked. 33 of 59 channels in a dated test. $0.004 per email found.
- [SEEK & JobStreet Jobs Scraper](https://apify.com/om_kh/seek-jobstreet-jobs-scraper) — jobs from SEEK (AU, NZ), JobStreet (MY, SG, ID, PH) and JobsDB (HK, TH) with parsed salary and company profile. $0.001 per job.
- [Kalshi & Polymarket Scraper](https://apify.com/om_kh/kalshi-polymarket-scraper) — live prediction-market odds from both exchanges in one table. $0.001 per market.
- [Website Screenshot API](https://apify.com/om_kh/website-screenshot-api) — full-page, viewport or element screenshots of up to 1,000 URLs as **PNG, JPEG or PDF** in a real Chrome browser: desktop, laptop, retina, iPad, iPhone or custom size, dark mode, cookie banners hidden (never accepted), ads blocked, lazy images loaded; **error pages are never charged**. $0.0025 per screenshot, $0.004 per full page or PDF.
- [Bilibili Scraper](https://apify.com/om_kh/bilibili-scraper) — Bilibili (哔哩哔哩) videos by keyword, link or the popular board with **views, likes, coins, favorites, shares**, danmaku and comment counts, tags, the creator's followers and verified title, top comments, **creators (UP主)** by UID or keyword, and **danmaku** bullet comments. No login. $0.004 per video, 5x cheaper than the most-used Bilibili Actor.
- [Google Trends Scraper](https://apify.com/om_kh/google-trends-scraper) — interest over time, average / peak / % change, interest by **country, region, city and metro**, rising and **Breakout** queries, compare mode, **custom dates**, YouTube / News / Images / Shopping trends, and every **Trending now** search of any country (4 hours to 7 days) with volume, growth and category. $0.002 per keyword.
- [YouTube Channel Search Scraper](https://apify.com/om_kh/youtube-channel-search-scraper) — find YouTube channels by keyword or through the videos that rank, up to 1,000 per search, with subscriber, video-count and verified filters; optional country, total views, social links and public business email. $0.0005 per channel.

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

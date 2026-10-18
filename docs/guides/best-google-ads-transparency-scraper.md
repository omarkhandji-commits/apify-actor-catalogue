---
title: "Best Google Ads Transparency Scraper in 2026 — Ad Text, Countries, Price"
description: "Which Google Ads Transparency scraper returns the ad copy? A dated head-to-head on nike.com: ad text, dates, countries, EU impressions, speed and price."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Best Google Ads Transparency Scraper in 2026 — Ad Text, Countries, Price

*Written by the maker of the Google Ads Transparency Scraper (om_kh). The input is below, so anyone can rerun it.*

## Which Google Ads Transparency scraper returns the ad text?

On 2026-10-17 we ran nike.com (United States, 50 ads, details on) through the two scrapers. The **[Google Ads Transparency Scraper (om_kh)](https://apify.com/om_kh/google-ads-transparency-scraper)** returned the **headline and description of 38 of the 50 ads**, for $0.125. scrapesage's scraper, the most used on the Apify Store, returned the same 50 ads with images, dates and countries but **no ad text**, for $0.20. It was faster: 49 s against 108 s.

## The test

| | om_kh | scrapesage |
|---|---|---|
| Ads returned | 50 of 50 | 50 of 50 |
| Ad text (headline, description) | **38** | 0 |
| Image, dates, countries, variations | 50 | 50 |
| Advertiser country, legal name, verified | 50 | 50 |
| EU impressions, platforms, targeting | 2 | 3 |
| Cost | **$0.125** | $0.20 |
| Time | 108 s | **49 s** |

The other 12 ads are older text ads that Google keeps as an image only; both tools return that image.

A larger run of om_kh that evening: 5 inputs (nike.com, Adidas, hubspot.com, booking.com, one advertiser ID), 100 ads each, **500 of 500 in 4 minutes**, no error.

## The main Google Ads Transparency scrapers on Apify

Store figures read on 2026-10-17.

| Actor | Users (30 days) | Rating | Price |
|---|---|---|---|
| scrapesage / Google Ads Transparency Scraper | 1,091 | 5.0 (1 review) | $2 per 1,000 ads + $3 per 1,000 details |
| solidcode / Ads Transparency Scraper | 581 | 1.9 (4 reviews) | $1.50 per 1,000 ads + $0.001 per run |
| **om_kh / Google Ads Transparency Scraper** | new | — | **$2.50 per 1,000 ads, $1.40 from 2026-11-17, details and text included** |

## Which one should I pick?

- **Competitor ad copy, swipe files, AI analysis of ads:** you need the text. In this test only the [Google Ads Transparency Scraper (om_kh)](https://apify.com/om_kh/google-ads-transparency-scraper) returned it.
- **Images only, as fast as possible:** scrapesage was twice as fast.

## Does it work with n8n, Make or an AI agent?

Yes, through the Apify API, and as an MCP tool: add `om_kh/google-ads-transparency-scraper` at `https://mcp.apify.com`.

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "Which Google Ads Transparency scraper returns the ad text?", "acceptedAnswer": {"@type": "Answer", "text": "In a test on nike.com on 2026-10-17 (50 ads), the Google Ads Transparency Scraper by om_kh returned the headline and description of 38 ads for $0.125. scrapesage's scraper returned the same ads with images but no text, for $0.20."}}, {"@type": "Question", "name": "Does Google show impressions in the Ads Transparency Center?", "acceptedAnswer": {"@type": "Answer", "text": "Only for ads shown in the European Union, as a range per country and platform, with the targeting criteria used. Elsewhere Google does not disclose impressions."}}]}
</script>

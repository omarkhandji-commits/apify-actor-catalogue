---
title: "Free n8n workflow templates for Apify Actors (Google Sheets, Slack)"
description: "Ready-to-import n8n workflows: YouTube transcripts, Google Maps new businesses, YouTube creator emails, ATS jobs to Slack, Kalshi/Polymarket odds, Google Trends."
---

# Free n8n workflow templates

Download a `.json` file, then in n8n: **Workflows → Import from file**. Each template has a yellow *Setup* note:
add your Apify API token as a Header Auth credential (`Authorization: Bearer YOUR_TOKEN`), connect Google Sheets or
Slack, edit the input, activate. No token is stored in the files. `maxTotalChargeUsd` caps the cost of every run.

| Workflow | File |
|---|---|
| [Discover -> monitor -> qualify: local business lead pipeline](n8n/flagship-local-lead-pipeline.json) | `flagship-local-lead-pipeline.json` |
| [New Google Business Profile question -> Slack alert](n8n/gbp-qa-alert.json) | `gbp-qa-alert.json` |
| [Google Trends interest to Google Sheets every week](n8n/google-trends-to-google-sheets.json) | `google-trends-to-google-sheets.json` |
| [Kalshi and Polymarket odds to Slack every hour](n8n/kalshi-polymarket-odds-to-slack.json) | `kalshi-polymarket-odds-to-slack.json` |
| [Local business discovery snapshot -> Google Sheets](n8n/local-business-discovery.json) | `local-business-discovery.json` |
| [New Google Maps business detected -> Slack + Sheets](n8n/maps-new-business-alert.json) | `maps-new-business-alert.json` |
| [New local businesses from Google Maps to Google Sheets (lead gen)](n8n/new-google-maps-businesses-to-google-sheets.json) | `new-google-maps-businesses-to-google-sheets.json` |
| [New jobs from Greenhouse, Lever, Ashby and Workday to Slack](n8n/new-jobs-greenhouse-lever-ashby-to-slack.json) | `new-jobs-greenhouse-lever-ashby-to-slack.json` |
| [Find YouTube creators with business emails to Google Sheets](n8n/youtube-creator-emails-to-google-sheets.json) | `youtube-creator-emails-to-google-sheets.json` |
| [Save YouTube transcripts to Google Sheets](n8n/youtube-transcripts-to-google-sheets.json) | `youtube-transcripts-to-google-sheets.json` |
| [Zillow price/status change -> Slack alert](n8n/zillow-price-change-alert.json) | `zillow-price-change-alert.json` |
| [New Google Jobs postings to Google Sheets every morning](n8n/google-jobs-to-google-sheets.json) | `google-jobs-to-google-sheets.json` |
| [New replies on a Threads post to Google Sheets every hour](n8n/threads-replies-to-google-sheets.json) | `threads-replies-to-google-sheets.json` |
| [TikTok videos for a keyword to Google Sheets every day](n8n/tiktok-keyword-videos-to-google-sheets.json) | `tiktok-keyword-videos-to-google-sheets.json` |
| [Google Hotels prices to Google Sheets every morning](n8n/google-hotels-prices-to-google-sheets.json) | `google-hotels-prices-to-google-sheets.json` |
| [Google Play app reviews to Google Sheets every morning](n8n/google-play-reviews-to-google-sheets.json) | `google-play-reviews-to-google-sheets.json` |
| [LinkedIn company data to Google Sheets every tuesday](n8n/linkedin-company-data-to-google-sheets.json) | `linkedin-company-data-to-google-sheets.json` |
| [YouTube comments to Google Sheets every morning](n8n/youtube-comments-to-google-sheets.json) | `youtube-comments-to-google-sheets.json` |
| [YouTube search results to Google Sheets every morning](n8n/youtube-search-videos-to-google-sheets.json) | `youtube-search-videos-to-google-sheets.json` |
| [Google News headlines to Google Sheets every morning](n8n/google-news-headlines-to-google-sheets.json) | `google-news-headlines-to-google-sheets.json` |
| [LinkedIn ads of a competitor to Google Sheets every tuesday](n8n/linkedin-ads-of-a-competitor-to-google-sheets.json) | `linkedin-ads-of-a-competitor-to-google-sheets.json` |
| [New Truth Social posts to Google Sheets every hour](n8n/truth-social-posts-to-google-sheets.json) | `truth-social-posts-to-google-sheets.json` |
| [Jobs from company career sites to Google Sheets every morning](n8n/company-careers-page-jobs-to-google-sheets.json) | `company-careers-page-jobs-to-google-sheets.json` |
| [French companies from the official registry to Google Sheets every tuesday](n8n/france-company-registry-to-google-sheets.json) | `france-company-registry-to-google-sheets.json` |

## Make.com blueprints (import a file)

In Make: new scenario → **⋮** menu (top right) → **Import blueprint** → pick the file → choose your own Apify connection in both modules → add Google Sheets, Slack or any app after it. Each blueprint is *Apify: Run an Actor* → *Apify: Get Dataset Items*, with a cost cap per run. No connection or token is stored in the files.

| Scenario | File |
|---|---|
| [New Google Jobs postings (Apify + Make)](make/google-jobs.make-blueprint.json) | `google-jobs.make-blueprint.json` |
| [New replies on a Threads post (Apify + Make)](make/threads-replies.make-blueprint.json) | `threads-replies.make-blueprint.json` |
| [Google Trends interest (Apify + Make)](make/google-trends.make-blueprint.json) | `google-trends.make-blueprint.json` |
| [Kalshi and Polymarket odds (Apify + Make)](make/kalshi-polymarket-odds.make-blueprint.json) | `kalshi-polymarket-odds.make-blueprint.json` |
| [New local businesses from Google Maps (Apify + Make)](make/new-google-maps-businesses.make-blueprint.json) | `new-google-maps-businesses.make-blueprint.json` |
| [New jobs from Greenhouse, Lever, Ashby and Workday (Apify + Make)](make/new-jobs-greenhouse-lever-ashby.make-blueprint.json) | `new-jobs-greenhouse-lever-ashby.make-blueprint.json` |
| [TikTok videos for a keyword (Apify + Make)](make/tiktok-keyword-videos.make-blueprint.json) | `tiktok-keyword-videos.make-blueprint.json` |
| [Find YouTube creators with business emails (Apify + Make)](make/youtube-creator-emails.make-blueprint.json) | `youtube-creator-emails.make-blueprint.json` |
| [Save YouTube transcripts (Apify + Make)](make/youtube-transcripts.make-blueprint.json) | `youtube-transcripts.make-blueprint.json` |
| [Google Hotels prices (Apify + Make)](make/google-hotels-prices.make-blueprint.json) | `google-hotels-prices.make-blueprint.json` |
| [Google Play app reviews (Apify + Make)](make/google-play-reviews.make-blueprint.json) | `google-play-reviews.make-blueprint.json` |
| [LinkedIn company data (Apify + Make)](make/linkedin-company-data.make-blueprint.json) | `linkedin-company-data.make-blueprint.json` |
| [YouTube comments (Apify + Make)](make/youtube-comments.make-blueprint.json) | `youtube-comments.make-blueprint.json` |
| [YouTube search results (Apify + Make)](make/youtube-search-videos.make-blueprint.json) | `youtube-search-videos.make-blueprint.json` |
| [Google News headlines (Apify + Make)](make/google-news-headlines.make-blueprint.json) | `google-news-headlines.make-blueprint.json` |
| [LinkedIn ads of a competitor (Apify + Make)](make/linkedin-ads-of-a-competitor.make-blueprint.json) | `linkedin-ads-of-a-competitor.make-blueprint.json` |
| [New Truth Social posts (Apify + Make)](make/truth-social-posts.make-blueprint.json) | `truth-social-posts.make-blueprint.json` |
| [Jobs from company career sites (Apify + Make)](make/company-careers-page-jobs.make-blueprint.json) | `company-careers-page-jobs.make-blueprint.json` |
| [French companies from the official registry (Apify + Make)](make/france-company-registry.make-blueprint.json) | `france-company-registry.make-blueprint.json` |

Make.com scenario specs: [workflows/make](make/README.md) · Postman: [collection](postman/local-maps-collection.json) · [All Actors](../all-actors.md)

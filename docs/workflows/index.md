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
| [TikTok videos for a keyword to Google Sheets every day](n8n/tiktok-keyword-videos-to-google-sheets.json) | `tiktok-keyword-videos-to-google-sheets.json` |

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

Make.com scenario specs: [workflows/make](make/README.md) · Postman: [collection](postman/local-maps-collection.json) · [All Actors](../all-actors.md)

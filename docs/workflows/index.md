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

Make.com scenario specs: [workflows/make](make/README.md) · Postman: [collection](postman/local-maps-collection.json) · [All Actors](../all-actors.md)

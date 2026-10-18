---
title: "Website Screenshot API — Full Page, Mobile and PDF Captures of Any URL"
description: "Take full-page or viewport screenshots of up to 1,000 URLs as PNG, JPEG or PDF in a real browser, on desktop or mobile, with cookie banners hidden. $2.50 per 1,000, error pages free."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# How do I take screenshots of many websites with an API?

Use the **[Website Screenshot API (om_kh)](https://apify.com/om_kh/website-screenshot-api)** on Apify. Give it a list of URLs; it opens each one in a real Chrome browser and returns one row per page with a **public link to the PNG, JPEG or PDF**, the final URL, the HTTP status, the page title and the load time.

*Written by the maker of the Actor (om_kh). Prices of other Actors were read from the Apify Store on 2026-10-18.*

## What it does

- Full page (long pages cut at 12,000 px), viewport, or one element by CSS selector.
- Desktop, laptop, retina, iPad, iPhone or a custom size; dark mode.
- Cookie banners of the common consent tools hidden (never accepted), ads and trackers blocked, lazy images loaded.
- Error pages (HTTP 4xx/5xx) are delivered and marked `blocked: true`, **never charged**.

## Price

| | Per 1,000 |
|---|---|
| Viewport or element screenshot | $2.50 |
| Full-page screenshot or PDF | $4.00 |
| Run start | $0.001 per run |

Other paid screenshot Actors in the Store on 2026-10-18: moonweil/url-screenshot-api $4 per 1,000 plus $0.001 per run, i-scraper/website-screenshot $6 per 1,000. apify/screenshot-url is a free Actor where you pay the platform usage.

## Tested on 50 popular websites

Desktop, default settings, 2026-10-18: **37 good viewport captures and 13 error pages** (delivered, not charged); **36 good full-page JPEG captures**. Some news and social sites refuse automated browsers; the Actor does not try to get around that.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/website-screenshot-api").call(run_input={
    "urls": ["https://apify.com", "example.com"],
    "device": "mobile",
    "fullPage": True,
    "format": "jpeg",
})
for row in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(row["url"], row["statusCode"], row["screenshotUrl"])
```

## cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~website-screenshot-api/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"urls": ["https://apify.com"], "fullPage": false, "format": "png"}'
```

## Output fields

`url`, `finalUrl`, `statusCode`, `blocked`, `title`, `screenshotUrl`, `key`, `format`, `device`, `viewportWidth`, `viewportHeight`, `fullPage`, `darkMode`, `bytes`, `loadTimeMs`, `takenAt`.

## Common uses

Visual monitoring of your own or competitors' pages on a schedule, SEO and QA checks on mobile and desktop, dated PDF evidence of pages and terms, and page images for AI agents (the Actor is also available as an MCP tool).

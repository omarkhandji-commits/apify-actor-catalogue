---
title: "Website Screenshot Generator API - Full Page, PDF $2.50/1K"
description: "Website screenshot generator API: full-page or viewport PNG, JPEG or PDF of any URL in a real browser. Desktop, tablet, mobile or custom size, dark mode, cookie banners hidden, ads blocked, lazy images loaded. $2.50 per 1,000 screenshots ($4 full page or PDF), refused pages free."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Website Screenshot Generator API - Full Page, PDF $2.50/1K

Website screenshot generator API: full-page or viewport PNG, JPEG or PDF of any URL in a real browser. Desktop, tablet, mobile or custom size, dark mode, cookie banners hidden, ads blocked, lazy images loaded. $2.50 per 1,000 screenshots ($4 full page or PDF), refused pages free.

**Run it on Apify:** [https://apify.com/om_kh/website-screenshot-api](https://apify.com/om_kh/website-screenshot-api) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Up to 1,000 web page links, a device and a format |
| **We do** | Open each page in a real Chrome browser and capture it |
| **You get** | One row per page: a public link to the PNG, JPEG or PDF file, the final URL, HTTP status, page title and load time |
| **It costs** | $2.50 per 1,000 screenshots, $4 per 1,000 full-page screenshots or PDFs, + $0.001 per GB of run memory per run ($0.004 at the default 4 GB). The first 5 screenshots of every run are free. No supplier fee |
| **It does not** | Sign in to sites. Very long pages are cut at 12,000 pixels |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `urls` | array | Web pages to capture, one per line (up to 1,000). 'example.com' works too. Default: `["https://apify.com", "https://www.wikipedia.org"]`. |
| `device` | string | Screen size and type the page is opened with. Default: `"desktop"`. |
| `width` | integer | Only with Custom size. 200 to 3,840. |
| `height` | integer | Only with Custom size. 200 to 4,320. |
| `viewportWidth` | integer | Width of the browser window, 200 to 3840, with the chosen device's height. |
| `fullPage` | boolean | Capture the whole page, not only the visible screen (very long pages are cut at 12,000 px). Default: `true`. |
| `format` | string | File type. Default: `"png"`. |
| `quality` | integer | 10 to 100. Default: `80`. |
| `darkMode` | boolean | Ask the site for its dark theme (prefers-color-scheme: dark). Default: `false`. |
| `hideCookieBanners` | boolean | Hide the consent pop-ups of the common consent tools. Default: `true`. |
| `blockAds` | boolean | Drop requests to common ad and tracking networks. Default: `true`. |
| `scrollToBottom` | boolean | Scroll down the page before a full-page capture so images that load on scroll appear. Default: `true`. |
| `delayAfterScrolling` | integer | Wait this long after scrolling to the bottom, before the capture. 0 to 300,000. Default: `0`. |
| `waitUntilNetworkIdleAfterScroll` | boolean | After scrolling, wait until the page stops loading (lazy images, feeds) before the capture. Default: `false`. |
| `waitUntilNetworkIdleAfterScrollTimeout` | integer | Longest wait for a quiet network after scrolling. Default: `30000`. |
| `waitUntil` | string | When the page counts as ready. Default: `"load"`. |
| `delaySeconds` | integer | Wait this long after loading, for animations. 0 to 300. Default: `0`. |
| `delay` | integer | Same as the delay in seconds but in milliseconds, 0 to 300,000. |
| `waitForSelector` | string | Optional CSS selector to wait for before the capture. |
| `elementSelector` | string | Optional CSS selector: the screenshot shows only the first matching element. |
| `hideSelectors` | array | Optional CSS selectors to hide (chat widgets, headers...). |
| `selectorsToHide` | string | Same as above as one comma-separated text, e.g. '.chat, #banner'. |
| `timeoutSeconds` | integer | 10 to 120. Default: `45`. |
| `maxTotalChargeUsd` | number | The run takes no more screenshots than this amount pays for. |
| `maxConcurrency` | integer | Advanced. |
| `proxy` | object | Optional: open the pages through Apify Proxy or your own proxy (to see a site as a visitor from another country sees it). |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "screenshot",
  "blocked": false,
  "url": "https://apify.com",
  "finalUrl": "https://apify.com/",
  "statusCode": 200,
  "title": "Apify: Marketplace of ready-to-run tools for AI",
  "screenshotUrl": "https://api.apify.com/v2/key-value-stores/n1hRv8H6fOMeZZXKM/records/screenshot-0001-apify.com.png?signature=Rrmd5FZPoYHVjEcyVQIh",
  "key": "screenshot-0001-apify.com.png",
  "format": "png",
  "device": "desktop",
  "viewportWidth": 1920,
  "viewportHeight": 1080,
  "fullPage": true,
  "darkMode": false,
  "bytes": 943019,
  "loadTimeMs": 4211,
  "takenAt": "2026-10-23T23:45:36Z"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/website-screenshot-api").call(run_input={
    "urls": [
        "https://apify.com",
        "https://www.wikipedia.org"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~website-screenshot-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"urls": ["https://apify.com", "https://www.wikipedia.org"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/website-screenshot-api` as a tool.

Full documentation, pricing and the latest changes: [Website Screenshot Generator API - Full Page, PDF $2.50/1K](https://apify.com/om_kh/website-screenshot-api).

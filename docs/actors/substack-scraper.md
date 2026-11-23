---
title: "Substack Posts Scraper - Newsletters, Subscribers, Likes"
description: "Substack posts scraper: newsletters and posts with subscribers, paid prices, author socials, likes, restacks, full text or HTML and comments. Search posts by topic across Substack, find top newsletters by category, filter by date and type. No login. From $0.50 per 1,000 posts."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Substack Posts Scraper - Newsletters, Subscribers, Likes

Substack posts scraper: newsletters and posts with subscribers, paid prices, author socials, likes, restacks, full text or HTML and comments. Search posts by topic across Substack, find top newsletters by category, filter by date and type. No login. From $0.50 per 1,000 posts.

**Run it on Apify:** [https://apify.com/om_kh/substack-scraper](https://apify.com/om_kh/substack-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Newsletters, categories or topics |
| **We do** | Read Substack newsletters and their posts, and search posts across all of Substack |
| **You get** | Newsletters (subscribers, paid prices, author, socials) and posts (title, date, likes, comments, restacks, word count, free or paid); option: full text, HTML and comments |
| **It costs** | $0.50 per 1,000 posts, $1 per 1,000 with full text, $2 per 1,000 newsletters, + $0.001 per run from Dec 4, 2026 (no start fee before). The first 20 results of every run are free. No supplier fee |
| **It does not** | Read paid posts or comment text that need a subscription |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `newsletters` | array | Substack newsletters: links (any page of the newsletter, custom domains work), name.substack.com, or just the subdomain (e.g. lenny). Default: `["lenny"]`. |
| `categories` | array | Substack leaderboard categories to discover top newsletters, e.g. Technology, Business, Finance, Culture, Politics, Health & Wellness, Food & Drink, Sports, Science, Crypto. Default: `["Technology"]`. |
| `maxNewslettersPerCategory` | integer | Top-ranked first, 1 to 1,000. Default: `25`. |
| `paidOnly` | boolean | Use the leaderboard of paid newsletters (ranked by paid subscribers). Default: `false`. |
| `keywords` | array | Find public posts across all of Substack for these topics, e.g. artificial intelligence, climate policy (up to 50). |
| `maxPostsPerKeyword` | integer | 1 to 500. Default: `20`. |
| `maxPostsPerNewsletter` | integer | Newest first, 0 to 5,000. 0 = newsletter info only. Default: `20`. |
| `includeText` | boolean | Full text of free posts (and the public preview of paid posts). Default: `false`. |
| `includeHtml` | boolean | Add the full HTML body next to the plain text (same price as the text). Default: `false`. |
| `includeComments` | boolean | Add each post's comments and replies in a commentsList field. Default: `false`. |
| `maxCommentsPerPost` | integer | 1 to 2,000, replies included. Default: `20`. |
| `postedAfter` | string | Only posts on or after this date (YYYY-MM-DD). |
| `postedBefore` | string | YYYY-MM-DD. |
| `contentType` | string | Keep only this kind of post. Default: `"all"`. |
| `onlyFree` | boolean | Skip paywalled posts. Default: `false`. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "newsletter",
  "category": "Technology",
  "categoryRank": 2,
  "newsletterId": 458709,
  "name": "(hidden here)",
  "url": "https://newsletter.pragmaticengineer.com",
  "subdomain": "pragmaticengineer",
  "customDomain": "newsletter.pragmaticengineer.com",
  "description": "Big Tech and startups, from the inside. Highly relevant for software engineers, AI engineers and engineering leaders, useful for those wo...",
  "language": "en",
  "subscribers": 1100000,
  "subscribersText": "1.1M+",
  "leaderboardBadge": "Tens of thousands of paid subscribers",
  "paidEnabled": true,
  "monthlyPriceUsd": 15,
  "yearlyPriceUsd": 150,
  "currency": "usd",
  "hasPodcast": true,
  "createdAt": "2021-08-25T13:08:12.798Z",
  "firstPostDate": "2021-08-30T11:24:02.082Z",
  "logo": "https://substackcdn.com/image/fetch/$s_!eod5!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%...",
  "authorName": "(hidden here)",
  "authorHandle": "(hidden here)",
  "authorBio": "(hidden here)",
  "authorFollowers": "(hidden here)",
  "bestsellerTier": 10000,
  "authorSocials": "(hidden here)",
  "authorWebsite": "(hidden here)",
  "profileUrl": "https://substack.com/@pragmaticengineer"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/substack-scraper").call(run_input={
    "newsletters": [
        "lenny"
    ],
    "categories": [
        "Technology"
    ],
    "maxNewslettersPerCategory": 10,
    "maxPostsPerNewsletter": 5
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~substack-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"newsletters": ["lenny"], "categories": ["Technology"], "maxNewslettersPerCategory": 10, "maxPostsPerNewsletter": 5}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/substack-scraper` as a tool.

Full documentation, pricing and the latest changes: [Substack Posts Scraper - Newsletters, Subscribers, Likes](https://apify.com/om_kh/substack-scraper).

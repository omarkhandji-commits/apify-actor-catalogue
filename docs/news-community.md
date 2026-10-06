[← Catalogue home](index.md)

# News & Community monitoring

## What problem this solves

Tracking mentions of a keyword or brand across Reddit, Hacker News, Stack Overflow, Product Hunt, and Google News — the places technical and general audiences actually talk, distinct from social platforms.

## When to use it

- You want **brand/keyword mentions** across all of Reddit, or a **specific subreddit** you already follow, or **one Reddit user's** history.
- You want **developer-community reaction** (Hacker News, Stack Overflow) instead of general news.
- You want to track **Product Hunt launches** matching a topic.
- You want **general news coverage** of a topic, no API key.

## Actors in this family

| Actor | Best for | Pricing |
|---|---|---|
| [Reddit Posts & Comments Scraper](https://apify.com/om_kh/reddit-posts-comments-scraper) | Keyword search across all of Reddit | $0.15 / monitored subject re-checked |
| [Reddit Subreddit Posts & Comments Scraper](https://apify.com/om_kh/reddit-subreddit-scraper) | One specific subreddit you already follow | $0.15 / monitored subject re-checked |
| [Reddit User Posts & Comments Scraper](https://apify.com/om_kh/reddit-user-scraper) | One specific Reddit account's history | $0.15 / monitored subject re-checked |
| [Hacker News Scraper](https://apify.com/om_kh/hacker-news-scraper) | Developer-community link/comment threads by keyword | $0.001 / hacker news story + $0.002 / monitored subject re-checked |
| [Stack Overflow Scraper](https://apify.com/om_kh/stack-overflow-scraper) | Q&A-style developer discussion by tag | $0.002 / stack overflow question + $0.002 / monitored subject re-checked |
| [Product Hunt Scraper](https://apify.com/om_kh/product-hunt-scraper) | New launches matching a topic | $0.01 / new launch alert + $0.2 / monitored subject re-checked |
| [Google News API](https://apify.com/om_kh/google-news-scraper) | Searches, topic sections, local news; up to 5,000 articles per search, publisher's own link, picture and summary; no API key | Free until 12 Oct 2026, then $0.002 per article |

## Telling the siblings apart

The three Reddit Actors differ only in scope: **keyword across all of Reddit**, **one known subreddit**, or **one known account** — pick based on what you already know. **Hacker News** and **Stack Overflow** both cover developer audiences but different formats: link/discussion threads vs. structured Q&A. **Product Hunt** is launch-specific, not ongoing discussion. **Google News** is the only general-news source in this family and the only free one.

## Recommended starting point

[**Reddit Posts & Comments Scraper**](https://apify.com/om_kh/reddit-posts-comments-scraper) — broadest reach when you don't know which subreddit to watch. Try it: [live example](https://apify.com/om_kh/reddit-posts-comments-scraper/examples/vigia-reddit-brand-monitor-quickstart).

## Related family

Same keyword, different audience: see [Social Monitoring](social-monitoring.md) for X/Twitter and Instagram/TikTok coverage of the same topic.

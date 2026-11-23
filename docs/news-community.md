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
| [Reddit Posts & Comments Scraper](https://apify.com/om_kh/reddit-posts-comments-scraper) | Keyword search across all of Reddit | $9 per 1,000 posts, no start fee (lowered on 21 November 2026 from $10) |
| [Reddit Subreddit Posts & Comments Scraper](https://apify.com/om_kh/reddit-subreddit-scraper) | One specific subreddit you already follow | $0.75 per 1,000 posts, no start fee (lowered on 21 November 2026 from $10) |
| [Reddit User Posts & Comments Scraper](https://apify.com/om_kh/reddit-user-scraper) | One specific Reddit account's history | Our fee is $0.75 per 1,000 posts; the optional scheduled monitoring adds $0.005 per check (one-off runs never pay it) |
| [Hacker News Scraper](https://apify.com/om_kh/hacker-news-scraper) | Developer-community link/comment threads by keyword | $0.19 per 1,000 stories and comments + $0.001 per run |
| [Stack Overflow Scraper](https://apify.com/om_kh/stack-overflow-scraper) | Q&A-style developer discussion by tag | $2 per 1,000 questions + $0.001 per run |
| [Product Hunt Scraper](https://apify.com/om_kh/product-hunt-scraper) | New launches matching a topic | $7.50 per 1,000 launches + $0.001 per run |
| [Google News API](https://apify.com/om_kh/google-news-scraper) | Searches, topic sections, local news; up to 5,000 articles per search, publisher's own link, picture and summary; no API key | $0.002 per article ($0.003 from Nov 12) |

## Telling the siblings apart

The three Reddit Actors differ only in scope: **keyword across all of Reddit**, **one known subreddit**, or **one known account** — pick based on what you already know. **Hacker News** and **Stack Overflow** both cover developer audiences but different formats: link/discussion threads vs. structured Q&A. **Product Hunt** is launch-specific, not ongoing discussion. **Google News** is the only general-news source in this family and the only free one.

## Recommended starting point

[**Reddit Posts & Comments Scraper**](https://apify.com/om_kh/reddit-posts-comments-scraper) — broadest reach when you don't know which subreddit to watch. Try it: [live example](https://apify.com/om_kh/reddit-posts-comments-scraper/examples/vigia-reddit-brand-monitor-quickstart).

## Related family

Same keyword, different audience: see [Social Monitoring](social-monitoring.md) for X/Twitter and Instagram/TikTok coverage of the same topic.

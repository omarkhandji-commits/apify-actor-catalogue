[← Catalogue home](index.md)

# Social Monitoring

## What problem this solves

Tracking a specific account, or searching a platform for a keyword or hashtag, across the major social platforms — as clean rows instead of a scroll of a feed.

## When to use it

- You know the **account** you want to track (posts, engagement over time).
- You want to **search a platform** by keyword or hashtag instead of watching one account.
- You want a **growth metric** (follower/engagement count over time) rather than content itself.

## Actors in this family

| Actor | Platform | Tracks | Pricing |
|---|---|---|---|
| [Instagram Profile Scraper](https://apify.com/om_kh/instagram-profile-scraper) | Instagram | Account | $0.01 / new post alert + $0.08 / monitored subject re-checked |
| [Instagram Hashtag Monitor](https://apify.com/om_kh/instagram-hashtag-scraper) | Instagram | Hashtag | $0.01 / new post alert + $0.1 / monitored subject re-checked |
| [TikTok Profile Scraper](https://apify.com/om_kh/tiktok-profile-scraper) | TikTok | Account | $0.01 / new video alert + $0.08 / monitored subject re-checked |
| [TikTok Keyword Search & Monitor](https://apify.com/om_kh/tiktok-search-scraper) | TikTok | Keyword | $0.1 / source check + $0.01 / new video |
| [TikTok Hashtag Posts Scraper](https://apify.com/om_kh/vigia-tiktok-hashtag-monitor) | TikTok | Hashtag/campaign | $0.1 / monitored subject re-checked + $0.01 / new post |
| [X (Twitter) Profile Scraper](https://apify.com/om_kh/twitter-x-profile-scraper) | X | Account | $0.05 / monitored subject re-checked |
| [X (Twitter) Search Scraper](https://apify.com/om_kh/twitter-x-search-scraper) | X | Keyword | $0.01 / new mention alert + $0.05 / source check |
| [Facebook Page Scraper](https://apify.com/om_kh/facebook-page-scraper) | Facebook | Page profile/followers | $0.01 / profile change + $0.35 / monitored subject re-checked |
| [Facebook Page Posts Scraper](https://apify.com/om_kh/facebook-page-posts-scraper) | Facebook | Page posts | $0.01 / new post alert + $0.12 / source check |
| [LinkedIn Company Scraper](https://apify.com/om_kh/linkedin-company-scraper) | LinkedIn | Company page | $0.02 / company change + $0.1 / monitored subject re-checked |
| [Twitch Clips Scraper](https://apify.com/om_kh/twitch-clips-scraper) | Twitch | Channel/game clips | $0.01 / new clip alert + $0.12 / monitored subject re-checked |
| [Instagram & TikTok Profile Scraper](https://apify.com/om_kh/instagram-tiktok-profile-scraper) | Instagram/TikTok | Growth delta (follower/engagement trend) | $0.01 / profile change + $0.12 / monitored subject re-checked |

## Telling the siblings apart

Within each platform, the split is the same pattern: a **profile** Actor tracks one known account's own content, and a **keyword/hashtag** Actor searches the platform for you when you don't know the account yet. **Instagram & TikTok Profile Scraper** is different from the others — it doesn't return posts at all, only a follower/engagement growth number compared against your last check, for teams who care about growth rate rather than content.

## Recommended starting point

[**X (Twitter) Search Scraper**](https://apify.com/om_kh/twitter-x-search-scraper) — no account required, works from a keyword. Try it: [live example](https://apify.com/om_kh/twitter-x-search-scraper/examples/vigia-x-keyword-monitor-quickstart).

## Related family

Brand mentions aren't limited to social platforms — see [News & Community](news-community.md) for Reddit, Hacker News, and general news coverage of the same keyword.

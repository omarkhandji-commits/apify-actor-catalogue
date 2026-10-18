---
title: "Best Bilibili Scraper in 2026 — Videos, Creators and Danmaku Without Login, Price per 1,000"
description: "Which Bilibili (哔哩哔哩) scraper gives the most data for the price? Store figures, price per 1,000 rows, and a dated run: 240 videos, 20 creators and 2,500 danmaku in 174 seconds."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Best Bilibili Scraper in 2026 — Videos, Creators and Danmaku Without Login

*Written by the maker of the Bilibili Scraper (om_kh). Store figures are public and anyone can check them.*

## Which Bilibili scraper should I use?

For video search, creator lists and danmaku without a Bilibili account, the **[Bilibili Scraper (om_kh)](https://apify.com/om_kh/bilibili-scraper)** returns every public counter (views, likes, **coins**, favorites, **shares**, comments, danmaku count), tags, the creator's followers and verified title, top comments and danmaku, at **$4 per 1,000 videos or creators** and $0.20 per 1,000 danmaku. The most-used Bilibili Actor on the Apify Store sells every row at $20 per 1,000.

## The main Bilibili scrapers on Apify

Store figures read on 2026-10-18.

| Actor | Users (30 days) | Rating | Price |
|---|---|---|---|
| zhorex / Bilibili Scraper | 2,867 | 2.0 (1 review) | $20 per 1,000 items, $0.05 per danmaku profile |
| socialdatax / Bilibili Data API | 268 | — | $2.99 per 1,000 items |
| lofomachines / Bilibili Scraper | 257 | — | usage based |
| **om_kh / Bilibili Scraper** | new | — | **$4 per 1,000 videos or creators, $0.20 per 1,000 danmaku** |

## Dated run on Apify

2026-10-18: keywords 数码测评 and 原神 sorted by views (100 each), the popular board (40), full details, top comments, 20 danmaku per video, and 20 creators for 美食.

| | Result |
|---|---|
| Videos | 240, all with views, likes, coins, favorites, shares, comments, danmaku count and tags |
| Creator data on each video | 240 of 240 (followers, uploads, likes, verified title) |
| Top comments | 240 of 240 |
| Creators found by keyword | 20 |
| Danmaku | 2,500 |
| Time | 174 seconds |

## What you can and cannot get without login

- **Yes:** keyword search (up to 1,000 videos per keyword, Bilibili's sort and length filter), any video link, the popular board, creators by UID, link or keyword, danmaku with their time in the video.
- **Only 3 comments per video:** Bilibili shows 3 comments to visitors who are not logged in. A scraper that promises full comment threads needs a logged-in account.
- **No full upload list of a creator:** Bilibili protects that page for visitors.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/bilibili-scraper").call(run_input={
    "keywords": ["数码测评"],
    "sortBy": "views",
    "maxVideosPerKeyword": 200,
    "includeTopComments": True,
    "maxDanmakuPerVideo": 50,
})
for row in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(row["type"], row.get("title") or row.get("text"), row.get("views"))
```

## Common uses

China market research on a brand or product, influencer (UP主) lists by niche with followers and verified title, daily brand monitoring with sort "newest", and Chinese-language sentiment corpora from danmaku and comments.

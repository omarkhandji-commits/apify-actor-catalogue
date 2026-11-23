---
title: "Google Play Store Scraper - Reviews, Apps, Developer Email"
description: "Google Play scraper: app details (exact installs, rating histogram, developer email, website, price) and reviews with filters by rating, date, language, device, version and keyword. Any country. $0.14 per 1,000 apps, $0.10 per 1,000 reviews, no start fee."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Google Play Store Scraper - Reviews, Apps, Developer Email

Google Play scraper: app details (exact installs, rating histogram, developer email, website, price) and reviews with filters by rating, date, language, device, version and keyword. Any country. $0.14 per 1,000 apps, $0.10 per 1,000 reviews, no start fee.

**Run it on Apify:** [https://apify.com/om_kh/google-play-store-scraper](https://apify.com/om_kh/google-play-store-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | App IDs, Google Play links or keywords, with a country and language |
| **We do** | Read each app's Google Play page, and its reviews if you ask |
| **You get** | One row per app: exact installs, rating and star histogram, ratings and reviews counts, developer email, website and address, price, ads, in-app purchases, dates, description and screenshots; one row per review with your filters |
| **It costs** | $0.14 per 1,000 apps and $0.10 per 1,000 reviews, no start fee. An app that does not exist in the chosen country is never charged. No supplier fee |
| **It does not** | Return more than 30 apps per keyword (use several keywords), or sign in to Google |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `apps` | array | App IDs (com.spotify.music) or Google Play URLs, one per line. Default: `["com.spotify.music", "https://play.google.com/store/apps/de`. |
| `searchTerms` | array | Optional keywords; each returns up to 30 apps from Google Play search, with full details (up to 20 keywords). Default: `["budget tracker"]`. |
| `maxAppsPerSearch` | integer | 1 to 30. Default: `30`. |
| `country` | string | Two-letter store country, e.g. us, gb, fr, de, in. Default: `"us"`. |
| `language` | string | Two-letter language for texts, e.g. en, fr, es. Default: `"en"`. |
| `maxReviewsPerApp` | integer | How many reviews to read for each app (0 to 100,000). 0: no reviews. $0.10 per 1,000 reviews. Default: `0`. |
| `reviewsOnly` | boolean | Return only the reviews, without the app details row. Default: `false`. |
| `reviewsSort` | string | Google Play's own order. Default: `"newest"`. |
| `reviewRatings` | array | Keep only reviews with these ratings. |
| `reviewLanguages` | array | Two-letter languages to read reviews in: en, fr, de.. |
| `reviewKeywords` | array | Keep only reviews that contain at least one of these words. |
| `reviewsSince` | string | YYYY-MM-DD. |
| `reviewsUntil` | string | YYYY-MM-DD. |
| `recentDays` | integer | Keep only reviews from the last N days. 0 or empty: no limit. |
| `deviceType` | string | Reviews written from this kind of device. |
| `appVersions` | array | Keep only reviews written on these app versions (a prefix works: 2.26 matches 2.26.38.73). |
| `includeSimilarApps` | boolean | Add to each app the IDs of the other apps Google Play shows on its page (similar apps and more by the developer). Default: `false`. |
| `maxTotalChargeUsd` | number | Optional hard cost cap for this run. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "appId": "com.mhriley.spendingtracker",
  "title": "Spending Tracker",
  "url": "https://play.google.com/store/apps/details?id=com.mhriley.spendingtracker&hl=en&gl=us",
  "developer": "MH Riley Ltd",
  "developerId": "MH+Riley+Ltd",
  "developerEmail": "(hidden here)",
  "developerWebsite": "http://www.mhriley.com/spendingtracker",
  "privacyPolicy": "http://www.mhriley.com/spendingtracker/privacy.html",
  "genre": "Finance",
  "genreId": "FINANCE",
  "score": 4.666,
  "ratings": 64531,
  "reviews": 6838,
  "histogram": {
    "1": 1152,
    "2": 721,
    "3": 1731,
    "4": 11272,
    "5": 49644
  },
  "installs": "1,000,000+",
  "minInstalls": 1000000,
  "realInstalls": 4676361,
  "free": true,
  "price": 0,
  "currency": "USD",
  "offersIAP": true,
  "inAppProductPrice": "$3.49 per item",
  "containsAds": true,
  "contentRating": "Everyone",
  "released": "Jan 31, 2014",
  "updatedAt": "2026-08-21T07:44:46Z",
  "version": "2.9",
  "summary": "Track your expenses, stick to a budget, save money. It's that simple!",
  "description": "Spending Tracker is the easiest and most user friendly expense manager app in the store. The simple fact is, by tracking your spending yo...",
  "icon": "https://play-lh.googleusercontent.com/crF6WsTtan4NtpYTRUqpXduLdefsQV4SR7PUz9XQp_2k35rVl2eFJiyMeF-OEB9k16Om2oOjj8q7KvbOdUPl",
  "headerImage": "https://play-lh.googleusercontent.com/WoMXzaxygFSkFNSTZqB4GXKHRW0tg8F3G4KDxVoKGbitYX8MeB7xN5zgOXniD4T90WzUjdM5raI2XQWFr94tw1I",
  "screenshots": [
    "https://play-lh.googleusercontent.com/5i7IDxQ4XgTj1q6TYx-88eSm88gstEwbaL1iMPNyIuvczMCxiXRabJCL-SwosQO8WQ5YwyHiT3fTmHHFhQDm",
    "https://play-lh.googleusercontent.com/g8XfFhJWu1EsO1E0xKXtzycZJpI7S5XjbTHQCDt8_Em0dCgu_4soy5Z2Bx_FN6TdYoRP4_QVyR3az0Z1JRBGRg"
  ],
  "video": "https://www.youtube.com/embed/7w97mMhTq7Y?vq=large&rel=0&autohide=1&showinfo=0",
  "country": "us",
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/google-play-store-scraper").call(run_input={
    "apps": [
        "com.spotify.music",
        "https://play.google.com/store/apps/details?id=com.duolingo"
    ],
    "searchTerms": [
        "budget tracker"
    ],
    "maxAppsPerSearch": 10
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~google-play-store-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"apps": ["com.spotify.music", "https://play.google.com/store/apps/details?id=com.duolingo"], "searchTerms": ["budget tracker"], "maxAppsPerSearch": 10}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/google-play-store-scraper` as a tool.

Full documentation, pricing and the latest changes: [Google Play Store Scraper - Reviews, Apps, Developer Email](https://apify.com/om_kh/google-play-store-scraper).

[← Catalogue home](../../README.md) · [Reviews & Reputation family](../reviews-reputation.md)

# Monitor reviews and detect what changed

## Problem

You want to know when a business gets a new review — not re-download the same reviews every time you check.

## Actors used

1. A source Actor from [Reviews & Reputation](../reviews-reputation.md) — e.g. [Google Maps Reviews Scraper](https://apify.com/om_kh/vigia-google-review-monitor)
2. [Review Cleaner & Deduplicator](https://apify.com/om_kh/vigia-reviews-delta) — if you're combining review data from more than one source or need explicit dedup + delta

## Inputs

```json
{
  "placeUrls": ["https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4"],
  "maxTotalChargeUsd": 1
}
```

## Steps

1. Run the source Actor matching your platform (Google/Yelp/Trustpilot/G2/TripAdvisor/Glassdoor/Amazon/App stores). Each already tracks new-vs-seen reviews on its own via its `monitorEnabled` input — most single-source use cases don't need a second Actor.
2. If you're pulling from **multiple sources** and want one unified new-review feed, pass the combined review data into **Review Cleaner & Deduplicator** as `currentReviews`.

## Sample result shape

*Illustrative — derived from the Actor's real dataset schema, not live data.*

```json
{
  "author": "Dharmendra Yadav",
  "rating": 4,
  "text": "Amazing coffee and a cozy atmosphere.",
  "published_at": "12 hours ago",
  "actionable": false,
  "severity": "minor"
}
```

## Try it live

[Public Task example](https://apify.com/om_kh/vigia-google-review-monitor/examples/vigia-google-review-monitor-quickstart)

## Code

### curl

```bash
curl "https://api.apify.com/v2/actor-tasks/om_kh~vigia-google-review-monitor-quickstart/run-sync-get-dataset-items?token=$APIFY_TOKEN" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"placeUrls": ["https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4"], "maxTotalChargeUsd": 1}'
```

### JavaScript

```javascript
const token = process.env.APIFY_TOKEN;
const res = await fetch(
  `https://api.apify.com/v2/actor-tasks/om_kh~vigia-google-review-monitor-quickstart/run-sync-get-dataset-items?token=${token}`,
  {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      placeUrls: ["https://www.google.com/maps/place/?q=place_id:ChIJN1t_tDeuEmsRUsoyG83frY4"],
      maxTotalChargeUsd: 1,
    }),
  }
);
const reviews = await res.json();
```

## Next step

Want the business's own profile data alongside its reviews? See [Local Business](../local-business.md).

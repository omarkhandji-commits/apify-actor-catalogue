[← Catalogue home](../README.md) · [Ads & Competitive Intelligence family](../docs/ads-competitive-intelligence.md)

# Track new and removed competitor ad creatives

## Problem

You don't just want a snapshot of a competitor's ads today — you want to know when they launch something new or pull a creative.

## Actors used

1. [Facebook Ads Library Scraper](https://apify.com/om_kh/vigia-ads-library-monitor) (or [Google Ads Transparency Scraper](https://apify.com/om_kh/vigia-google-ads-transparency-monitor)) — pulls current ads
2. [Ad Creative Change Detector](https://apify.com/om_kh/vigia-ad-creative-delta) — diffs two snapshots

## Inputs

```json
{
  "pageNames": ["Nike"],
  "maxTotalChargeUsd": 1
}
```

## Steps

1. Run **Facebook Ads Library Scraper** (or the Google equivalent) to get the advertiser's current ad creatives.
2. Save that run's output as `previousAds` the next time you run it, and pass the new run's output as `currentAds` to **Ad Creative Change Detector** — it returns exactly what's new, removed, or edited.

## Sample result shape

*Illustrative — derived from the Actor's real dataset schema, not live data.*

```json
{
  "page_name": "Nike",
  "ad_id": "1033781512449452",
  "creative_fingerprint": "72d59c3e9383543bdfc5f5d1c7c55c06...",
  "is_active": true
}
```

## Try it live

[Public Task example](https://apify.com/om_kh/vigia-ads-library-monitor/examples/vigia-ads-library-monitor-quickstart)

## Code

### curl

```bash
curl "https://api.apify.com/v2/actor-tasks/om_kh~vigia-ads-library-monitor-quickstart/run-sync-get-dataset-items?token=$APIFY_TOKEN" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"pageNames": ["Nike"], "maxTotalChargeUsd": 1}'
```

### JavaScript

```javascript
const token = process.env.APIFY_TOKEN;
const res = await fetch(
  `https://api.apify.com/v2/actor-tasks/om_kh~vigia-ads-library-monitor-quickstart/run-sync-get-dataset-items?token=${token}`,
  {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ pageNames: ["Nike"], maxTotalChargeUsd: 1 }),
  }
);
const ads = await res.json();
```

## Next step

Also want to see if the same competitor is hiring for a related push? See [Jobs & Hiring](../docs/jobs.md).

---
title: "TikTok Influencer Search — Find Creators by Niche With Views and Engagement"
description: "Find TikTok influencers in any niche: followers, median views of recent videos, engagement rate, posting cadence, last video date and a score with its reasons. No login."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# TikTok Influencer Search — Find Creators by Niche With Views and Engagement

## How do I find TikTok influencers in a niche?

Use the **TikTok Influencer Search** robot on Apify. Type a niche (for example `skincare routine`) or paste creators' usernames; it finds creators and measures their recent videos, returning one row per creator with followers, median views of recent videos, engagement rate, how often they post, last video date, the hashtags they use most, their latest videos and a score with its reasons. It does not sign in to TikTok or message anyone.

**Try it:** [TikTok Influencer Search on Apify](https://apify.com/om_kh/tiktok-creator-search-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [TikTok Influencer Search](https://apify.com/om_kh/tiktok-creator-search-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "keywords": [
    "productivity apps"
  ]
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/tiktok-creator-search-scraper").call(run_input={
  "keywords": [
    "productivity apps"
  ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~tiktok-creator-search-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"keywords": ["productivity apps"]}'
```

## What you get

- `username`
- `profile_url`
- `followers`
- `follower_band`
- `median_recent_views`
- `engagement_rate`
- `posting_cadence_days`
- `last_video_at`
- `top_video_url`
- `qualification_score`
- `score_reasons`

## Price

Pay per qualified creator; see the Pricing tab of the robot for today's price. Apify also bills the supplier Actor this robot runs for you, at its own price. The first 3 creators of every run are free of this robot's fee. Set `maxTotalChargeUsd` to cap a run.

## Use cases

- Influencer marketing shortlists
- Outreach lists for brands and agencies
- Checking a creator's real recent reach before paying them

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/tiktok-creator-search-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Does it send messages to creators?**  
No. It only reads public profiles and videos.

**Why median views and not followers only?**  
Followers can be old or bought; median views of recent videos show today's real reach.

## Related

- [TikTok Shop Creator Finder](https://apify.com/om_kh/tiktok-shop-creator-finder)
- [YouTube Business Email Scraper - Bio, Website, Videos](https://apify.com/om_kh/youtube-channel-email-scraper)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I find TikTok influencers in a niche?", "acceptedAnswer": {"@type": "Answer", "text": "Use the TikTok Influencer Search robot on Apify. Type a niche (for example `skincare routine`) or paste creators' usernames; it finds creators and measures their recent videos, returning one row per creator with followers, median views of recent videos, engagement rate, how often they post, last video date, the hashtags they use most, their latest videos and a score with its reasons. It does not sign in to TikTok or message anyone."}}, {"@type": "Question", "name": "Does it send messages to creators?", "acceptedAnswer": {"@type": "Answer", "text": "No. It only reads public profiles and videos."}}, {"@type": "Question", "name": "Why median views and not followers only?", "acceptedAnswer": {"@type": "Answer", "text": "Followers can be old or bought; median views of recent videos show today's real reach."}}]}
</script>

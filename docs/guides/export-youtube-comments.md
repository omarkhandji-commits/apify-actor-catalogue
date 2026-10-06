---
title: "Export YouTube Comments to CSV or JSON — Up to 50,000 per Video, With Replies"
description: "Download the comments of any YouTube video or Short with likes, reply count, author, date and hearted flag. No API key, no quota."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Export YouTube Comments to CSV or JSON — Up to 50,000 per Video, With Replies

## How do I export all comments from a YouTube video?

Use the **YouTube Comments Scraper** with one or more video URLs. It returns up to 50,000 comments per video, with their replies on request (`includeReplies`), sorted by newest or top, with an optional date limit, with text, author, like count, reply count, date and whether the creator hearted it. Export as CSV, Excel or JSON. No YouTube API key and no quota. $0.40 per 1,000 comments.

**Try it:** [YouTube Comments Scraper on Apify](https://apify.com/om_kh/youtube-comments-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [YouTube Comments Scraper](https://apify.com/om_kh/youtube-comments-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "videoUrls": [
    "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
  ],
  "maxComments": 500,
  "sortBy": "top"
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/youtube-comments-scraper").call(run_input={
    "videoUrls": [
        "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
    ],
    "maxComments": 500,
    "sortBy": "top"
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~youtube-comments-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"videoUrls": ["https://www.youtube.com/watch?v=dQw4w9WgXcQ"], "maxComments": 500, "sortBy": "top"}'
```

## What you get

- `commentId`
- `text`
- `author`
- `authorChannelId`
- `likeCount`
- `replyCount`
- `isHearted`
- `published_at`
- `videoId`
- `videoTitle`
- `url`

## Price

$0.0004 per comment. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- Audience research and product feedback
- Sentiment analysis and AI summaries of what viewers say
- Giveaway winner picking
- Competitor channel research

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/youtube-comments-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Does it work on Shorts?**  
Yes, pass a Shorts URL or an 11-character video ID.

**Is there a quota?**  
No YouTube API quota applies.

## Related

- [YouTube Transcript Scraper - Full Text, Timestamps, Language](https://apify.com/om_kh/youtube-transcript-api)
- [YouTube Channel Videos Scraper - Exact Views, $0.50/1K](https://apify.com/om_kh/youtube-channel-videos-scraper)
- [YouTube Search Scraper API - Videos, Views, $0.50/1K](https://apify.com/om_kh/vigia-youtube-search-monitor)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I export all comments from a YouTube video?", "acceptedAnswer": {"@type": "Answer", "text": "Use the YouTube Comments Scraper with one or more video URLs. It returns up to 50,000 comments per video, with their replies on request (`includeReplies`), sorted by newest or top, with an optional date limit, with text, author, like count, reply count, date and whether the creator hearted it. Export as CSV, Excel or JSON. No YouTube API key and no quota. $0.40 per 1,000 comments."}}, {"@type": "Question", "name": "Does it work on Shorts?", "acceptedAnswer": {"@type": "Answer", "text": "Yes, pass a Shorts URL or an 11-character video ID."}}, {"@type": "Question", "name": "Is there a quota?", "acceptedAnswer": {"@type": "Answer", "text": "No YouTube API quota applies."}}]}
</script>

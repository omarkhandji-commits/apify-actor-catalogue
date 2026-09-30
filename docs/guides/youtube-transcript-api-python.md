---
title: "YouTube Transcript API in Python — No API Key, With Timestamps"
description: "Get the transcript of any YouTube video as text, timestamped segments, SRT, VTT or RAG chunks from Python, JavaScript or cURL. No YouTube API key."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# YouTube Transcript API in Python — No API Key, With Timestamps

## How do I get the transcript of a YouTube video with an API?

Call the **YouTube Transcript API** Actor on Apify with a list of video URLs. It returns, for each video, the full text, timestamped segments, the caption language and, on request, SRT, VTT or ~250-word RAG chunks with start and end seconds. No YouTube API key, no OAuth, no cookies. Videos without captions are never charged.

**Try it:** [YouTube Transcript API on Apify](https://apify.com/om_kh/youtube-transcript-api) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [YouTube Transcript API](https://apify.com/om_kh/youtube-transcript-api) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "videos": [
    "https://www.youtube.com/watch?v=aircAruvnKk"
  ],
  "outputFormats": [
    "chunks",
    "srt"
  ]
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/youtube-transcript-api").call(run_input={
    "videos": [
        "https://www.youtube.com/watch?v=aircAruvnKk"
    ],
    "outputFormats": [
        "chunks",
        "srt"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~youtube-transcript-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"videos": ["https://www.youtube.com/watch?v=aircAruvnKk"], "outputFormats": ["chunks", "srt"]}'
```

## What you get

- `video_id`
- `title`
- `channel`
- `language`
- `is_generated`
- `text`
- `segments` (start, duration, text)
- `chunks` (start, end, text)
- `srt` / vtt

## Price

Pay per transcript delivered — see the Pricing tab for the current price. You only pay for results delivered; set `maxTotalChargeUsd` to cap a run.

## Use cases

- RAG chatbots over courses, podcasts or product videos
- Summaries and show notes
- Subtitles for video editors (SRT/VTT)
- Search across a channel's spoken content

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/youtube-transcript-api` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Do I need a YouTube Data API key?**  
No. The official YouTube Data API does not return transcripts of other people's videos anyway; this Actor reads the public captions.

**What if the video has no captions?**  
It is reported as unavailable and not charged.

**Can I get a whole channel?**  
Yes, use [YouTube Channel Transcripts](https://apify.com/om_kh/youtube-channel-transcripts) with an @handle.

## Related

- [YouTube Channel Transcripts Scraper - Every Video to Text](https://apify.com/om_kh/youtube-channel-transcripts)
- [YouTube Comments Scraper - Likes, Replies, Date, $0.40/1K](https://apify.com/om_kh/youtube-comments-scraper)
- [Video Transcript API - YouTube to Text, Timestamps, JSON](https://apify.com/om_kh/video-transcript-api)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I get the transcript of a YouTube video with an API?", "acceptedAnswer": {"@type": "Answer", "text": "Call the YouTube Transcript API Actor on Apify with a list of video URLs. It returns, for each video, the full text, timestamped segments, the caption language and, on request, SRT, VTT or ~250-word RAG chunks with start and end seconds. No YouTube API key, no OAuth, no cookies. Videos without captions are never charged."}}, {"@type": "Question", "name": "Do I need a YouTube Data API key?", "acceptedAnswer": {"@type": "Answer", "text": "No. The official YouTube Data API does not return transcripts of other people's videos anyway; this Actor reads the public captions."}}, {"@type": "Question", "name": "What if the video has no captions?", "acceptedAnswer": {"@type": "Answer", "text": "It is reported as unavailable and not charged."}}, {"@type": "Question", "name": "Can I get a whole channel?", "acceptedAnswer": {"@type": "Answer", "text": "Yes, use [YouTube Channel Transcripts](https://apify.com/om_kh/youtube-channel-transcripts) with an @handle."}}]}
</script>

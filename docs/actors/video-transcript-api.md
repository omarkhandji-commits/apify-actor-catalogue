---
title: "YouTube Video Transcript API - Text, Timestamps, JSON"
description: "Video transcript API for LLMs and RAG: YouTube videos or whole channels to JSON with full text and timestamped segments. Also views, likes, upload date, channel subscribers, optional SRT/VTT and RAG chunks. MCP-ready. $2.50 per 1,000 transcripts, failed videos never charged."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# YouTube Video Transcript API - Text, Timestamps, JSON

Video transcript API for LLMs and RAG: YouTube videos or whole channels to JSON with full text and timestamped segments. Also views, likes, upload date, channel subscribers, optional SRT/VTT and RAG chunks. MCP-ready. $2.50 per 1,000 transcripts, failed videos never charged.

**Run it on Apify:** [https://apify.com/om_kh/video-transcript-api](https://apify.com/om_kh/video-transcript-api) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | YouTube video links or IDs (up to 1,000 per run) or playlist links, as a batch run, a live HTTP call or an AI agent tool |
| **We do** | Read YouTube's own captions, human-written first, in the language you choose |
| **You get** | JSON per video: the full text and timestamped segments, ready for summaries, search or AI |
| **It costs** | $2.50 per 1,000 transcripts: 100 videos = **$0.25**, + $0.001 per run from Nov 24, 2026 (no start fee before). Videos without captions are never charged; the first result of every run is free |
| **It does not** | Make a transcript when the video has no captions (that video is reported and costs $0), sign in, or use an API key |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `videos` | array | Video URLs or IDs. Default: `["https://www.youtube.com/watch?v=aircAruvnKk", "https://you`. |
| `channels` | array | Transcribe a whole channel: channel links, @handles, channel IDs or playlist links. |
| `maxVideosPerChannel` | integer | Per channel or playlist. Default: `10`. |
| `publishedAfter` | string | Only channel videos uploaded on or after this date (YYYY-MM-DD). |
| `publishedBefore` | string | Only channel videos uploaded on or before this date (YYYY-MM-DD). |
| `language` | string | Two-letter language code (en, fr, es, de...). |
| `includeSegments` | boolean | Keep the per-line segments with start time and duration. Default: `true`. |
| `includeStats` | boolean | Add likes, comment count and upload date to every transcript (views, description, channel and thumbnail are always included). Default: `true`. |
| `translateTo` | string | Experimental: asks YouTube for its own machine translation into this language code (fr, es, pt-BR...). |
| `outputFormats` | array | Add ready-to-use formats to every transcript: 'srt' and 'vtt' subtitle files as text, and 'chunks' (about 250-word passages with start and end times, ready to embed for RAG). |
| `proxyConfiguration` | object | YouTube blocks datacenter IPs, so this Actor routes through a proxy. Default: `{"useApifyProxy": true}`. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `youtube_url` | string | Same as one entry of `videos` (field name used by other YouTube transcript Actors). |
| `videoUrl` | string | Same as one entry of `videos`. |
| `channel_url` | string | Same as one entry of `channels`. |
| `max_videos` | integer | Same as `maxVideosPerChannel`. |
| `start_date` | string | Same as `publishedAfter` (YYYY-MM-DD). |
| `end_date` | string | Same as `publishedBefore` (YYYY-MM-DD). |
| `targetLanguage` | string | Same as `language`. |
| `include_transcript_text` | boolean | Accepted for compatibility: the plain `text` field is always included. Default: `true`. |

## Example output

A row as shown in the Actor's README:

```json
{
  "video_id": "dQw4w9WgXcQ",
  "video_url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ",
  "title": "Rick Astley - Never Gonna Give You Up (Official Video) (4K Remaster)",
  "channel": "Rick Astley",
  "language": "en",
  "is_generated": false,
  "available_languages": [
    "de-DE",
    "en"
  ],
  "duration_seconds": 211.32,
  "segment_count": 61,
  "word_count": 487,
  "text": "[♪♪♪] ♪ We're no strangers to love ♪ ♪ You know the rules and so do I ♪ ♪ A full commitment's what I'm thinking of ♪ ♪ You wouldn't get t...",
  "segments": [
    {
      "start": 1.36,
      "duration": 1.68,
      "text": "[♪♪♪]"
    },
    {
      "start": 18.64,
      "duration": 3.24,
      "text": "♪ We're no strangers to love ♪"
    }
  ],
  "source": "youtube",
  "channel_id": "UCuAXFkgsw1L7xaCfnd5JJOw",
  "channel_url": "https://www.youtube.com/channel/UCuAXFkgsw1L7xaCfnd5JJOw",
  "description": "The official video for “Never Gonna Give You Up” by Rick Astley. \n\nNever: The Autobiography 📚 OUT NOW! \nFollow this link to get your copy...",
  "keywords": [
    "rick astley",
    "Never Gonna Give You Up"
  ],
  "view_count": 1830096493,
  "video_length_seconds": 213,
  "thumbnail_url": "https://i.ytimg.com/vi/dQw4w9WgXcQ/sddefault.jpg",
  "is_live": false,
  "duration_human": "3:33",
  "hashtags": [
    "NeverGonnaGiveYouUp",
    "OfficialMusicVideo"
  ],
  "is_private": false,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/video-transcript-api").call(run_input={
    "videos": [
        "https://www.youtube.com/watch?v=aircAruvnKk",
        "https://youtu.be/dQw4w9WgXcQ"
    ],
    "proxyConfiguration": {
        "useApifyProxy": true
    }
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~video-transcript-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"videos": ["https://www.youtube.com/watch?v=aircAruvnKk", "https://youtu.be/dQw4w9WgXcQ"], "proxyConfiguration": {"useApifyProxy": true}}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/video-transcript-api` as a tool.

Full documentation, pricing and the latest changes: [YouTube Video Transcript API - Text, Timestamps, JSON](https://apify.com/om_kh/video-transcript-api).

---
title: "YouTube Channel Transcripts Scraper - Every Video to Text"
description: "Bulk YouTube channel and playlist transcripts for RAG and LLM datasets: one timestamped transcript per video from an @handle, channel URL or playlist, with optional SRT/VTT and RAG chunks. Videos without captions never billed. API and MCP ready. $5 per 1,000 transcripts, $1 from Dec 21."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# YouTube Channel Transcripts Scraper - Every Video to Text

Bulk YouTube channel and playlist transcripts for RAG and LLM datasets: one timestamped transcript per video from an @handle, channel URL or playlist, with optional SRT/VTT and RAG chunks. Videos without captions never billed. API and MCP ready. $5 per 1,000 transcripts, $1 from Dec 21.

**Run it on Apify:** [https://apify.com/om_kh/youtube-channel-transcripts](https://apify.com/om_kh/youtube-channel-transcripts) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | A channel (`@name` or link) or a playlist link |
| **We do** | List the channel's or playlist's videos, newest first, and read YouTube's own captions for each |
| **You get** | One row per video: the full transcript as clean text, with timestamped lines if you want them |
| **It costs** | $5 per 1,000 transcripts until 21 December 2026, then **$1 per 1,000**: a 100-video channel = **$0.50** now, **$0.10** from 21 December, + $0.001 per run. Videos without captions are never charged; the first result of every run is free. `maxVideos` (default 50) decides how far back it goes |
| **It does not** | Make a transcript when the video has no captions (that video is reported and costs $0), sign in, or use an API key |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `sources` | array | Channel handles (@3blue1brown), channel URLs, channel IDs (UC...), playlist URLs or playlist IDs. Default: `["@3blue1brown", "https://www.youtube.com/playlist?list=PLZH`. |
| `maxVideos` | integer | Total ceiling across every source, applied after duplicates are removed. Default: `50`. |
| `language` | string | Two-letter code (en, fr, es...). |
| `includeSegments` | boolean | Keep the per-line segments with start time and duration. Default: `true`. |
| `translateTo` | string | Experimental: asks YouTube for its own machine translation into this language code (fr, es, pt-BR...). |
| `outputFormats` | array | Add ready-to-use formats to every transcript: 'srt' and 'vtt' subtitle files as text, and 'chunks' (about 250-word passages with start and end times, ready to embed for RAG). |
| `proxyConfiguration` | object | YouTube blocks datacenter IPs, so this Actor routes through a proxy. Default: `{"useApifyProxy": true}`. |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |

## Example output

A row as shown in the Actor's README:

```json
{
  "video_id": "LKrwhjOI8Nc",
  "video_url": "https://www.youtube.com/watch?v=LKrwhjOI8Nc",
  "title": "There's never been a better time to go into math",
  "channel": "3Blue1Brown",
  "language": "en",
  "is_generated": false,
  "available_languages": [
    "ar",
    "bn"
  ],
  "duration_seconds": 2417.378,
  "segment_count": 1276,
  "word_count": 8859,
  "text": "Well, let's talk about it. It feels like the whole math world is on fire talking about AI in math. I have been thinking about this for a...",
  "segments": [
    {
      "start": 0,
      "duration": 1.432,
      "text": "Well, let's talk about it."
    },
    {
      "start": 1.432,
      "duration": 2.441,
      "text": "It feels like the whole math world is on fire"
    }
  ],
  "source": "youtube",
  "channel_id": "UCYO_jab_esuFRV4b17AJtAw",
  "channel_url": "https://www.youtube.com/channel/UCYO_jab_esuFRV4b17AJtAw",
  "description": "Sharing a few thoughts on the future of math\nThese videos are funded directly by viewers: https://3b1b.co/support\nAn equally valuable for...",
  "keywords": [
    "Mathematics",
    "three blue one brown"
  ],
  "view_count": 2466827,
  "video_length_seconds": 2444,
  "thumbnail_url": "https://i.ytimg.com/vi/LKrwhjOI8Nc/sddefault.jpg",
  "is_live": false,
  "duration_human": "40:44",
  "hashtags": [
    "manim"
  ],
  "is_private": false,
  "allow_ratings": true,
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/youtube-channel-transcripts").call(run_input={
    "sources": [
        "@3blue1brown",
        "https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi"
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
curl -X POST "https://api.apify.com/v2/acts/om_kh~youtube-channel-transcripts/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"sources": ["@3blue1brown", "https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi"], "proxyConfiguration": {"useApifyProxy": true}}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/youtube-channel-transcripts` as a tool.

Full documentation, pricing and the latest changes: [YouTube Channel Transcripts Scraper - Every Video to Text](https://apify.com/om_kh/youtube-channel-transcripts).

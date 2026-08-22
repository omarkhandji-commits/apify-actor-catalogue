[← Catalogue home](../../README.md) · [YouTube & Video family](../youtube-video.md)

# Turn YouTube videos into transcripts for AI workflows

## Problem

You want video content as text — for a RAG index, a summarizer, or search — without transcribing audio yourself.

## Actors used

1. [YouTube Transcript Scraper](https://apify.com/om_kh/youtube-transcript-api) — single video, free
2. [YouTube Channel Transcripts](https://apify.com/om_kh/youtube-channel-transcripts) — scale up to a whole channel

## Inputs

```json
{
  "videos": ["https://www.youtube.com/watch?v=aircAruvnKk"],
  "maxTotalChargeUsd": 0
}
```

## Steps

1. Start with **YouTube Transcript Scraper** on a single video — it's free, so there's no cost to validate the output shape before scaling up.
2. Once you need a channel's worth of content, switch to **YouTube Channel Transcripts** with the channel URL — it covers recent videos in one run, billed per video after a free tier.

## Sample result shape

*Illustrative — derived from the Actor's real dataset schema, not live data.*

```json
{
  "video_id": "aircAruvnKk",
  "title": "But what is a neural network? | Deep learning chapter 1",
  "channel": "3Blue1Brown",
  "language": "en",
  "word_count": 3357,
  "text": "This is a 3. It's sloppily written and rendered at an extremely low resolution..."
}
```

## Try it live

[Public Task example](https://apify.com/om_kh/youtube-transcript-api/examples/youtube-transcript-single-video)

## Code

### curl

```bash
curl "https://api.apify.com/v2/actor-tasks/om_kh~youtube-transcript-single-video/run-sync-get-dataset-items?token=$APIFY_TOKEN" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"videos": ["https://www.youtube.com/watch?v=aircAruvnKk"], "maxTotalChargeUsd": 0}'
```

### Python

```python
import os, requests

token = os.environ["APIFY_TOKEN"]
url = "https://api.apify.com/v2/actor-tasks/om_kh~youtube-transcript-single-video/run-sync-get-dataset-items"
resp = requests.post(url, params={"token": token}, json={
    "videos": ["https://www.youtube.com/watch?v=aircAruvnKk"],
    "maxTotalChargeUsd": 0,
})
transcript = resp.json()
```

## Agent / MCP

This is one of the clearest MCP matches in the catalogue: a natural-language request like "get the transcript of this YouTube video" maps directly to the `youtube-transcript-api` tool.

## Next step

Need to know what people are *saying about* a video topic, not the video itself? See [News & Community](../news-community.md) or [Social Monitoring](../social-monitoring.md).

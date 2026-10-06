[← Catalogue home](index.md) · [YouTube & Video family](youtube-video.md)

# Turn YouTube into text, at any scale

Four real jobs people come to this family for — pick the one that matches what you're actually trying to do, then scale up as needed.

## 1. Get transcript

The fastest path: one video in, clean text out, free.

- **Actor**: [YouTube Transcript Scraper](https://apify.com/om_kh/youtube-transcript-api)
- **Try it live**: [single-video example](https://apify.com/om_kh/youtube-transcript-api/examples/youtube-transcript-single-video)
- **Input**: `{"videos": ["<youtube-url>"], "maxTotalChargeUsd": 0}`

```bash
curl "https://api.apify.com/v2/actor-tasks/om_kh~youtube-transcript-single-video/run-sync-get-dataset-items?token=$APIFY_TOKEN" \
  -X POST -H "Content-Type: application/json" \
  -d '{"videos": ["https://www.youtube.com/watch?v=aircAruvnKk"], "maxTotalChargeUsd": 0}'
```

Need a raw caption/subtitle track instead of prose text? Same free tier, different output shape: [YouTube Subtitles Scraper](https://apify.com/om_kh/youtube-transcript-scraper).

## 2. Feed transcripts into AI/RAG

Same transcript data, pre-shaped for agent pipelines instead of a one-off read.

- **Actor**: [Video Transcript API](https://apify.com/om_kh/video-transcript-api) — same free transcript extraction, output structured for chunking/embedding.
- **Actor**: [YouTube Transcript Scraper](https://apify.com/om_kh/youtube-transcript-api) also exposes an **MCP tool** — a natural-language agent request like *"get the transcript of this YouTube video"* maps to it directly, no custom integration code.

## 3. Process channel transcripts

Scale from one video to a channel's worth of recent uploads in a single run.

- **Actor**: [YouTube Channel Transcripts](https://apify.com/om_kh/youtube-channel-transcripts) — covers ~15 recent videos per run, 1 free, then $1/1K.
- **Try it live**: [channel-transcripts-recent-videos example](https://apify.com/om_kh/youtube-channel-transcripts/examples/channel-transcripts-recent-videos)

Natural next step from job #1: start with a single video on **YouTube Transcript Scraper** to confirm the output shape costs you nothing, then move to **YouTube Channel Transcripts** once you need a whole channel instead of one URL at a time.

## 4. Content/upload monitoring

Not transcripts — the upload signal itself, and everything downstream of a new video existing.

- **Actor**: [YouTube Channel Videos Scraper](https://apify.com/om_kh/youtube-channel-videos-scraper) — a channel's videos, Shorts and live streams, newest, most popular or oldest first, with exact views and likes, plus the channel's profile (no transcript).
- **Actor**: [YouTube Search Scraper](https://apify.com/om_kh/vigia-youtube-search-monitor) — discover videos, Shorts and live streams by topic, sorted by relevance, views or date, with YouTube's own filters and optional likes and subscriber counts.
- **Actor**: [YouTube Comments Scraper](https://apify.com/om_kh/youtube-comments-scraper) — the audience reaction to a specific video: up to 50,000 comments with their replies, newest or top first, with a date limit.

Chain it: **YouTube Channel Videos Scraper** flags a new upload → feed that video URL into **YouTube Transcript Scraper** (job #1) → you have searchable text the moment a channel publishes, with no manual step in between.

## Automation status (honest, not aspirational)

| Asset | Status |
|---|---|
| Apify Actors (all 7 in this family) | **PUBLIC** — live on the Apify Store, linked above |
| Public Task examples | **PUBLIC** — 4 live Tasks across this family (see links above) |
| n8n workflows (internal) | Real-tested against live Apify data this project's own n8n instance — not a schema-only design |
| n8n workflow template files (downloadable/importable) | Available: [YouTube transcripts → Google Sheets](workflows/n8n/youtube-transcripts-to-google-sheets.json) — see [all n8n templates](workflows/index.md) |
| Make scenarios | `PAUSED_NO_USER_ACCESS` — see the private tracker; not part of this public catalogue regardless |

## Agent / MCP

This is one of the clearest MCP matches in the whole catalogue: "get the transcript of this YouTube video," "summarize this channel's recent uploads," and "tell me when this channel posts something new" all map directly onto the Actors above with no custom glue code.

## Related

- [YouTube & Video family page](youtube-video.md) for the fuller sibling comparison
- [Workflow example: Turn YouTube videos into transcripts for AI workflows](examples/youtube-example.md)
- [News & Community](news-community.md) if the goal is tracking what's being said *about* a topic, not the video content itself

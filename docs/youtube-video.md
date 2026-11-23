[← Catalogue home](index.md)

# YouTube & Video

## What problem this solves

Turning YouTube video content into text — for search, summarization, RAG pipelines, or just reading instead of watching — plus tracking channels, search results, and comments over time.

## When to use it

- You need the **transcript of one video** (no API key).
- You need transcripts for **every recent video on a channel**, not just one.
- You want to **watch a channel** and get notified only of new uploads.
- You want to **search YouTube** by topic rather than watch a known channel.
- You want the **comments** on a specific video.

## Actors in this family

| Actor | Best for | Pricing |
|---|---|---|
| [YouTube Transcript Scraper](https://apify.com/om_kh/youtube-transcript-api) | Single videos or whole channels (up to 500 videos each, date range), with views, likes, upload date and channel subscribers | **$1 per 1,000 transcripts, $2 per 1,000 from 13 December 2026.** 100 videos = $0.10 today, $0.20 from 13 December |
| [Video Transcript API](https://apify.com/om_kh/video-transcript-api) | Same transcript, structured for RAG/agent pipelines | $2.50 per 1,000 transcripts: 100 videos = **$0.25**, + $0.001 per run from Nov 24, 2026 (no start fee before) |
| [YouTube Subtitles Scraper](https://apify.com/om_kh/youtube-transcript-scraper) | Raw caption/subtitle track instead of prose text | $2.50 per 1,000 subtitles: 100 videos = **$0.25**, + $0.001 per run from Nov 24, 2026 (no start fee before) |
| [YouTube Channel Transcripts](https://apify.com/om_kh/youtube-channel-transcripts) | Transcripts for ~15 recent videos on a channel in one run | $5 per 1,000 transcripts: a 100-video channel = **$0.50**, + $0.001 per run |
| [YouTube Channel Videos Scraper](https://apify.com/om_kh/youtube-channel-videos-scraper) | A channel's videos, Shorts and live streams, by date or popularity, with channel info | **$0.50 per 1,000 videos** (from 4 December 2026: $1.50 per 1,000) + $0.001 per run |
| [YouTube Search Scraper](https://apify.com/om_kh/vigia-youtube-search-monitor) | Search videos, Shorts and live streams by topic, with filters and sort | **$0.50 per 1,000 videos** + $0.001 per run |
| [YouTube Comments Scraper](https://apify.com/om_kh/youtube-comments-scraper) | Bulk-export a video's comments and replies (up to 50,000) | **$0.40 per 1,000 comments** + $0.001 per run |
| [YouTube Channel Search Scraper](https://apify.com/om_kh/youtube-channel-search-scraper) | Find channels by keyword, filter by subscribers, optional country, links, business email and latest uploads | $0.50 per 1,000 channels, + $0.002 per channel with the option on, + $0.001 per run |
| [YouTube Creator Lead Finder](https://apify.com/om_kh/youtube-creator-lead-finder) | Qualified creators in a niche with views, engagement and verified contact | $4 per 1,000 qualified creators + $0.002 per verified contact + $0.001 per run |

## Telling the siblings apart

**YouTube Transcript Scraper**, **Video Transcript API**, and **YouTube Subtitles Scraper** all pull the same underlying caption data for a single video, at $0 — they differ only in output shape: prose text, RAG-ready structure, or a raw caption/subtitle track. **YouTube Channel Transcripts** is the bulk version: point it at a channel and get several videos' transcripts in one run, billed per video after a free tier. **YouTube Channel Videos Scraper** does *not* fetch transcripts at all — it watches a channel for new uploads (title, URL, publish date), the notification layer. **YouTube Search Scraper** is for when you don't know the channel yet and want to discover videos by topic. **YouTube Comments Scraper** is a separate axis entirely: the audience reaction to a video, not the video's own content.

## Recommended starting point

[**YouTube Transcript Scraper**](https://apify.com/om_kh/youtube-transcript-api) — single video, the simplest way to try this family. Try it: [live example](https://apify.com/om_kh/youtube-transcript-api/examples/youtube-transcript-single-video). Once you need more than one video, [YouTube Channel Transcripts](https://apify.com/om_kh/youtube-channel-transcripts) is the natural next step — same underlying data, scaled to a whole channel in one run.

## Workflow example

See [Turn YouTube videos into transcripts for AI workflows](examples/youtube-example.md) for the full walkthrough (single video → whole-channel scale-up), or [Turn YouTube into text, at any scale](automate-youtube-transcripts.md) for all four jobs this family covers (get transcript, feed AI/RAG, process channel transcripts, monitor for new uploads) in one place.

## Agent / MCP

`youtube-transcript-api` exposes an MCP tool for "get the transcript of this YouTube video" — a natural-language agent request maps to it directly without custom integration code.

## Related family

Turning video into text overlaps with [News & Community](news-community.md) if your goal is monitoring what's being *said about* a topic rather than the video content itself.

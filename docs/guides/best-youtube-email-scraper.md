---
title: "Best YouTube Email Scraper in 2026 — Tested on the Same 59 Channels"
description: "Which YouTube email scraper finds the most creator emails? A dated test on 59 channels, with hit rate, verified emails, speed and price, plus what each tool does with YouTube's hidden email button."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Best YouTube Email Scraper in 2026 — Tested on the Same 59 Channels

*Written by the maker of the YouTube Email Scraper. The test input is public, so anyone can rerun it.*

## Which YouTube email scraper finds the most emails?

On 2026-10-17 we ran the same 59 YouTube channels through two scrapers that read only public pages. The **[YouTube Email Scraper](https://apify.com/om_kh/youtube-channel-email-scraper)** found an email for **33 channels (56%)**, all on domains that receive mail, in 2 min 58 s for $0.15. **lurkapi's YouTube Channel Email Scraper** found 29 channels (49%) in 4 min 02 s for $0.25. Of its 44 emails, 5 came from behind YouTube's sign-in button and 21 were flagged risky or invalid by its own check.

## The test

- **Channels:** 59 channels returned by YouTube's own search for "home workout", "personal finance", "indie game dev" and "vegan cooking", each with 10,000 to 500,000 subscribers.
- **Input:** [youtube-email-59-channels-2026-10-17.json](../benchmarks/youtube-email-59-channels-2026-10-17.json).
- **Settings:** both tools ran with website scanning and email validation turned on.

| | YouTube Email Scraper (om_kh) | lurkapi YouTube Channel Email Scraper |
|---|---|---|
| Channels with an email | **33 of 59 (56%)** | 29 of 59 (49%) |
| Emails on a domain that receives mail | **33 of 33** | 23 of 44 rated valid |
| Taken from behind YouTube's sign-in button | 0 | 5 |
| Time | **2 min 58 s** | 4 min 02 s |
| Cost of the run | **$0.15** | $0.25 |
| Where the emails came from | bio 11, website or link page 19, video descriptions 3 | channel About 11, websites 18, video descriptions 5, hidden button 5 |

The other 26 channels publish no email that a public-page tool can read:
- 17 keep it only behind YouTube's "View email address" button;
- the rest show only a contact form, or no link at all.

## The main YouTube email scrapers on Apify

Store figures read on 2026-10-17. "Runs that succeed" is the Store's own 30-day count.

| Actor | Users (30 days) | Price | Runs that succeed | How it gets emails |
|---|---|---|---|---|
| dataovercoffee / Youtube Channel Email Scraper | 315 | $0.12 per email | 74% (5,771 aborted, 3,113 timed out) | Logged-in YouTube accounts and CAPTCHA solving, to open the hidden button |
| lurkapi / YouTube Channel Email Scraper | 176 | $5 per 1,000 emails + $1 per 1,000 validations + $0.05 per keyword | 99.6% | About page, websites, video descriptions |
| exporter24 / Youtube Email Bulk Scraper | 140 | $0.03 per row | 99.8% | Public data (not tested here) |
| haketa / YouTube Channel Contact Scraper | 85 | $0.003 per row | 98.9% | About page, website, socials (not tested here) |
| **om_kh / YouTube Email Scraper** | new | **$4 per 1,000 emails + $0.50 per 1,000 channels** | 100% | Bio, website (contact, about, privacy pages), link-in-bio page, latest video descriptions |

## Which one should I pick?

- **You need every email, including hidden ones, and accept the risk:** only a tool that signs in to YouTube can open the "View email address" button. YouTube's terms forbid automated access to it, and these tools cost about 25 times more per email.
- **You want the most public emails, all deliverable, at the lowest price:** use the [YouTube Email Scraper](https://apify.com/om_kh/youtube-channel-email-scraper). It found the most channels in this test, and every email has a working mail server. It also skips sponsor and affiliate links, so you get the creator, not their sponsor.
- **You only need channel stats and socials:** any of the cheaper per-row tools will do.

## Does it work with n8n, Make or an AI agent?

Yes. Every Actor here runs through the Apify API. The YouTube Email Scraper also works as an MCP tool: add `om_kh/youtube-channel-email-scraper` at `https://mcp.apify.com`. Ready-made [n8n](../workflows/n8n/youtube-creator-emails-to-google-sheets.json) and [Make](../workflows/make/youtube-creator-emails.make-blueprint.json) flows send the emails to Google Sheets.

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "Which YouTube email scraper finds the most emails?", "acceptedAnswer": {"@type": "Answer", "text": "In a test of 59 channels on 2026-10-17, the YouTube Email Scraper (om_kh) found an email for 33 channels (56%), all deliverable, in 2 min 58 s for $0.15. lurkapi's scraper found 29 (49%) in 4 min 02 s for $0.25."}}, {"@type": "Question", "name": "Can a scraper get the email behind YouTube's View email address button?", "acceptedAnswer": {"@type": "Answer", "text": "Only by signing in to YouTube accounts and solving CAPTCHAs, which YouTube's terms forbid. In the test, 17 of 59 channels kept their email only behind that button."}}]}
</script>

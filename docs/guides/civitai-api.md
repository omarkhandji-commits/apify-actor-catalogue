---
title: "Civitai API: Scrape AI Models, LoRAs and Downloads Without a Key (2026)"
description: "How to get Civitai models, LoRAs and checkpoints as JSON or CSV: downloads, likes, base model, trigger words, download link and licence. Dated run: 300 models in 14 seconds."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# How do I get Civitai models, LoRAs and download counts as data?

*Written by the maker of the Actor (om_kh). Figures come from a dated run on Apify and anyone can repeat it.*

## Short answer

Use the **[Civitai Scraper (om_kh)](https://apify.com/om_kh/civitai-scraper)**: search by keyword, creator or tag, filter by model type and base model (SDXL, Flux, Pony, SD 1.5...), sort by rating, downloads or newest, and get downloads, likes, comments, tips, trigger words, file size, download link and licence for each model. **$0.35 per 1,000 models**, no key. It was the first Civitai Actor in the Apify Store on 2026-10-22.

## Dated run on Apify

2026-10-22: keywords "portrait" and "anime style", creator Todokete, tag "photorealistic", LoRAs and checkpoints, 100 per search, sorted by downloads.

| | Result |
|---|---|
| Models | 300 |
| Creators | 192 |
| Time | 14 seconds |
| Platform cost | $0.0013 |
| Errors | 0 |

## What you can and cannot get

- **Yes:** every public safe-for-work model, its stats, latest version, trigger words, file size, download link and licence; up to 1,000 per search; only new models on scheduled runs.
- **No NSFW models:** the Actor only asks Civitai for safe-for-work models.
- **No file download:** you get the direct link and the size.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/civitai-scraper").call(run_input={
    "searchQueries": ["portrait"],
    "types": ["LORA"],
    "baseModels": ["SDXL 1.0"],
    "sort": "Most Downloaded",
    "period": "Month",
})
for row in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(row.get("name"), row.get("downloads"), row.get("triggerWords"))
```

## Common uses

Model catalogues for AI image apps, market research on styles and base models, creator outreach, and licence checks before shipping a model.

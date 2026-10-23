---
title: "Most Downloaded Civitai LoRAs and Checkpoints by Base Model (How to Export, 2026)"
description: "Export the most downloaded Civitai LoRAs and checkpoints for SDXL, Flux or Pony to CSV, with downloads, likes and trigger words."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# How do I list the most downloaded Civitai LoRAs for one base model?

Use the **[Civitai Scraper (om_kh)](https://apify.com/om_kh/civitai-scraper)** with `sort: Most Downloaded`, a `period` (AllTime, Year, Month, Week, Day), `types: ["LORA"]` and `baseModels` (for example `SDXL 1.0`, `Flux.1 D`, `Pony`). Each row has downloads, likes, comments, tips, trigger words, file size, download link and licence. **$2 per 1,000 models**; safe-for-work models only.

Dated test on 2026-10-22: 4 searches returned **300 models from 192 creators in 14 seconds**.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/civitai-scraper").call(run_input={
    "browseAll": True, "types": ["LORA"], "baseModels": ["SDXL 1.0"], "sort": "Most Downloaded", "period": "Month"})
```

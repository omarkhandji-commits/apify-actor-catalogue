---
title: "How to Export Civitai Models to CSV or Google Sheets (No API Key, 2026)"
description: "Export Civitai models of a creator, tag or keyword to CSV, Excel or Google Sheets, with stats, licence and download links."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# How do I export all models of a Civitai creator or tag to a spreadsheet?

Give the **[Civitai Scraper](https://apify.com/om_kh/civitai-scraper)** a creator username, a tag or keywords; download the dataset as CSV or Excel, or schedule the ready n8n workflow that appends the week's top models to Google Sheets: [civitai-top-models-to-google-sheets.json](../workflows/n8n/civitai-top-models-to-google-sheets.json). Up to 1,000 models per search, with downloads, likes, base model, trigger words, licence (commercial use, credit required) and download link.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/civitai-scraper").call(run_input={"creators": ["Todokete"], "maxModelsPerSearch": 1000})
print(client.dataset(run["defaultDatasetId"]).get_items_as_bytes(item_format="csv")[:200])
```

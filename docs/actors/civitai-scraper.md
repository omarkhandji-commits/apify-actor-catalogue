---
title: "Civitai Scraper - AI Models, Downloads, LoRAs $0.35/1K"
description: "Scrape Civitai AI image models by keyword, creator or tag: checkpoints, LoRAs, embeddings with downloads, likes, comments, tips, base model (SDXL, Flux, Pony), trigger words, file size, download link, licence and preview image. No login. $0.35 per 1,000 models."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# Civitai Scraper - AI Models, Downloads, LoRAs $0.35/1K

Scrape Civitai AI image models by keyword, creator or tag: checkpoints, LoRAs, embeddings with downloads, likes, comments, tips, base model (SDXL, Flux, Pony), trigger words, file size, download link, licence and preview image. No login. $0.35 per 1,000 models.

**Run it on Apify:** [https://apify.com/om_kh/civitai-scraper](https://apify.com/om_kh/civitai-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords, creators, tags, or model ids and links |
| **We do** | Read Civitai's AI image models |
| **You get** | One row per model (or per image, or per creator, in the Images and Creators modes): type, creator, tags, downloads, likes, comments, tips, base model, trigger words, file size, format, SHA256 hash and safety scans, every file, download link, licence, preview and sample images |
| **It costs** | **$0.35 per 1,000 models** + $0.001 per run. Searches that fail are never charged. No supplier fee |
| **It does not** | Download the model files for you or sign in to Civitai |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `mode` | string | Models: by keyword, creator, tag or id. Default: `"models"`. |
| `models` | array | Civitai model ids (4201) or links (https://civitai.com/models/4201/...). |
| `searchQueries` | array | Words to search model names and tags, as on civitai.com/models. Default: `["portrait", "anime style"]`. |
| `creators` | array | Civitai usernames: every model they published. |
| `tags` | array | Civitai tags (style, character, photorealistic, concept...). |
| `types` | array | Only these model types. |
| `baseModels` | array | Only models for these base models, exactly as Civitai writes them: SDXL 1.0, Flux.1 D, Pony, SD 1.5, Illustrious... |
| `sort` | string | Civitai's own order for model searches. Default: `"Highest Rated"`. |
| `period` | string | Rank models by their rating or downloads over this period. Default: `"AllTime"`. |
| `maxModelsPerSearch` | integer | Up to 1,000 models, images or creators for each keyword, creator, tag or model. Default: `100`. |
| `browseAll` | boolean | With no keyword, creator, tag or model: the top models (or images) of the whole site for the sort, period and filters above. Default: `false`. |
| `includeDescription` | boolean | The creator's description as plain text (up to 2,000 characters). Default: `true`. |
| `includeAllVersions` | boolean | Adds allVersions: each version's base model, trigger words, downloads, likes, file, hash and safe previews (the row already has the latest version). Default: `false`. |
| `maxImagesPerModel` | integer | Adds up to this many safe images to each model row, with likes, hearts and comments (0 = none). Default: `0`. |
| `imageSort` | string | Order of images, in Images mode and for 'Images per model'. Default: `"Most Reactions"`. |
| `onlyNewModels` | boolean | Each run delivers only models (or images, or creators) you have not received yet. Default: `false`. |
| `monitorId` | string | With 'Only new models', keeps separate memories for separate schedules. |
| `maxTotalChargeUsd` | number | The run stops before it would cost more than this. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "model",
  "modelId": 5658,
  "name": "(hidden here)",
  "url": "https://civitai.com/models/5658",
  "modelType": "LORA",
  "creator": "Todokete",
  "creatorUrl": "https://civitai.com/user/Todokete",
  "tags": [
    "style",
    "persona"
  ],
  "downloads": 4961,
  "thumbsUp": 761,
  "thumbsDown": 1,
  "comments": 15,
  "tips": 0,
  "baseModels": [
    "SD 1.5"
  ],
  "versions": 2,
  "latestVersion": "v1.0",
  "latestVersionId": 18823,
  "latestBaseModel": "SD 1.5",
  "latestPublishedAt": "2023-03-05T09:20:59.604Z",
  "triggerWords": [
    "portrait",
    "solo"
  ],
  "downloadUrl": "https://civitai.com/api/download/models/18823",
  "fileSizeMb": 18.7,
  "fileFormat": "SafeTensor",
  "imageUrl": "https://image.civitai.com/xG1nkqKTMzGDvpLrqFT7WA/7857fc6e-4fd4-4663-3d80-44c155938700/original=true/196065.jpeg",
  "commercialUse": [
    "Image",
    "RentCivit"
  ],
  "allowDerivatives": true,
  "creditRequired": false,
  "description": "v1.0 Release! LoRA was trained on, and all images were generated with, Counterfeit v2.5 All examples use the seed of \"1\" with a batch siz...",
  "searchQuery": "portrait"
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/civitai-scraper").call(run_input={
    "searchQueries": [
        "portrait",
        "anime style"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~civitai-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchQueries": ["portrait", "anime style"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/civitai-scraper` as a tool.

Full documentation, pricing and the latest changes: [Civitai Scraper - AI Models, Downloads, LoRAs $0.35/1K](https://apify.com/om_kh/civitai-scraper).

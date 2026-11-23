---
title: "HelloFresh Recipes Scraper - Ingredients, Calories $2/1K"
description: "Scrape HelloFresh recipes in 18 countries by keyword: ingredients with quantities, calories and full nutrition, allergens, utensils, step-by-step instructions, prep and total time, difficulty, cuisine, tags, rating and image. No login. $2 per 1,000 recipes."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# HelloFresh Recipes Scraper - Ingredients, Calories $2/1K

Scrape HelloFresh recipes in 18 countries by keyword: ingredients with quantities, calories and full nutrition, allergens, utensils, step-by-step instructions, prep and total time, difficulty, cuisine, tags, rating and image. No login. $2 per 1,000 recipes.

**Run it on Apify:** [https://apify.com/om_kh/hellofresh-recipes-scraper](https://apify.com/om_kh/hellofresh-recipes-scraper) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Keywords, weeks or recipe and menu links, and countries (18 HelloFresh countries) |
| **We do** | Read HelloFresh recipes |
| **You get** | One row per recipe: ingredients with quantities, calories and full nutrition, allergens, utensils, step-by-step instructions, prep and total time, difficulty, cuisine, tags, rating and photo |
| **It costs** | $2 per 1,000 recipes + $0.001 per run. Searches that fail and recipes your filters drop are never charged. No supplier fee |
| **It does not** | Order meal kits or sign in to HelloFresh |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `searchQueries` | array | Dishes, ingredients or styles, as on hellofresh.com/recipes. Default: `["salmon", "pasta"]`. |
| `weeks` | array | ISO weeks (2026-W47), 'current' or 'next': every recipe on that week's menu in each chosen country, with its menu and position. |
| `startUrls` | array | Links from any HelloFresh country site: recipe pages (…/recipes/name-) or menu pages (…/menus or …/menus/2026-W47). |
| `countries` | array | HelloFresh countries to search (and to read weekly menus for), each in its own language and units: us, gb, ca, au and 14 more. Default: `["us"]`. |
| `maxRecipesPerSearch` | integer | Up to 1,000 recipes per keyword and country. Default: `100`. |
| `fullRecipesOnly` | boolean | Leave out ready-to-heat meals and add-ons that have no cooking steps (keyword searches only: recipes you ask for by link or menu are always kept). Default: `true`. |
| `maxTotalTimeMinutes` | integer | Only recipes ready in this time or less. |
| `maxCalories` | integer | Only recipes at or below this many kcal per serving. |
| `maxTotalChargeUsd` | number | The run stops before it would cost more than this. |

## Example output

A row as shown in the Actor's README:

```json
{
  "status": "ok",
  "type": "recipe",
  "recipeId": "6ab5620d8a36ef62cf58c018",
  "name": "(hidden here)",
  "headline": "with Potatoes, Thyme & Old Bay Croutons",
  "url": "https://www.hellofresh.com/recipes/chesapeake-2x-salmon-and-corn-chowder-6ab5620d8a36ef62cf58c018",
  "imageUrl": "https://d3hvwccx09j84u.cloudfront.net/0,0/image/HFUSRC_R18949-1_Hero_ChesapeakeTilapiaAndCornChowder_W49_71_2026_Web-32738bf9.jpg",
  "country": "us",
  "category": "Seafood",
  "cuisines": [
    "North American"
  ],
  "tags": [
    "pescatarian"
  ],
  "difficulty": 2,
  "prepTimeMinutes": 40,
  "totalTimeMinutes": 10,
  "ratingsCount": 0,
  "favorites": 0,
  "servings": 2,
  "ingredients": [
    {
      "name": "(hidden here)",
      "amount": 1,
      "unit": "unit",
      "shipped": true
    },
    {
      "name": "(hidden here)",
      "amount": 1,
      "unit": "unit",
      "shipped": true
    }
  ],
  "allergens": [
    "Fish",
    "Shellfish"
  ],
  "nutrition": {
    "Calories": {
      "amount": 1360,
      "unit": "kcal"
    },
  ...
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/hellofresh-recipes-scraper").call(run_input={
    "searchQueries": [
        "salmon",
        "pasta"
    ],
    "countries": [
        "us"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~hellofresh-recipes-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"searchQueries": ["salmon", "pasta"], "countries": ["us"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/hellofresh-recipes-scraper` as a tool.

Full documentation, pricing and the latest changes: [HelloFresh Recipes Scraper - Ingredients, Calories $2/1K](https://apify.com/om_kh/hellofresh-recipes-scraper).

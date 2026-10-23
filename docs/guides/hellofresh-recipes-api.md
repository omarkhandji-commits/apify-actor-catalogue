---
title: "HelloFresh Recipes API: Ingredients, Calories and Steps as Data (2026)"
description: "How to get HelloFresh recipes as JSON or CSV in 18 countries: ingredients with quantities, calories and nutrition, allergens and steps. Dated run: 249 recipes in 26 seconds."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# How do I get HelloFresh recipes with ingredients and nutrition as data?

*Written by the maker of the Actor (om_kh). Figures come from a dated run on Apify and anyone can repeat it.*

## Short answer

Use the **[HelloFresh Recipes Scraper (om_kh)](https://apify.com/om_kh/hellofresh-recipes-scraper)**: search any dish or ingredient in 18 HelloFresh countries and get ingredients with quantities, calories and full nutrition, allergens, utensils, steps, times, difficulty, cuisine and rating, with time and calorie filters. **$2 per 1,000 recipes**, no login. It was the first HelloFresh Actor in the Apify Store on 2026-10-22.

## Dated run on Apify

2026-10-22: salmon, chicken and "vegetarian pasta" in the US, the UK and Germany, 50 per search.

| | Result |
|---|---|
| Recipes | 249 (UK 100, US 75, Germany 74) |
| With ingredient quantities | 249 of 249 |
| With calories | 249 of 249 |
| Time | 26 seconds |
| Platform cost | $0.0004 |

## What you can and cannot get

- **Yes:** full recipes with quantities for one serving size, nutrition per serving, allergens and steps, in each country's language and units.
- **One phrase per keyword:** HelloFresh's search matches the words as one phrase; "vegetarian pasta" found nothing, "pasta" works.
- **No account data:** menus of a customer's box are private.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/hellofresh-recipes-scraper").call(run_input={
    "searchQueries": ["salmon", "pasta"],
    "countries": ["us", "gb"],
    "maxTotalTimeMinutes": 30,
    "maxCalories": 700,
})
for row in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(row["name"], row["calories"], row["totalTimeMinutes"])
```

## Common uses

Recipe and meal-planning apps, nutrition tools, AI cooking assistants, and food market research by country.

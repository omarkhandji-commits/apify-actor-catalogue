---
title: "HelloFresh Recipes Dataset: Ingredients, Steps and Photos for 18 Countries (2026)"
description: "Build a HelloFresh recipes dataset with ingredients and quantities, steps, photos, cuisine and ratings for meal-planning apps or AI."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# How do I build a dataset of HelloFresh recipes?

Search the dishes and ingredients you need with the **[HelloFresh Recipes Scraper](https://apify.com/om_kh/hellofresh-recipes-scraper)** in any of 18 countries (each in its own language and units). Every row has ingredients with quantities for one serving size, steps, photo, cuisine, tags, difficulty, prep and total time, rating and nutrition. HelloFresh's search matches each keyword as one phrase, so use one dish or ingredient per keyword (salmon, pasta, tacos).

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/hellofresh-recipes-scraper").call(run_input={
    "searchQueries": ["salmon", "pasta", "tacos"], "countries": ["us", "gb", "de"], "maxRecipesPerSearch": 1000})
```

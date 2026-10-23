---
title: "HelloFresh Nutrition Data: Calories and Macros per Recipe as CSV (2026)"
description: "Get calories, fat, carbohydrate, protein and sodium per serving for HelloFresh recipes in 18 countries, with allergens and ingredients."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# How do I get calories and nutrition for HelloFresh recipes?

The **[HelloFresh Recipes Scraper (om_kh)](https://apify.com/om_kh/hellofresh-recipes-scraper)** returns, for each recipe, `calories` and the full `nutrition` per serving (energy, fat, saturated fat, carbohydrate, sugar, fiber, protein, sodium...), allergens and ingredients with quantities. Filter with `maxCalories` and `maxTotalTimeMinutes`. **$2 per 1,000 recipes**.

Dated test on 2026-10-22: 249 recipes in the US, UK and Germany, **every one with calories and ingredient quantities**, in 26 seconds.

## Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("om_kh/hellofresh-recipes-scraper").call(run_input={"searchQueries": ["chicken"], "maxCalories": 600})
for r in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(r["name"], r["calories"], r["nutrition"].get("Protein"))
```

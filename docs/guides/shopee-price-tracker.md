---
title: "Shopee Price Tracker — Exact Price, Variants and Units Sold by Product Link"
description: "Track Shopee prices: give product links, run it daily and get each day's exact price, SKU variants, units sold, rating and seller, as JSON, CSV or Google Sheets."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# Shopee Price Tracker — Exact Price, Variants and Units Sold by Product Link

## How do I track Shopee prices?

Use the **Shopee Price Tracker** robot on Apify. Give it Shopee product links or item IDs; every run returns one row per product with the exact price (with a `price_verified` flag), rating, SKU variants, units sold, favourites, category, images and the seller's profile. Schedule it daily on the same links and keep the runs, or send them to Google Sheets, to build the price history: the robot itself does not store past prices.

**Try it:** [Shopee Price Tracker on Apify](https://apify.com/om_kh/shopee-product-detail-scraper) — click *Try for free*, the input is prefilled.

## Step by step

1. Open [Shopee Price Tracker](https://apify.com/om_kh/shopee-product-detail-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "productUrls": [
    "https://shopee.sg/-SG-STOCK-Logitech-M331-SILENT-PLUS-Wireless-Mouse-2.4GHz-with-USB-Receiver-Optical-Tracking-1-YEAR-LOCAL-WARRANTY-i.12496837.29695565289"
  ]
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/shopee-product-detail-scraper").call(run_input={
  "productUrls": [
    "https://shopee.sg/-SG-STOCK-Logitech-M331-SILENT-PLUS-Wireless-Mouse-2.4GHz-with-USB-Receiver-Optical-Tracking-1-YEAR-LOCAL-WARRANTY-i.12496837.29695565289"
  ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~shopee-product-detail-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"productUrls": ["https://shopee.sg/-SG-STOCK-Logitech-M331-SILENT-PLUS-Wireless-Mouse-2.4GHz-with-USB-Receiver-Optical-Tracking-1-YEAR-LOCAL-WARRANTY-i.12496837.29695565289"]}'
```

## What you get

- `title`
- `product_url`
- `list_price`
- `exact_price`
- `price_verified`
- `currency`
- `status`

## Price

Pay per product delivered; see the Pricing tab of the robot for today's price. Apify also bills the supplier Actor this robot runs for you, at its own price. An item that returns an error is never charged. Set `maxTotalChargeUsd` to cap a run.

## Use cases

- Watch competitors' prices on Shopee every day
- Check price changes before and after a sale
- Feed product prices into a spreadsheet or dashboard

## From an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/shopee-product-detail-scraper` as a tool.
The agent sends the same JSON input and gets the rows back.

## FAQ

**Does it keep the price history?**  
No. Each run gives the current price; keep the runs or send them to Google Sheets to see the history.

**Does it need a Shopee account?**  
No. It does not sign in or place orders.

## Related

- [AliExpress Product Search Scraper - Real Prices, Units Sold](https://apify.com/om_kh/aliexpress-search-scraper)

<script type="application/ld+json">
{"@context": "https://schema.org", "@type": "FAQPage", "mainEntity": [{"@type": "Question", "name": "How do I track Shopee prices?", "acceptedAnswer": {"@type": "Answer", "text": "Use the Shopee Price Tracker robot on Apify. Give it Shopee product links or item IDs; every run returns one row per product with the exact price (with a `price_verified` flag), rating, SKU variants, units sold, favourites, category, images and the seller's profile. Schedule it daily on the same links and keep the runs, or send them to Google Sheets, to build the price history: the robot itself does not store past prices."}}, {"@type": "Question", "name": "Does it keep the price history?", "acceptedAnswer": {"@type": "Answer", "text": "No. Each run gives the current price; keep the runs or send them to Google Sheets to see the history."}}, {"@type": "Question", "name": "Does it need a Shopee account?", "acceptedAnswer": {"@type": "Answer", "text": "No. It does not sign in or place orders."}}]}
</script>

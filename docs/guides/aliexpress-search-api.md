---
title: "AliExpress Search API — Real Seller Prices, Units Sold, Ratings"
description: "Get AliExpress products for any keyword with the seller's real price (not the new-shopper teaser), units sold, rating, photos, free shipping and delivery estimate, as JSON or CSV. Tested against the most-used scraper."
---

[← All guides](index.md) · [All Actors](../all-actors.md)

# AliExpress Search API — Real Seller Prices, Units Sold, Ratings

## How do I scrape AliExpress search results with real prices?

Use the **AliExpress Search Scraper**. Give it keywords or AliExpress search links, pick a sort (best match, most
orders, price low or high) and optional filters (price range in USD, minimum rating, minimum units sold). It returns
one row per unique product with the **seller's real price**, list price, discount, rating, units sold, Choice flag,
delivery estimate and badges such as "Lowest price in 90 days", with ads flagged or removed. Up to 3,000 products per
search. $3 per 1,000 products, the first 10 of every run free. No login.

Why "real price": AliExpress shows logged-out visitors a one-time new-shopper deal on many products (on 15 October
2026, 40-55% of "phone case" results showed $0.33 to $1.09 teasers). This Actor returns the seller's normal price in
`price` and the teaser apart in `newShopperPrice`.

**Try it:** [AliExpress Search Scraper on Apify](https://apify.com/om_kh/aliexpress-search-scraper) — click *Try for free*, the input is prefilled.

## Do AliExpress scrapers return the real price?

Not always. Logged-out visitors are shown a one-time "new shopper" teaser on many products, and a scraper that reads
the shown price returns that teaser. Measured on 2026-10-17 on "wireless earbuds" (48 products):

| | AliExpress Search Scraper (om_kh) | kawsar AliExpress Search Scraper (most used, 1,677 users) |
|---|---|---|
| Prices that are new-shopper teasers | **0** (teaser kept in `newShopperPrice`) | **19 of 48**, 16 under $2 |
| Median price | **$13.25** | $4.43 |
| Units sold | 47 of 48 | 44 of 48 |
| Photo gallery | 48 of 48 | 48 of 48 |
| Runs that succeed (30 days) | 100% | 84% |
| Price per 1,000 products | **$3** | $8 |

For dropshipping or resale research, a teaser price makes margins look about 3 times better than they are.

## Step by step

1. Open [AliExpress Search Scraper](https://apify.com/om_kh/aliexpress-search-scraper) and click **Try for free** (an Apify account is free).
2. Paste this input (or fill the form):

```json
{
  "searchTerms": ["phone case", "led strip"],
  "maxProductsPerSearch": 300,
  "sortBy": "orders",
  "minRating": 4.5,
  "includeSponsored": false
}
```

3. Click **Start**. Download the results as JSON, CSV or Excel, or read them from the API.

## From Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/aliexpress-search-scraper").call(run_input={
    "searchTerms": ["phone case", "led strip"],
    "maxProductsPerSearch": 300,
    "sortBy": "orders",
    "minRating": 4.5,
    "includeSponsored": False,
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item["title"][:60], item["price"], item.get("soldCount"))
```

## With one HTTP call (cURL)

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~aliexpress-search-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>"   -H "Content-Type: application/json"   -d '{"searchTerms": ["yoga mat"], "maxProductsPerSearch": 60, "sortBy": "orders"}'
```

## What one row looks like

Real row, read on 15 October 2026 (search "phone case" sorted by orders):

```json
{
  "productId": "1005012011127508",
  "url": "https://www.aliexpress.com/item/1005012011127508.html",
  "price": 4.2,
  "originalPrice": 4.33,
  "currency": "USD",
  "newShopperPrice": null,
  "rating": 4.9,
  "soldCount": 6633,
  "isChoice": true,
  "isSponsored": false,
  "deliveryEstimate": "Oct 22 - 27",
  "badges": ["Save $2.16"],
  "listedAt": "2026-04-03"
}
```

## What people use it for

- Dropshipping and product research: best sellers by units sold, with real margins.
- Price monitoring of a category or of your own listings.
- Supplier shortlists: Choice products, fast delivery, high ratings.

## Price

$0.003 per product ($3 per 1,000), no start fee, first 10 products of every run free. Searches with no product and
AliExpress outages are never charged. Paid Apify plans get lower tier prices.

## Questions

**Does it open product pages?** No, it reads search result pages only (no variants or reviews).

**Which currency?** US dollars, as shown to a US visitor.

**Can an AI agent use it?** Yes, through the Apify MCP server (`https://mcp.apify.com`) as `om_kh/aliexpress-search-scraper`.

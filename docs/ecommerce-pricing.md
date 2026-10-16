[← Catalogue home](index.md)

# Ecommerce & Pricing signals

## What problem this solves

Tracking prices, stock status, and marketplace listings — for competitive pricing research, arbitrage, or catalog monitoring — without manually re-checking product pages.

## When to use it

- You want **price/stock changes** on a specific product page over time.
- You want **Amazon search results** for a keyword or a **Best Sellers category**.
- You want to monitor a **specific Etsy shop's** listings.
- You want **Korean marketplace prices** (11st) or **Australian supermarket prices** (Coles) for any search.

## Actors in this family

| Actor | Best for | Pricing |
|---|---|---|
| [Amazon Price & Stock Scraper](https://apify.com/om_kh/amazon-price-stock-tracker) | Price/stock delta for specific product pages (Amazon or any Shopify catalog) | $0.007 / price or stock change + $0.3 / monitored subject re-checked |
| [Amazon Best Sellers Scraper](https://apify.com/om_kh/amazon-best-sellers-scraper) | New entrants to a Best Sellers category | $0.01 / new bestseller + $0.2 / monitored subject re-checked |
| [Amazon Search Results Scraper](https://apify.com/om_kh/amazon-product-search-scraper) | Search-result monitoring for a keyword | $0.01 / new product alert + $0.12 / monitored subject re-checked |
| [Etsy Listings Scraper](https://apify.com/om_kh/etsy-listings-scraper) | A specific Etsy shop's current listings | $0.007 / listing change + $0.35 / source check |
| [11st (11번가) Korea Product Scraper](https://apify.com/om_kh/11st-korea-product-scraper) | Prices, sellers, sales counts and ratings on 11st, a top South Korean marketplace, for any search | $0.004 / product |
| [Coles Australia Scraper](https://apify.com/om_kh/coles-australia-scraper) | Coles supermarket prices, specials and unit prices, per store | $0.001 / product |

## Telling the siblings apart

**Amazon Price & Stock Scraper** watches *specific product pages* you already know about. **Amazon Best Sellers Scraper** and **Amazon Search Results Scraper** are discovery tools instead — a category leaderboard vs. a keyword search — for finding products you don't have a URL for yet. **Etsy Listings Scraper** covers a shop's full catalog rather than one product.

## Recommended starting point

[**Amazon Price & Stock Scraper**](https://apify.com/om_kh/amazon-price-stock-tracker) — the most broadly useful for ongoing price monitoring. Try it: [live example](https://apify.com/om_kh/amazon-price-stock-tracker/examples/vigia-price-stock-delta-quickstart).

## Related family

Want the reviews on a product too? See [Reviews & Reputation](reviews-reputation.md) for Amazon product reviews specifically.

# Make (Integromat) scenarios — Local / Maps wave

No Make account is available to authenticate and build these natively in this session, so each scenario below is a complete, ready-to-recreate module spec rather than an exported native blueprint (Make's blueprint format is proprietary and account-scoped; hand-writing one that hasn't been round-tripped through the actual app risks producing an unimportable file). `MANUAL_PUBLICATION_REQUIRED` for all 5 — recreating any of these in the Make UI from the module list below takes a few minutes.

Each scenario ports its matching n8n workflow (see `../n8n/`) 1:1 in structure — same trigger, same Apify call, same filter, same destination — adapted to Make's module-per-step model.

## 1. New Google Maps business detected -> Slack + Sheets

Ports: `maps-new-business-alert.json`

| # | Module | Config |
|---|---|---|
| 1 | **Schedule** | Daily, 08:00 |
| 2 | **HTTP > Make a request** | `POST https://api.apify.com/v2/actor-tasks/om_kh~vigia-maps-new-business-monitor-quickstart/run-sync-get-dataset-items?token={{APIFY_TOKEN}}`, body: `{"searches":["coffee shops in Austin, TX"],"maxPlacesPerSearch":10,"monitorEnabled":true,"maxTotalChargeUsd":1}` |
| 3 | **Iterator** | over the HTTP response array |
| 4 | **Google Sheets > Add a Row** | map `business_name`, `category`, `address`, `rating`, `website`, `google_maps_url` |
| 5 | **Slack > Create a Message** | `New business detected: {{business_name}} ({{category}}) at {{address}}` |

## 2. Local business discovery snapshot -> Google Sheets

Ports: `local-business-discovery.json`

| # | Module | Config |
|---|---|---|
| 1 | **Manual run** (or Schedule) | — |
| 2 | **HTTP > Make a request** | `POST .../actor-tasks/om_kh~vigia-local-business-monitor-quickstart/run-sync-get-dataset-items`, body: `{"searchQueries":["coffee shop"],"locationQuery":"Austin, TX","maxTotalChargeUsd":1}` |
| 3 | **Iterator** | over response |
| 4 | **Google Sheets > Add a Row** | map `title`, `rating`, `reviews_count`, `address`, `categories` |

## 3. New Google Business Profile question -> Slack alert

Ports: `gbp-qa-alert.json`

| # | Module | Config |
|---|---|---|
| 1 | **Schedule** | Every 6 hours |
| 2 | **HTTP > Make a request** | `POST .../actor-tasks/om_kh~vigia-gbp-qa-monitor-quickstart/run-sync-get-dataset-items`, body: `{"placeUrls":["<your listing>"],"maxTotalChargeUsd":1}` |
| 3 | **Iterator** | over response |
| 4 | **Slack > Create a Message** | `New unanswered question: {{question_text}}` |

## 4. Zillow price/status change -> Slack alert

Ports: `zillow-price-change-alert.json`

| # | Module | Config |
|---|---|---|
| 1 | **Schedule** | Daily |
| 2 | **HTTP > Make a request** | `POST .../actor-tasks/om_kh~vigia-zillow-realestate-monitor-quickstart/run-sync-get-dataset-items` |
| 3 | **Iterator** | over response |
| 4 | **Filter** | `change_type` = `price_down` |
| 5 | **Slack > Create a Message** | `Price change: {{name}} -- {{source_url}}` |

## 5. FLAGSHIP: Discover -> monitor -> qualify local business lead pipeline

Ports: `flagship-local-lead-pipeline.json`

| # | Module | Config |
|---|---|---|
| 1 | **Schedule** | Daily |
| 2 | **HTTP > Make a request** | `POST .../actor-tasks/om_kh~vigia-maps-new-business-monitor-quickstart/run-sync-get-dataset-items`, body as above |
| 3 | **Iterator** | over response |
| 4 | **Filter** | `website` is not empty |
| 5 | **HTTP > Make a request** | `POST .../actor-tasks/om_kh~vigia-lead-quality-api-quickstart/run-sync-get-dataset-items`, body: `{"websiteUrls":["{{website}}"],"maxTotalChargeUsd":1}` |
| 6 | **Google Sheets > Add a Row** | map `business_name`, `category`, `address`, `website` (from module 2's item) + `business_contacts[].email` (from module 5's response) |

5 modules, deliberately not a sprawling scenario — same anti-spam-of-complexity principle as the n8n version.

## Setup for all 5

- Make **Data Store** or **HTTP connection** with `APIFY_TOKEN` stored as a connection parameter, never hardcoded in a module.
- Google Sheets and Slack: use Make's native app connections (OAuth), not raw HTTP.
- Every scenario's first HTTP module should have **Max results / timeout** set generously (Apify Task runs can take up to a few minutes) to avoid a false timeout error.

## Status

`MAKE_TEMPLATES_BUILT` = 5 (spec-complete, described above)
`MAKE_TEMPLATES_TESTED` = 0 (no Make account available this session)
`MAKE_PUBLIC/SUBMITTED` = 0
`MAKE_MANUAL_PUBLICATION_REQUIRED` = 5

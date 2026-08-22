[← Catalogue home](index.md)

# Leads & Verification

## What problem this solves

Once you've discovered a company or business (from Local Business, Jobs, or anywhere else), you usually need a real, verified contact to actually reach out — not a guess.

## When to use it

- You have a **company domain** or **business** and need a **verified public business email**.

## Actor in this family

| Actor | Best for | Pricing |
|---|---|---|
| [Business Email Finder & Verifier](https://apify.com/om_kh/vigia-lead-quality-api) | Public, MX-validated business emails from a website | $0.035/lead |

This family is currently a single, focused Actor rather than a set of siblings — it's the qualification step other families feed into, not a source of its own.

## How it works

Point it at a company's website; it reads public contact-page content and validates any email it finds via MX record, no SMTP probing, no purchased lists. Try it: [live example](https://apify.com/om_kh/vigia-lead-quality-api/examples/vigia-lead-quality-api-quickstart).

## Workflow example

See [Get current jobs from a company without knowing its ATS](examples/jobs-example.md) and [Find newly discovered local businesses and qualify them](examples/local-business-example.md) — both chain into this Actor as the final step.

## Related families

Feed this Actor from [Jobs & Hiring](jobs.md) (a hiring company) or [Local Business](local-business.md) (a newly-detected business).

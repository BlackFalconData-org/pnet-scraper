# Pnet Scraper

Extract structured data from [pnet.co.za](https://pnet.co.za) — structured job listings from pnet.co.za — South Africa's leading job portal. Salary, company, location, full descriptions, contact info, and more.

**[Pnet Scraper - South Africa Job Listings on Apify →](https://apify.com/blackfalcondata/pnet-scraper?fpr=1h3gvi)**

---

## Key features





**Search with filters** — Search by keyword and location. Filter by contract type, remote work, experience level, and more.

**Detail enrichment** — Fetch full job descriptions, salary data, employer profiles, contact information for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Description truncation** — Cap description length per listing to control output size and cost.

**Result cap** — Stop after N listings (up to 3.500). Set to 0 for the full catalog.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Every listing returns the same schema with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases





**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from pnet.co.za on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from pnet.co.za.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**Compensation benchmarking**
Aggregate salary ranges across roles, industries, and locations on pnet.co.za to inform pricing decisions, hiring plans, or candidate negotiations.

**Lead generation**
Extract employer contact details alongside listings to build outreach lists for recruiters, staffing agencies, or B2B sales teams.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

---

## Quick start

```json
{
  "query": "software developer",
  "maxResults": 50,
  "includeDetails": true
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Job search keywords (e.g. 'software developer', 'accountant', 'nurse'). |
| `location` | string | — | City or area slug (e.g. 'johannesburg', 'cape-town', 'durban'). Used in URL path. |
| `contractType` | enum | — | Filter by contract type. |
| `remoteWork` | enum | — | Filter by remote work availability. |
| `experienceLevel` | enum | — | Filter by experience level. |
| `jobAge` | enum | — | Only show jobs posted within this period. |
| `sort` | enum | — | Sort order for results. |
| `maxResults` | integer | `25` | Maximum total results (0 = unlimited). |
| `includeDetails` | boolean | `false` | Fetch full job descriptions and metadata from detail pages. Slower but provides complete data including geo coordinates, employment type, and full HTML descriptions. |
| `descriptionMaxLength` | integer | `0` | Truncate description to N characters. 0 = no truncation. |
| `descriptionFormat` | enum | `"text"` | Output description as plain text or HTML. |
| `compact` | boolean | `false` | Core fields only (for AI-agent/MCP workflows). |
| `incrementalMode` | boolean | `false` | Only output new/changed jobs compared to previous run. |
| `stateKey` | string | — | Stable identifier for tracked universe. Different stateKeys maintain separate tracking. |

---

## FAQ

<!-- WRITE: 4-6 Q&A pairs relevant to this product -->

**Is it legal to scrape pnet.co.za?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

<!-- WRITE: 4-6 honest limitations -->

- <!-- WRITE: limitation 1 -->
- <!-- WRITE: limitation 2 -->


## Output fields

Every listing returns the same 38-field schema. Missing values are `null` — never omitted.

- `jobId`
- `pnetId`
- `harmonisedId`
- `title`
- `company`
- `location`
- `city`
- `latitude`
- `longitude`
- `description`
- `descriptionHtml`
- `employmentType`
- `contractType`
- `workType`
- `industry`
- `workFromHome`
- `isSponsored`
- `isRepost`
- `repostDetectedAt`
- `salaryText`
- `salaryMin`
- `salaryMax`
- `salaryCurrency`
- `salaryType`
- `postedAt`
- `validThrough`
- `applyUrl`
- `canonicalUrl`
- `portalUrl`
- `companyLogo`
- `companyUrl`
- `companyEmployeeRange`
- `companyIndustry`
- `contactEmail`
- `contactPhone`
- `fetchedAt`
- `sourceDomain`
- `changeType`


## Sample output

One object per listing. Here is a real example from a production run:

```json
{
  "jobId": "4c665700f809db666c6ec82e464a945f51ae3ff95a09091cb7bac3b038531b4e",
  "pnetId": 4137723,
  "harmonisedId": "f6b01038-c001-4546-88bc-6b99f9a3f094",
  "title": "Software Developer",
  "company": "Helm Operations",
  "location": "Remote, South Africa",
  "city": "Victoria",
  "latitude": null,
  "longitude": null,
  "description": "Introduction\nAt Helm Operations, we build the software that keeps the world’s maritime operations moving. From tugboats in Vancouver Harbour to offshore service vessels in the Nort…",
  "descriptionHtml": "<h4>Introduction</h4>\n<p>At Helm Operations, we build the software that keeps the world’s maritime operations moving. From tugboats in Vancouver Harbour to offshore service vessels…",
  "employmentType": "FULL_TIME"
}
```

*Truncated — full records contain 38 fields. See Output fields for the complete schema.*


**[Try Pnet Scraper - South Africa Job Listings now — $5 free credit, no credit card →](https://apify.com/blackfalcondata/pnet-scraper?fpr=1h3gvi)**


## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.01 |
| Result | $0.002 |

See the [actor on Apify](https://apify.com/blackfalcondata/pnet-scraper?fpr=1h3gvi) for current pricing.

---

## Related products by Black Falcon Data





- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board
- [Naukri Scraper](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi) — India's largest job portal


## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. [Sign up free](https://console.apify.com/sign-up?fpr=1h3gvi) — $5 credit included
2. Open the actor and paste your input
3. Click Start — results download as JSON, CSV, or Excel

Need more volume? [See pricing](https://apify.com/pricing?fpr=1h3gvi).

---


## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---
---

*Last updated: 2026 03*

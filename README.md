# Pnet Scraper

Extract structured data from [pnet.co.za](https://pnet.co.za) — structured job listings from pnet.co.za — South Africa's leading job portal. Salary, company, location, full descriptions, contact info, and more.

**[Pnet Scraper on Apify →](https://apify.com/blackfalcondata/pnet-scraper)**

---

## Key features



**Search with filters** — Search by keyword and location. Filter by contract type, remote work, experience level, and more.

**Detail enrichment** — Fetch full job descriptions, salary data, employer profiles, contact information for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

---

## Use cases



**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from pnet.co.za on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from pnet.co.za.

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

---

## Related products by Black Falcon Data



- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 03*

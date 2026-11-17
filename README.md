# Bulldogjob Tech Jobs & IT Salaries Scraper

[![Apify Actor](https://img.shields.io/badge/Apify-Actor%20Store-orange?logo=apify)](https://apify.com/moneygain/bulldogjob-scraper)
[![Python Version](https://img.shields.io/badge/Python-3.10%20%7C%203.11%20%7C%203.12-blue?logo=python)](https://github.com/Archibald322/bulldogjob-scraper)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Live Apify Store Actor:** [https://apify.com/moneygain/bulldogjob-scraper](https://apify.com/moneygain/bulldogjob-scraper)

This repository provides an open-source Python runner and documentation for **[Bulldogjob Tech Jobs & IT Salaries Scraper](https://apify.com/moneygain/bulldogjob-scraper)**.

---

## ⚡ Quickstart

### Option 1: Run in Cloud (No Code)
Launch directly from your browser via the Apify Store console:
👉 **[Open Bulldogjob Tech Jobs & IT Salaries Scraper on Apify Store](https://apify.com/moneygain/bulldogjob-scraper)**

### Option 2: Run via Python SDK
```bash
git clone https://github.com/Archibald322/bulldogjob-scraper.git
cd bulldogjob-scraper
pip install -r requirements.txt
export APIFY_TOKEN="your_apify_token_here"
python run.py
```

---

# 🐶 Bulldogjob Tech Recruitment & IT Salaries Scraper

**Scrape Bulldogjob tech jobs data to JSON, CSV, or Excel in seconds without browser overhead.** Extract verified software developer vacancies, B2B contract rates, permanent employment salary brackets, required tech stack tags, seniority levels, remote eligibility, and direct recruiter application links from **Bulldogjob.pl** — Poland and Central Europe's developer-first IT recruitment community.

Designed for IT recruiting agencies, tech headhunters, HR analytics startups, salary benchmarking researchers, and autonomous AI agents. Built with high-speed HTTP requests with Chrome TLS fingerprinting, **zero browser overhead**, and **100% Pay-Per-Event (PPE) pricing** — you only pay for verified job postings delivered.

---

## ⚡ Speed & Value Comparison

| Feature | Our Lightweight Bulldogjob Scraper | Heavy Browser Scrapers (Playwright / Puppeteer) |
|---|---|---|
| **Memory Usage** | **128 MB – 256 MB** | 2 GB – 4 GB |
| **Startup Fee** | **$0.00 (Zero Start Fee)** | $0.05 – $0.10 per run |
| **Speed per Page** | **0.25s – 0.5s per page** | 10s – 20s per page |
| **Pricing Model** | **Pay-Per-Event ($0.005 / job)** | Expensive Monthly Flat Rate |
| **Salary Parsing** | **Structured B2B net & Employment gross brackets** | Unstructured raw text |
| **Anti-Bot Reliability** | **Chrome TLS session emulation** | Frequent bot detection blocks |

---

## 📦 Sample JSON Output

```json
{
  "id": "119842",
  "title": "Senior Cloud DevOps Engineer",
  "company": "CloudWave Systems",
  "companyLogo": "https://bulldogjob.pl/system/companies/logos/119842/cloudwave.png",
  "location": "Warszawa",
  "isRemote": true,
  "experienceLevel": "senior",
  "salaryB2B": "25 000 - 30 000 PLN net / mth",
  "salaryPerm": "19 000 - 24 000 PLN gross / mth",
  "technologies": ["Kubernetes", "Terraform", "AWS", "Python", "CI/CD"],
  "offerUrl": "https://bulldogjob.pl/companies/jobs/119842-senior-cloud-devops-engineer",
  "publishedAt": "2026-11-17T09:00:00.000Z",
  "scrapedAt": "2026-11-17T10:00:00.000000+00:00"
}
```

---

## 🎯 Use Cases & Business Value

- **Central European IT Talent Sourcing**: Source mid, senior, and lead developers across Poland, Central Europe, and the EU remote time zone.
- **Tech Stack Salary Indexing**: Monitor compensation shifts for React, Java, Python, .NET, DevOps, and Data Science skill sets.
- **Competitor Hiring Insights**: Track which software houses and multinational tech hubs are actively hiring in Poland.
- **Autonomous AI Career Agents**: Feed developer job feeds directly into candidate sourcing and matching agents via **Apify MCP Server**.

---

## ⚙️ Input Parameters

| Parameter | Type | Default | Description |
|---|---|---|---|
| `startUrls` | Array | `["https://bulldogjob.pl/companies/jobs"]` | Direct URLs to Bulldogjob listings or search filters. |
| `role` | String | `""` | Optional role or technology filter (e.g. `frontend`, `backend`, `devops`, `python`, `react`). |
| `city` | String | `""` | Optional city filter (e.g. `warszawa`, `krakow`, `wroclaw`, `gdansk`). |
| `experienceLevel` | String | `"all"` | Seniority filter (`junior`, `mid`, `senior`, `lead`). |
| `onlyRemote` | Boolean | `false` | When `true`, filters strictly for 100% remote positions. |
| `maxItems` | Integer | `10` | Maximum number of verified job records to scrape (Prefilled for instant 5-second test runs). |

---

## 🤖 Integrate with AI Agents & No-Code Platforms

### 1. Claude Desktop & Cursor via Apify MCP Server
Connect this actor directly to Cursor, Claude Desktop, Windsurf, or LangChain agents using the official Apify MCP Server:

```json
{
  "mcpServers": {
    "apify": {
      "command": "npx",
      "args": ["-y", "@apify/mcp-server"],
      "env": {
        "APIFY_TOKEN": "YOUR_APIFY_API_TOKEN"
      }
    }
  }
}
```
*Prompt example:*
> *"Find 15 remote DevOps and Cloud jobs in Poland on Bulldogjob paying over 24,000 PLN B2B using bulldogjob-scraper."*

### 2. n8n Automation Workflows
1. Add an **Apify Node** or **HTTP Request Node** in your n8n workflow.
2. Select `Run an Actor` with Actor ID: `moneygain/bulldogjob-scraper`.
3. Pipe daily job postings into Telegram, Discord, or Airtable.

### 3. Make.com (Integromat)
1. Add the **Apify Module** ➔ `Run Actor and get dataset items`.
2. Push developer job alerts into Notion or your candidate pipeline.

### 4. Clay.com Enrichment
1. Use the **Apify Integration** inside Clay.
2. Enrich tech company profiles with active regional engineering job vacancies.

### 5. Python SDK Integration
```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_API_TOKEN")
run_input = {
    "role": "python",
    "onlyRemote": True,
    "maxItems": 20
}
run = client.actor("moneygain/bulldogjob-scraper").call(run_input=run_input)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"[{item['company']}] {item['title']} | {item['salaryB2B']} -> {item['offerUrl']}")
```

---

## ❓ Frequently Asked Questions (SEO FAQ)

### Q1: Is it legal to scrape data from Bulldogjob.pl?
**Yes.** All job postings extracted are public recruitment advertisements placed by companies for public talent discovery. The actor accesses only public listings and does not access private employer panels or applicant CVs.

### Q2: How much does it cost to scrape 1,000 job postings?
Under our **Pay-Per-Event (PPE)** pricing model, you only pay **$0.005 per verified job posting**, so 1,000 jobs cost **$5.00**. There are zero startup costs and subscribers on Apify Bronze/Silver/Gold tiers receive automatic volume discounts up to 20% ($4.00 per 1,000).

### Q3: Can I export Bulldogjob data to Excel, CSV, or Google Sheets?
**Yes.** Apify provides 1-click export options in JSON, CSV, XML, Excel (.xlsx), and HTML table formats. You can also sync datasets automatically to Google Sheets or Airtable via webhooks.

### Q4: Do I need proxies to scrape Bulldogjob?
**No.** Our optimized HTTP engine connects directly with Chrome TLS session impersonation, ensuring reliable extraction without proxy bandwidth costs.

### Q5: Does this scraper separate B2B contract rates from employment contracts?
**Yes.** The actor extracts both `salaryB2B` (net PLN/month for contractors) and `salaryPerm` (gross PLN/month for employment contracts) whenever provided by the hiring company.

---

## 🔗 Explore More High-Speed B2B Scrapers & Enrichers by Our Team

Supercharge your data pipelines, sales outreach, and AI agents with our suite of lightweight, Pay-Per-Event scrapers:

| Scraper | Segment / Target | Key Value | Store Link |
|---|---|---|---|
| **TrustMRR SaaS Startups Scraper** | SaaS Revenue & M&A Data | Stripe-verified MRR, 30d revenue, active subscriptions & founder contacts | [Open on Apify Store](https://apify.com/moneygain/trustmrr-startups-scraper) |
| **Ashby ATS Tech Jobs Scraper** | Next-Gen ATS Career Feeds | Direct ATS API extraction, salaries, departments & remote flags | [Open on Apify Store](https://apify.com/moneygain/ashby-jobs-scraper) |
| **Clutch B2B Agencies Scraper** | B2B Agencies & IT Services | Decoded direct websites, review ratings, hourly rates & service focus | [Open on Apify Store](https://apify.com/moneygain/clutch-agencies-scraper) |
| **Wellfound Startup Talent Scraper** | AI & Tech Startup Jobs | Startup jobs, compensation ranges, equity & tech stack tags | [Open on Apify Store](https://apify.com/moneygain/wellfound-jobs-scraper) |
| **TheProtocol.it IT Careers Scraper** | IT Salaries & Vacancies | Verified salary brackets, tech requirements & seniority levels | [Open on Apify Store](https://apify.com/moneygain/theprotocol-scraper) |
| **Bulldogjob Tech Recruitment Scraper** | Tech Recruitment Feeds | B2B/Employment rates, tech tags & recruiter contacts | [Open on Apify Store](https://apify.com/moneygain/bulldogjob-scraper) |

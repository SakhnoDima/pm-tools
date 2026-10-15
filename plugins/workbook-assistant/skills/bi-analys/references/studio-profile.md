# Studio profile: what we sell

Used by `/bi-analys` (step 5.8 and section 10 "Де ми можемо заробити") and for any proposal work.
It answers: which services we sell, in which industries we are strong, which projects we take and which we
decline. Map every client pain to a service line below; never offer something that is not here.

## Positioning

**We build the data pipelines and the AI systems on top of them.** Most AI projects stall because the data lives
in scattered PDFs, broken APIs, half-scraped websites and legacy databases; we do both halves, so the AI build
does not wait for "someone to figure out the data".

- B2B AI engineering studio, 5 engineers, Ukraine, since 2022.
- Focus: agentic AI and data engineering; strong in healthcare and finance; scraping, RAG, MCP.
- How we work: week 1 scope and edge cases locked; weeks 2–3 something running on the client's data, not
  slides; then iteration with evals, guardrails and observability. Model calls logged with cost, output
  quality tracked per run.

## Service lines

Ordered by how often they win work. "First offer" = the small, fixed, measurable thing to open with.

### 1. Web scraping and data extraction — the entry channel

- **What:** production scrapers for marketplaces and portals with anti-bot rotation, proxies, scheduling,
  change detection, deduplication; clean datasets into PostgreSQL, Google Sheets, an API; captcha-heavy and
  legacy sites without APIs.
- **Experience:** 24/7 monitoring of several marketplaces; e-commerce product matching by GTIN; real-estate data
  lake over property portals with deduplication; large archives (millions of records and files) behind captchas
  and dynamic links; job aggregation across many platforms; place data feeding programmatic pages.
- **First offer:** one scraper for one source with a clean dataset and scheduled refresh.
- **Fits when:** the client needs fresh external data, competitor or price monitoring, lead lists, a dataset
  for AI.

### 2. Data engineering, ETL and legacy migration

- **What:** ETL pipelines (S3, FTP, APIs → PostgreSQL), legacy database migration (MS Access, MDB, Excel,
  FoxPro, PDF → PostgreSQL on AWS RDS), schema design, data validation, REST APIs over the data.
- **Experience:** migration of dozens of legacy databases with hundreds of tables and corrected documentation;
  large market-data ETL with daily refresh; S3 → PostgreSQL → FastAPI pipelines with tests and Docker;
  client data cleaning and enrichment.
- **First offer:** legacy data (Access, Excel, FoxPro, PDF) migrated to a clean database.
- **Fits when:** data lives in old desktop databases, files or FTP drops; analytics or AI is blocked by data
  quality.

### 3. RAG, GraphRAG and document intelligence

- **What:** RAG over the client's documents with a knowledge graph (Neo4j) next to the vector index (pgvector,
  Qdrant, Milvus); answers with file + paragraph citations and the entity chain behind them; connectors
  (SharePoint, data rooms, Outlook), background workers, multi-tenant and on-prem options; RAG audits.
- **Experience:** GraphRAG for a due-diligence platform; RAG over medical literature; tender automation with
  semantic search (weeks of work per tender cut to days); RAG assistant for a manufacturer; OCR of
  educational PDFs into structured data.
- **First offer:** RAG over the client's documents with paragraph-level citations; or a RAG review (chunking,
  retrieval, citations, evals) as a fixed audit.
- **Fits when:** an existing chatbot is inaccurate or slow, knowledge sits in documents, answers must be
  traceable (compliance, due diligence, legal, life sciences).

### 4. AI agents, MCP servers and assistants

- **What:** agents on Claude and OpenAI; MCP servers that expose the client's data and APIs to any MCP client;
  customer-facing assistants (site widget, WordPress plugin, messengers); internal ops assistants;
  NL-to-dashboard tools.
- **Experience:** AI ops assistant for affiliate networks; assistant for an electronics distributor (BOM
  cross-referencing); assistant for an EdTech platform; e-commerce chatbot; natural-language dashboards on
  Amazon Bedrock; lead-generation bot.
- **First offer:** one MCP server or one assistant on one data source, fixed scope, with usage and cost
  analytics.
- **Fits when:** the client wants their product or data usable from AI clients, or wants to automate a
  repetitive team workflow.

### 5. Healthcare data (strong niche)

- **What:** aggregation of public US healthcare data with entity resolution; NPI matching and HCP data
  validation; physician / KOL target lists; lab-report parsing and biomarker scoring.
- **Experience:** a medical data graph over public sources (providers, procedures, payments, clinical trials,
  publications) with a high-accuracy matching engine and a fast API. Public data only, no PHI.
- **First offers:** NPI matching; lab reports parsed into normalized biomarker data; biomarker scoring engine
  with AI recommendations.
- **Fits when:** MedTech, pharma sales / research teams, clinics, health platforms. HIPAA projects need the
  BAA question settled in discovery.

### 6. Quant tooling: backtesting, strategy migration, optimization (strong niche)

- **What:** porting legacy trading systems (VB.NET, EasyLanguage / MultiCharts, AFL, MQL, ThinkScript, Excel)
  to Python with signal-by-signal validation; corporate-action-adjusted market-data pipelines; backtesting
  with standard risk metrics; parameter optimization with out-of-sample checks.
- **Experience:** described only generically (see Confidentiality): migrated a legacy trading-signal system to
  Python with validation; built market-data pipelines and optimization tooling around it.
- **First offers:** Python backtest with an overfitting check; legacy → Python strategy port.
- **Fits when:** fintech, trading education, funds and family offices, signal providers.

### 7. Automation and AI content (secondary)

- **What:** n8n / Make workflows between CRM, mail, Sheets, messengers; AI-generated SEO content with review in
  Google Sheets and autoposting (WordPress, LinkedIn); news aggregators with AI categorization.
- **Experience:** large-scale AI content and programmatic pages; news aggregation with AI categorization;
  content pipelines that measurably improved search positions.
- **Sell as:** an add-on or a growth idea for an existing client, not as a headline service.

### 8. Web development (add-on only)

WordPress / WooCommerce / Webflow customization, plugins, multisite, booking and event platforms, React
widgets, calculators. Take it only as part of a data / AI project or for an existing client. We do not sell
online-store builds as a service.

## Industries

| Industry | Strength | What we have done there |
| --- | --- | --- |
| Finance, trading, investment data | Strong | Legacy data migration, market-data ETL, financial scraping, strategy migration and optimization |
| Healthcare, MedTech | Strong | Medical data graph, GraphRAG for due diligence, medical-literature RAG, biomarker and lab-report products |
| E-commerce, retail intelligence | Solid | Marketplace monitoring, discount analytics with agents, chatbots, affiliate platforms |
| Real estate | Solid | Data lake over property portals with lead strategies |
| Affiliate and performance marketing | Solid | AI ops assistant, affiliate scraping + AI content |
| Crypto, web3 | Past | Older WordPress-era work: content, a trading bot |
| Media, content, SEO | Past | Aggregators, AI content pipelines |
| EdTech | Some | Assistant for a learning platform, OCR of educational PDFs |
| Distribution, manufacturing, agriculture | Some | BOM assistant, document RAG, tender automation |

## Upsell pattern

Proven with past clients: free setup items (analytics, a short audit) → paid support (monitoring of scrapers and
APIs, prompt and model updates, hosting) → growth ideas (AI assistant, alerts, dashboards, extra data sources).

## Projects we take and decline

**Take:**

- Data + AI projects where we own the data side (scraping, ETL, migration) and the AI side (RAG, agents, MCP).
- Fixing or improving an existing AI system (accuracy, retrieval, speed, reliability, evals).
- Long-running data feeds with paid monitoring — most long-term clients started with a scraping job.
- Fintech and healthcare work where the data is messy and the domain is regulated.

**Decline or treat with care:**

- Pure online-store or theme builds, design-only work, mobile apps.
- Forex / MetaTrader bots, Snowflake / Databricks projects — no real case behind them.
- Anything that needs PHI without a signed BAA, or AI output that would be investment advice without the
  client's licence.
- Red flags seen before: no payment method, unrealistic scope for a tiny fixed budget, poor client reviews,
  scams.

## Confidentiality when citing experience

- Never name past clients, their contacts, markets, private links or internal results in anything a client or
  prospect sees. Cite the type of work and the outcome only.
- Cases under NDA (the quant tooling work) are described only as generically as in service line 6: no market,
  exchange, algorithms, rules, parameters, methods or results.
- Prices and rates are not part of this profile; take them from the PM.

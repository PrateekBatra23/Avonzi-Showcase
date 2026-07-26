# Avonzi

**AI intelligence, delivered daily.**

Avonzi is a platform built for engineers, researchers, and practitioners who need to stay current on what's actually shipping in AI — model releases, research, tooling, and implementation-level updates — and who are looking for open roles across AI and broader tech companies. Every day, Avonzi compiles an Archive made up of individual Briefs, alongside a continuously updated board of real job openings, not limited to AI-focused companies alone.

🔗 [avonzi.prateekbatra.dev](https://avonzi.prateekbatra.dev)


> Source code for this project is maintained in private repositories. This repository exists to document and showcase the product.

---

## What Avonzi does

**Daily Archives** — Every day, Avonzi's pipeline gathers, deduplicates, and compiles the day's most significant AI developments into an Archive entry, made up of individual Briefs. The full history is searchable by date range, so nothing that shipped is ever lost to the feed.

**Jobs Board** — A live, continuously updated board of open roles at leading AI companies, refreshed every 6 hours. Listings are filterable by company, role, seniority, and remote status, with freshness clearly signaled so the newest opportunities are never buried.

**Company & Topic Pages** — Every Brief is organized by the company and topic it concerns, so anyone tracking a specific company's trajectory — or a specific theme, like agent tooling or inference hardware — can follow it directly.

**Community Moderation** — Visitors can flag inaccurate or stale job listings directly from the board, feeding a review workflow that keeps the data trustworthy without requiring manual auditing of every post.

**Internal Admin Portal** — A real operations console, not a CRUD afterthought: pipeline health monitoring, per-run execution history, a live data-quality feed, content moderation with cascading rules, and role-based access control (owner/admin/read-only) for a small internal team. The kind of internal tooling most teams retrofit later — built proactively here from the start.

---

## By the numbers

- **167+ companies tracked**, across 11 distinct data-source integrations
- **4 enterprise ATS platforms integrated via reverse-engineered API access** — not HTML scraping — meaning each integration is built against a source platform's real data contract, not its rendered page markup
- **2,000+ live tech and AI job listings** maintained at any given time
- **Two fully independent ingestion pipelines** (news and jobs), each with its own isolated, narrowly-scoped credentials
- **Full historical audit trail** — every job listing ever seen is logged as a distinct event, not overwritten, preserving a genuine record of the market over time rather than just a live snapshot

---

## Engineering highlights

- **API integrations, not brittle scrapers.** Every major data source was integrated by reverse-engineering the platform's actual underlying API rather than parsing rendered HTML — a meaningfully more resilient approach, since API-based integrations only break when a platform changes its real data contract, not on every UI redesign.
- **Crash-resilient, incremental ingestion.** Results are posted company-by-company as they're fetched, not batched at the end of a run — so a mid-run failure only loses what was in flight at that exact moment, never the whole run's progress.
- **Deterministic, rubric-based editorial curation.** Story selection for each day's Archive uses an explicit, auditable multi-axis scoring system — company significance, content type, recency, source credibility — rather than unstructured AI judgment, so editorial decisions are consistent and explainable rather than a black box.
- **Graceful degradation, everywhere.** Missing or ambiguous data never blocks content from publishing — it falls through a defined chain of fallbacks and is flagged for review instead, a design philosophy applied consistently across the whole system rather than a one-off feature.
- **Full run-lifecycle observability.** Every pipeline execution is tracked start-to-finish — timing, results, failures, and why — as structured data the admin portal can query and display, not logs that vanish after the fact.
- **A permanent, auditable image-licensing trail.** Every image on the site traces back to a recorded, verifiable public-domain or licensed source, enforced at the data layer — the system will not let an image go live without one.

<details>
<summary><strong>For the technically curious</strong></summary>

- **Machine identity, not shared secrets.** The news and jobs pipelines authenticate with distinct, narrowly-scoped credentials rather than a single shared key — a compromised or misbehaving credential on one side can never touch the other's data.
- **Two data philosophies, one deliberate design.** The jobs pipeline is append-only, preserving a full historical log of every listing ever seen; the news pipeline treats each day's Archive as a discrete, current-state publication with explicit duplicate suppression. Job postings and news content are genuinely different kinds of data with different lifecycle needs — the system is designed to treat them accordingly rather than forcing one pattern onto both.
- **Self-healing ingestion recovery.** When incoming content momentarily references something that doesn't resolve correctly, the system attempts contextual recovery using other data from the same batch before falling back to a quarantine state — reducing the operational burden of babysitting a daily automated pipeline.
- **Deliberate, reversible moderation.** Deactivating content cascades sensibly through related data, but reactivation is always a conscious, granular decision — the system never assumes "undo" means "restore everything exactly as it was."
- **Full content provenance.** Every Archive entry and every job posting traces back to the exact pipeline execution that produced it, which matters enormously for debugging and trust in a system that runs unattended for months at a time.

</details>

---

## Product principles

- **Signal over noise.** Coverage is curated and compiled, not a raw feed — this is a platform, not a news outlet.
- **Nothing disappears.** The full Archive is permanent and searchable; a missed day is always one click away.
- **Fast by default.** The site is server-rendered end-to-end, with full SEO coverage (structured data, sitemap, per-page metadata) so content is discoverable, not just visitable.

---

## Under the hood

Avonzi is built as three coordinated services — an automated ingestion pipeline, a FastAPI backend, and a server-rendered Next.js frontend — plus a fully separate internal admin application for content operations and moderation. The system is designed to scale from a handful of tracked companies to hundreds without requiring code changes: adding, retiring, or re-theming a company is a single data change that propagates automatically across the entire site.

---

## Author

Built and maintained by [Prateek Batra](https://prateekbatra.dev).

---

© 2026 Prateek Batra. All rights reserved. This repository is for informational purposes only.

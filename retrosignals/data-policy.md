# RetroSignals: Data Policy

RetroSignals is CRB's **frozen, task-linked consumer-signal environment**. It exists so model comparisons are reproducible despite a continuously changing web (deleted posts, accumulating comments, shifting search rankings, new summaries). This document covers what it contains, how it is conditioned, the privacy and responsible-use rules it operates under, and how contamination is handled.

## What a snapshot may contain

A snapshot is collected and timestamped **before** benchmark execution and may include: social posts; comments and replies; reviews; marketplace content; community discussions; search-result pages; blog and article content; video metadata; video/audio transcripts; creator content; and brand/competitor context documents.

Each signal is stored with metadata: source type, timestamp, geography (where available), language, engagement indicators, parent–child conversation structure, and enrichment labels.

## Two arms

The same frozen snapshot is served in two arms, which is what enables the data × model ablation:

1. **Consumer-signal corpus arm** — enriched and contextually filtered consumer corpus.
2. **Public-web arm** — public snapshot only.

A **tool-less control** (model answers from memory, no corpus) measures how much data helps at all.

## Signal conditioning

CRB evaluates whether an agent retrieves *conditioned, research-ready* signal, not just data. Conditioning includes: relevance filtering; spam/bot filtering; promotional-content detection; brand-owned vs consumer-owned separation; duplicate/near-duplicate control; contextual filtering; conversation threading; and privacy-safe sentiment, need-state, occasion, stage, and cohort classification. Conditioning quality is reported as a **diagnostic** (data breadth, depth, condition; relevant signal density), not folded into any composite in v0.1.

## Privacy and responsible use

Consumer research agents operate on human expression. These rules are core, not an appendix:

1. Personally identifiable information must not be exposed in benchmark outputs.
2. Usernames, handles, and private details are removed or anonymized.
3. Cohort-level claims use aggregation thresholds.
4. Sensitive-attribute inference is prohibited unless explicitly supported, privacy-safe, and ethically approved.
5. Quotes are anonymized or paraphrased where required.
6. Platform terms, data licenses, and source restrictions are respected; data sources and licensing are documented per snapshot.
7. Psychographic and cohort labels are used cautiously and never treated as unsupported individual-level claims.
8. Systems are penalized for stereotyping, manipulative recommendations, or overconfident psychological profiling.

The benchmark rewards systems that are evidence-grounded, privacy-safe, transparent, and honest about uncertainty.

## Contamination, holdout, and refresh

- **Splits.** Public sample (released), development (approved participants), private test (never released or trained on; used for official scoring). Prompts, evidence checklists, reference reports, and snapshots for the private set are not released.
- **Holdout.** Where possible, include a date-stamped holdout of consumer conversations collected **after** relevant model training cutoffs.
- **Refresh.** Tasks and snapshots are refreshed quarterly to reduce contamination and saturation.
- **Live-vs-frozen check.** For a subset of tasks, compare live-corpus and RetroSignals performance and report rank correlation. If relative rankings are stable, RetroSignals is the canonical setting for official scoring.

## Provenance

Each snapshot ships with a manifest: collection date, source list, licensing/terms basis, enrichment steps applied, and any provider contributions (which must be disclosed — see [GOVERNANCE.md](GOVERNANCE.md)).

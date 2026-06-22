# Consumer Research Bench (CRB)

> A benchmark for evaluating AI agents on consumer research. The question it asks: **can a system *conduct consumer research*, not merely search the web?**

[![status: preprint](https://img.shields.io/badge/status-preprint%20v0.6-blue)](paper/CRB-v0.6.md)
[![license: CC BY 4.0](https://img.shields.io/badge/paper-CC%20BY%204.0-green)](#license)
[![governance: independent](https://img.shields.io/badge/governance-independent-purple)](GOVERNANCE.md)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-orange)](#contribute)

**Status:** Working Draft v0.6 · preprint · all results tables are `[TO RUN]`
**v0.1 scope:** Consumer domain only. Brand, Category, and Culture are retained as roadmap domains.
**Administration:** independent — evaluated vendors do not control task selection, scoring, reference reports, or publication. See [GOVERNANCE.md](GOVERNANCE.md).

---

## What CRB measures

> **Decision-ready consumer-research quality per unit time, at a fixed evidence-grounding bar.**

Consumer understanding now has to be produced both deep and fast. Primary research is deep but slow; social listening is fast but shallow; general AI tools search and summarize but lack consumer-specific data, methodology, and reasoning standards. No existing benchmark tests consumer-research-specific capability directly. CRB does.

## How it works

- **Objective Track** — atomic tasks (Find Signal, Derive Metric, Validate Claim, Attribute Driver, Define Cohort, Populate Set, Compile Dataset) scored against expert-worked ground truth. See [`benchmark/task-schema.json`](benchmark/task-schema.json).
- **Report Track** — open-ended research memos scored by **C-RACE**, a reference-based, criteria-adaptive judge. Scores are **provisional** until judge–human agreement is demonstrated. See [`benchmark/rubrics/c-race.md`](benchmark/rubrics/c-race.md).
- **RetroSignals** — a frozen consumer-signal environment for reproducibility, with two arms (public-web vs consumer-signal corpus) that enable a **data × model ablation**. See [`retrosignals/data-policy.md`](retrosignals/data-policy.md).
- **Validity gates** — hard failures (fabricated quotes, unsupported statistics, no inspectable evidence) **invalidate or cap** a run rather than just nicking the score. See [`benchmark/rubrics/validity-gates.md`](benchmark/rubrics/validity-gates.md).
- **Diagnostics** — data breadth/depth/condition, relevant signal density, contextual fidelity, quant–qual integration, speed, calibration, trace failure rates. Reported, **not** folded into any composite.

CRB v0.1 deliberately reports **no single overall score** until both tracks are individually validated.

## Repository layout

```
.
├── README.md                       # you are here
├── paper/
│   └── CRB-v0.6.md                 # the preprint (finalized v0.6)
├── benchmark/
│   ├── task-schema.json            # JSON Schema for a CRB task instance
│   └── rubrics/
│       ├── c-race.md               # Report Track rubric + scoring bands
│       └── validity-gates.md       # run-level failure & score-cap conditions
├── retrosignals/
│   └── data-policy.md              # frozen environment + privacy/responsible-use policy
├── GOVERNANCE.md                   # independent administration, conflict-of-interest rules
└── CITATION.cff                    # machine-readable citation
```

## Status & what's deliberately missing

This is honest: **no task instances and no results are published yet.** Every results table in the paper is `[TO RUN]`.

Conspicuously absent, and intentionally so until authored properly:
- `benchmark/tasks/` — the actual task instances (briefs + frozen snapshots + reference reports + evidence checklists).
- A runner / scoring harness.
- Any leaderboard.

The immediate priorities are (1) authoring the first reference reports and task instances, and (2) running the first head-to-head to fill the first results row.

## Contribute

CRB is a living preprint and an open call. We are recruiting **independent task authors and reviewers** — senior consumer-insights researchers, brand/category experts, and cultural analysts who are not employed by evaluated vendors. Independence is what makes the benchmark credible; see [GOVERNANCE.md](GOVERNANCE.md). Open an issue or contact the Working Group to get involved.

## Citation

See [`CITATION.cff`](CITATION.cff) — GitHub renders a "Cite this repository" button from it.

## License

Paper text and benchmark specification: **CC BY 4.0**. Any code added later: MIT (add a `LICENSE` file before first public release).

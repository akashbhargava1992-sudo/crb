# Submitting to the Consumer Research Bench (CRB)

**Participation is open to anyone.** CRB is a public, community benchmark: fork the repo, run the
benchmark, and open a pull request with your results and the artifacts that let us reproduce them. A
maintainer reviews it, independently re-runs/re-scores it, and merges it onto the leaderboard.

This model follows how established benchmarks handle open submissions — self-run + PR + verify — as in
[SWE-bench](https://github.com/swe-bench/experiments), [AlpacaEval](https://github.com/tatsu-lab/alpaca_eval),
and [MLPerf](https://github.com/mlcommons/policies) — with the integrity safeguards below adapted to
CRB's two tracks.

> **Status (v0.1).** The spec, rubrics, and task schema are public; the **public sample tasks and the
> submission harness are being released.** You can participate **now** by reviewing the rubrics,
> proposing tasks, and preparing a submission against the format below. Result PRs open when the sample
> tasks land — [watch the repo](https://github.com/akashbhargava1992-sudo/crb) for the call.

## Who can submit

Anyone — any consumer-research system: an AI agent, a workflow/tool, a deep-research model, or a human
baseline. First-party entries (including the maintainers' own) are welcome but are **flagged as
first-party and independently re-scored** (see Governance).

## The two tracks

- **Objective track** — auto-scorable tasks run against the frozen [RetroSignals](retrosignals/data-policy.md)
  corpus. Reproducible: anyone re-running the same pinned corpus + code gets the same score.
- **Report track** — open consumer-research briefs scored on the [C-RACE rubric](benchmark/rubrics/c-race.md)
  by an LLM-as-judge plus a human panel, under the [validity gates](benchmark/rubrics/validity-gates.md).

## How to submit (the flow)

1. **Fork** the repo and run your system on the **public sample tasks** using the released harness.
2. **Add your entry** under `submissions/<track>/<YYYY-MM-DD>-<system-slug>/` containing:
   - `metadata.yaml` — the disclosure + result block (template below).
   - **Objective:** your `predictions` (or a runnable recipe/container), plus execution **logs** and the
     **pinned corpus version**.
   - **Report:** the produced report(s) **as rendered** (PDF/HTML with images intact — not text-only),
     plus run **traces/logs** where available.
3. **Open a pull request.** A maintainer reviews it against the rubric + validity gates and
   **independently re-runs a random subset** (objective) or **re-scores with the published judge +
   blinded panel** (report).
4. **Merge.** Passing entries land on the leaderboard tagged **Verified**; entries we can't yet re-run
   are listed as **Community (self-reported)**.

## Result tiers

- **Verified** — maintainer re-ran (objective) or re-scored (report). Only Verified entries get the
  headline ranking.
- **Community / self-reported** — accepted with artifacts but not yet independently re-run; labelled as
  such so readers can weight them accordingly.

## Anti-gaming rules

- **No peeking at held-out labels.** A private held-out slice is scored by a neutral custodian; its gold
  is never released. Submissions to the held-out set are **frequency-limited** to prevent probing.
- **No leakage.** Do not train, tune, or retrieve against gold answers, and do not look up task solutions
  on the web. Objective submissions must not use any hidden gold/hint fields.
- **Report the run honestly.** Single attempt by default; if you select among multiple runs, disclose the
  selection logic and include traces for all of them.
- **Pin everything.** Corpus version, judge model + version, and your system/code commit must be pinned
  so the run is reproducible.

## Governance & conflict-of-interest

CRB's author is also a vendor that can be evaluated, so neutrality is enforced structurally
([GOVERNANCE.md](GOVERNANCE.md)):

- **Mandatory disclosure** on every entry: the models/vendors used, open vs. closed weights and code,
  data sources, and any conflict of interest.
- **First-party entries are flagged** and **re-scored/signed off by an external reviewer** on the panel.
- **Neutral custodian** holds the private held-out gold; the conflicted party never touches the labels.
- **Report track is blinded** (vendor identity stripped) for the human panel, with a meta-review
  committee making the final accept/reject call.
- The **judge rubric, judge model/version, and the LLM-judge↔human agreement** are published; the judge
  applies positional randomization and length control.

## `metadata.yaml` template

```yaml
system:
  name: "Your System Name"
  version: "v1.2"
  type: "ai-agent"        # ai-agent | workflow | deep-research | human-baseline
  url: "https://..."      # optional
track: "report"           # report | objective
models_used:              # every model in the pipeline
  - name: "provider/model-id"
    role: "generation"    # generation | judge (judge is set by CRB, not the submitter)
open_weights: false
open_system: false
vendor: "Your Org"
data_sources: ["..."]     # where the system's evidence came from
conflict_of_interest: "none"   # or describe (e.g. first-party author entry)
cost_usd: null            # optional, if disclosed
artifacts:
  predictions: "predictions/"     # objective
  report: "report.pdf"            # report track (rendered, images intact)
  logs: "logs/"
  corpus_version: "retrosignals@<pin>"
report: "https://..."     # link to a technical report / write-up (required for report track)
```

## Contribute without a submission

- **Propose or review tasks** (a PR against the task schema, with a short rationale) — reviewed publicly,
  decided by a meta-review committee.
- **Review the rubrics** ([C-RACE](benchmark/rubrics/c-race.md), [validity gates](benchmark/rubrics/validity-gates.md))
  and open issues.

Questions → open an [issue](https://github.com/akashbhargava1992-sudo/crb/issues).

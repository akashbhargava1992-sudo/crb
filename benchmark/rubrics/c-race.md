# C-RACE — Consumer Research Adaptive Criteria Evaluation

The Report Track rubric. C-RACE is a **reference-based, criteria-adaptive** framework: a judge model generates task-specific dimension weights and criteria, then scores the target report **relative to an expert reference report**. Isolated scoring is avoided because fluent reports tend to receive uniformly high absolute scores.

> **Provisional-until-validated.** Automated C-RACE scores are reported as *provisional* until the judge's agreement with human experts is demonstrated (see [Human-Consistency Validation](#human-consistency-validation)). Until then, lead with human scores.

## Dimensions

C-RACE scores a small **core** set and tracks the rest as **diagnostics** until each added dimension is itself validated against humans. Every dimension you score raises the human-agreement bar you must clear, so v0.1 keeps the scored set lean.

### Scored (core)

| Dimension | What it measures |
|---|---|
| Comprehensiveness | Coverage of relevant groups, occasions, motivations, counter-signals, category context |
| Consumer Insight Depth | Interpretation of motivations, tensions, rituals, identity signals, barriers, behavioral shifts |
| Methodology Fidelity | Whether the report follows the appropriate research method |
| Evidence & Traceability | Whether claims are grounded in inspectable consumer signal |

### Diagnostic (reported, not yet folded into the score)

| Dimension | What it measures |
|---|---|
| Quant–Qual Integration | Whether quantitative patterns are connected to qualitative evidence and confidence |
| Contextual Fidelity | Whether findings are read against market, category, cultural, and business context |
| Decision Readiness | Whether the output gives clear implications and recommended actions |
| Readability & Structure | Whether the report is clear, scannable, and usable by stakeholders |

Promote a diagnostic to scored only after it clears the same human-agreement bar as the core set.

## Dynamic weighting

The judge (or an expert panel) assigns per-task weights across the scored dimensions **before** seeing outputs. Examples:

- **U&A task** → weight Comprehensiveness, segmentation, and Insight Depth.
- **Trendspotting** → weight weak-signal discovery and Insight Depth.
- **Whitespace** → weight strategic synthesis and Decision Readiness (diagnostic-informed).

Record the weights with the task instance (`scoring.crace_weights`).

## Reference-based scoring

For each scored dimension, the judge compares the target report against the expert reference on the task-specific criteria, producing intermediate scores. The final relative score is:

```
S_final(target) = S_int(target) / ( S_int(target) + S_int(reference) )
```

Report **rankings and proportional gaps**, not absolute values. The reference is the expert-authored gold answer; authoring it is the key dependency for the Report Track.

## Scoring bands (per scored dimension, 0–10)

**Consumer Insight Depth**

| Score | Description |
|---|---|
| 0–2 | Surface summary; no real consumer motivation |
| 2–4 | Some motivations, generic and weakly supported |
| 4–6 | Adequate motivations and some segmentation |
| 6–8 | Strong explanation of motivations, tensions, rituals, occasions |
| 8–10 | Deep, specific, non-obvious, evidence-backed understanding |

**Evidence & Traceability**

| Score | Description |
|---|---|
| 0–2 | Most claims unsupported or fabricated |
| 2–4 | Some evidence, weak or loosely related |
| 4–6 | Most claims supported, limited triangulation |
| 6–8 | Strong support and clear traceability |
| 8–10 | Fully auditable, triangulated, high-integrity grounding |

(Define equivalent 0–10 bands for Comprehensiveness and Methodology Fidelity before first run.)

## Human-consistency validation

Using the human evaluation panel, report: Pairwise Agreement Rate, Overall Pearson, Filtered Average Pearson, Filtered Average Spearman, and Intraclass Correlation. **Target: C-RACE–human agreement ≥ human inter-annotator agreement.** Until met, scores are provisional.

## Validity gates apply first

Before any C-RACE scoring, apply [validity gates](validity-gates.md). A run that triggers an invalidation condition is not scored; a run that triggers a score-cap condition cannot exceed the cap regardless of C-RACE output.

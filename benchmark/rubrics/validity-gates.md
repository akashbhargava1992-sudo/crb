# Validity Gates

Some failures should not merely reduce a score. They violate the minimum evidentiary standards of consumer research, so they either **invalidate the run** or **cap the maximum score**. Validity gates are applied **before** any Objective Track or C-RACE scoring, and they make the benchmark harder to game: a fluent but unsupported output cannot post a high number.

## Run-level failure conditions (invalidate)

A run is marked **invalid** (not scored) if the system does any of the following:

1. Fabricates consumer quotes.
2. Fabricates statistics, source counts, or quantitative claims.
3. Cites evidence that does not exist.
4. Produces key claims with no inspectable raw evidence.
5. Cannot provide source-level traceability for its central conclusions.

An invalid run is recorded as a failure in the results, not omitted — repeated invalidation is itself a reportable signal about a system.

## Score-capping conditions (cap)

A run receives a **capped score** (it cannot exceed the cap regardless of how strong the rest of the output is) if the system:

1. Confuses brand-owned content with organic consumer signal.
2. Treats news, investor commentary, or PR material as consumer behavior.
3. Overgeneralizes from one platform or one viral post.
4. Ignores obvious contradictory evidence.
5. Produces generic insights that could apply to many brands or categories.
6. Provides recommendations without evidence.
7. Fails to explain or follow the intended methodology.

The cap value is set per task (default: 0.5 of the available scale) and recorded with the task instance.

## How gates are applied

1. **Grounding check first.** Decompose the output into claims and run statement–signal verification (see the paper, §10). The fabrication and traceability gates draw directly on this.
2. **Apply invalidation gates.** If any invalidation condition is met, stop — the run is invalid.
3. **Apply cap gates.** Record any cap condition met and set the ceiling.
4. **Score.** Run Objective Track scoring and/or C-RACE; clamp to the cap if one was set.
5. **Log.** Record which gates fired in the per-run trace (feeds the [failure taxonomy](../../paper/CRB-v0.6.md) and the validity-gates results table).

## Reporting

Validity-gate outcomes are reported per system: invalid runs, score-capped runs, and counts of each triggering condition (fabricated quotes, unsupported statistics, no evidence for key claims). These columns are part of the official results, not a footnote.

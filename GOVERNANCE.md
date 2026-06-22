# Governance

CRB is intended to be administered by an **independent research group**, not by any vendor whose system it evaluates. This separation is the benchmark's central credibility claim. A benchmark a vendor designs, authors, scores, and publishes for its own product cannot, on its own, prove that product beats competitors — independence is what lets the results travel.

> **Independence is a commitment, not a label.** Calling the maintainer "independent" does nothing unless real, non-vendor people hold the controlling roles below. If a single evaluated vendor in practice controls the test set, scoring, references, or publication, this document is being violated regardless of what the README badge says — and an undisclosed vendor relationship dressed as independence is *worse* than honest vendor administration. Where full independence is not yet in place, state that plainly and scope claims to "independently governed where feasible."

## The CRB Working Group (maintainer)

The Working Group controls, and only the Working Group controls:

1. The benchmark construct and scope.
2. Recruitment of expert task authors (with a majority not employed by evaluated vendors).
3. The public / development / private splits, and the sealed private test set.
4. Official evaluation runs.
5. Validation of automated judges (e.g., C-RACE) against human experts.
6. Publication of results, limitations, and the leaderboard.
7. Benchmark refreshes.

At least one Working Group reviewer with no commercial relationship to any evaluated system must sign off on the task set and the published results.

## Participant systems

Participants may include consumer-research AI models, general-purpose LLMs with web search, deep-research agents, social-listening / market-intelligence workflows, and human-researcher baselines.

Vendors may **submit systems for evaluation**. Vendors may **not** control:

- task selection or authoring,
- scoring criteria or rubrics,
- reference reports,
- the private test set,
- leaderboard publication.

## Data providers

Some snapshots may include data contributed by commercial or academic providers. Any such contribution **must be disclosed** in the snapshot manifest and in published results. A data provider must not influence task selection, scoring criteria, or official reporting **for any task on which its own system is evaluated**, and must recuse from those decisions.

## Conflict-of-interest mitigations

1. Independent benchmark governance (this document).
2. Independent task authors not employed by evaluated vendors.
3. Blind grading — evaluators do not know which system produced which output.
4. Pre-registered criteria locked before results are seen.
5. Sealed holdout tasks not exposed to participants.
6. Full method and prompt disclosure for public tasks.
7. A public sample subset.
8. Clear separation between development use and official benchmark claims.
9. Data × model ablation, so any advantage is attributable to data, model, or system design rather than asserted.

## Disclosure

Every published result names: who authored the tasks, who graded, which entities funded or contributed data or infrastructure, and any commercial relationship between a Working Group member and an evaluated system. Recusals are recorded.

## Release stages

1. Internal pilot by the independent Working Group.
2. Public sample release.
3. Private held-out evaluation.
4. Verified leaderboard.
5. Rolling benchmark refresh.

## Amending this document

Changes to governance are themselves disclosed, with rationale and date, in the version history. Loosening any vendor-control restriction above requires sign-off from a non-vendor Working Group member.

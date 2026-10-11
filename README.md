# Synareon Open Lab

Public research record of the Synareon project's coding-agent experiments:
what was tried, what was actually measured, and what remains unknown.

## Why trustworthy coding-agent completion matters

Coding agents routinely produce output that *looks* finished while being
wrong, incomplete, or unverified. Synareon studies whether explicit,
deterministic checks (proposal contracts, verification gates, sealed
evidence) improve the rate at which agents reach genuinely complete,
evaluator-passing solutions — and publishes the failures as carefully as
any success.

## EXP-003 overview

EXP-003 (run `EXP-003-F`, revision R3) was a 4-arm factorial benchmark of
deterministic assurance versus raw agent execution: A raw agent, B skills
only, C harness governance only, D skills plus harness. 132 logical units
planned; 131 sealed; 1 censored with no imputation. Status:
`TERMINATED_INCOMPLETE` / `CLOSED_WITH_CENSORED_UNIT`.

## Key actual results (observed, not claimed as proof)

- Qualified Completion (evaluator-passed + sealed, the only hard gate):
  **5/131 (3.8%)** — A 1/33, B 4/33, C 0/32, D 0/33.
- The evaluator ran on all 65 governed seals and passed none. No
  successful governed mutation was observed.
- Primary paired comparison (D vs B, n=33): B 4, D 0 — descriptive gap
  over 4 events, not a significance result.
- **Interpretation:** EXP-003 is a negative result. It does not demonstrate
  harness superiority, and no such claim is made. Details:
  [`experiments/EXP-003/RESULTS.md`](experiments/EXP-003/RESULTS.md).

## Limitations and negative outcomes (read before citing)

Governed-arm failures mix proposal-contract rejection, agent stalls, and
unmeasured harness failure modes; usage data covers 33/131 units
(governed-arm cost UNKNOWN); lane equals model by design, so no model
ranking is possible; one unit is censored and irrecoverable. Full list:
[`experiments/EXP-003/LIMITATIONS.md`](experiments/EXP-003/LIMITATIONS.md).

## EXP-004 planned improvements (plan, not results)

EXP-004 is a planned follow-up: proposal-packaging discipline, durable
attempt admission and liveness, bounded no-progress controls, and
measurement projection — each as a falsifiable micro-experiment proposal.
Status: **PLANNED. No EXP-004 results are claimed.**
See [`experiments/EXP-004/EXPERIMENT_PLAN.md`](experiments/EXP-004/EXPERIMENT_PLAN.md).

## Evidence and reproducibility

Aggregate results plus content hashes are published here. Raw per-unit
streams, session transcripts, and internal endpoints are not published.
What is public, what is private, and what would be needed to reproduce
this work: [`docs/EVIDENCE_AND_DISCLOSURE.md`](docs/EVIDENCE_AND_DISCLOSURE.md).

## Experiment status and links

| Experiment | Status | Detail |
|---|---|---|
| EXP-003-F R3 | `TERMINATED_INCOMPLETE`, `CLOSED_WITH_CENSORED_UNIT` | `experiments/EXP-003/` |
| EXP-004 formal | PLANNED (not authorized, no results) | `experiments/EXP-004/` |
| R6 implementation / smoke | separately closed / `CLOSED_WITH_NEGATIVE_QUALIFICATION`; live set route never observed | limitations §7 |

## License

Apache License 2.0 (`LICENSE`). Public artifacts are original authorship
summaries of internal experiment evidence. No third-party benchmark
fixtures, skill packs, or datasets are redistributed.

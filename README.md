# Synareon Open Lab

Public research record of the Synareon project's coding-agent
experiments: what was tried, what was actually measured, and what
remains unknown.

**Guiding message: Synareon is investigating trustworthy coding-agent
completion through controlled experiments, including failures.**
No performance improvement is claimed anywhere in this repository
that is not demonstrated by sealed evidence.

## Why This Project Exists

Coding agents routinely produce output that *looks* finished while
being wrong, incomplete, or unverified. Synareon studies whether
explicit, deterministic checks (proposal contracts, verification
gates, sealed evidence) improve the rate at which agents reach
genuinely complete, evaluator-passing solutions — and publishes the
failures as carefully as any success.

## Experiment Timeline

### EXP-001 — Long-Horizon Feasibility (`TERMINATED_EARLY`)

SCBench 468-unit formal run stopped at 12 sealed units: the 1500s-class
budget envelope proved unfit for long-horizon execution (11 timeouts).
No benchmark verdict was made — the envelope, not the agent, decided.
[`experiments/EXP-001/README.md`](experiments/EXP-001/README.md)

### EXP-002 — Cost-Controlled Matrix (`EARLY_TERMINATED`)

468-unit formal run stopped at 86 sealed units by explicit Project
Owner decision: the B/D paired contrast rested on a single task, so
further measurement was not cost-efficient. Performance claim:
NOT_ESTABLISHED. [`experiments/EXP-002/README.md`](experiments/EXP-002/README.md)

### EXP-003 — Controlled Benchmark and Negative Results

132 planned units, 131 sealed + 1 censored (no imputation):
Qualified Completion 5/131 — A 1/33, B 4/33, C 0/32, D 0/33. The
evaluator ran on all 65 governed seals and passed none. A negative
result: no harness superiority demonstrated, none claimed.
[`experiments/EXP-003/RESULTS.md`](experiments/EXP-003/RESULTS.md)

## What We Learned

1. Budget envelopes decide long-horizon outcomes before quality can be
   measured (EXP-001) — calibrate timeouts first.
2. Paired coverage must be scheduled deliberately, and measurement cost
   fenced by decision evidence (EXP-002) — the stop protocol itself is
   the reusable part.
3. Narrower frozen benchmarks with hard gates produce decisive negative
   results instead of inconclusive large ones (EXP-003) — but governed
   failure modes still need separating from the hypothesis.
4. Across all three: incomplete and censored outcomes are preserved as
   findings, never imputed or topped up.

## What EXP-004 Will Test

Bounded repair proposals (packaging discipline, durable attempt
admission and liveness, no-progress controls, measurement projection),
each as a falsifiable micro-experiment. Status: PLANNED. No EXP-004
results are claimed.
[`experiments/EXP-004/EXPERIMENT_PLAN.md`](experiments/EXP-004/EXPERIMENT_PLAN.md)

## Evidence and Limitations

Aggregate results plus content hashes are public; raw per-unit streams,
transcripts, endpoints, and fixtures are not (disclosed, not hidden).
Limitations are part of the publication:
[`experiments/EXP-003/LIMITATIONS.md`](experiments/EXP-003/LIMITATIONS.md),
[`docs/EVIDENCE_AND_DISCLOSURE.md`](docs/EVIDENCE_AND_DISCLOSURE.md).

## Next Experiments

EXP-004 micro-runs first (proposal-packaging qualification, liveness
fault-injection, admission-field trial, observability-first timeout
work, seal-projection trial). No formal multi-lane launch is
authorized by the current plan.

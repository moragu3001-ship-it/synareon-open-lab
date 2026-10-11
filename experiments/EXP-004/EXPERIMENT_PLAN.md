# EXP-004 Experiment Plan (PROPOSALS ONLY — NO RESULTS CLAIMED)

```text
EXP-004 STATUS = PLANNED
EXP-004 FORMAL = NOT AUTHORIZED
EXP-004 RESULTS = NOT CLAIMED WITHOUT EVIDENCE
```

## Which EXP-003 findings motivate EXP-004

- 33/131 units failed first at proposal admission (12 genuinely ambiguous
  multi-block, 14 single-block other causes, 7 no-block); all governed QC
  is 0. (Proposal-packaging contract mismatch.)
- 1 censored unit with no durable attempt record; scheduler liveness gaps.
- 61 timeout-scope units; silent-hang classes with UNKNOWN runtime cause.
- Usage measured on 33/131 units only; governed-arm cost UNKNOWN.

## Proposed improvement hypotheses (hypotheses, not findings)

- **P0-1 prompt/packaging discipline:** enforced one-block completion
  discipline (instruction plus deterministic check). Proposed micro-run:
  prompt-ablation on frozen checkpoints measuring block-count
  distribution; fail-closed held.
- **P0-2 scheduler/liveness:** durable attempt admission plus
  lease/heartbeat plus fenced writers plus deterministic
  terminalization. Proposed micro-run: fault-injection qualification
  (kill coordinator mid-run; require deterministic terminalization).
- **P0-3 launch attempt authority:** pre-launch durable admission
  (attempt_id, budget fields) so launches are countable. Proposed
  micro-run: admission-field trial on a micro panel.
- **P0-4 runtime timeouts:** no-progress / tool-loop / token-velocity
  bounded escalation. Proposed micro-run: observability-first run
  before any envelope change (7200s envelope stays).
- **P1-1 measurement projection:** project raw usage into seals on all
  terminal paths. Proposed micro-run: seal-projection trial on replayed
  raw. R3 seals are never rewritten (additive future revisions only).
- **P1-2 packaging qualification then formal-envelope smoke re-run**
  before any EXP-004 formal run.
- **P1-3 CREATE parent-directory semantics:** architecture decision
  record first; no behavior change proposed here.

Each hypothesis above is explicitly a hypothesis. None has been tested.

## Bounded repair direction

Fix failure modes (packaging discipline, liveness, observability,
measurement projection) before re-measuring the harness hypothesis, so
a future run measures the hypothesis rather than its failure modes.
No scheduler rewrite, no timeout increase, no probabilistic merge
repairs are proposed.

## Experimental arms and comparison method (planned)

Same 2x2 structure (raw / skills-only / harness-only / skills+harness)
with paired denominators, censored-cell exclusion without imputation,
and the Qualified Completion hard gate (evaluator-passed + sealed),
unless the approved formal plan states otherwise. Comparisons remain
descriptive until event counts support more.

## Measurement metrics (planned)

Qualified Completion per arm; paired differences with N_paired;
terminal and first-failure distributions; censoring receipts;
usage/cost capture on ALL terminal paths (the EXP-003 gap being closed);
durable per-unit timing where the projection repair lands.

## Acceptance and rejection criteria (planned)

- Accept an improvement hypothesis only on pre-registered, paired,
  non-imputed gains with complete capture; reject on flat or negative
  paired differences, on censoring/imputation violations, or on
  fail-closed violations.
- A proposal-packaging fix must reduce admission-first-failures without
  merging ambiguous proposals (last-wins/guess repairs stay forbidden).

## Proposed next step: bounded 1-Lane feasibility (status note)

The current work-order direction proposes shortening the benchmark
lifecycle with a bounded 1-Lane feasibility experiment (one execution
lane, not necessarily one comparison arm) before broader multi-lane
measurements. Status: PROPOSED NEXT STEP ONLY — no experiment manifest
exists, no formal protocol is approved, and this proposal does not
replace or supersede the 2x2 structure above. Formal EXP-004 execution
requires its own approved manifest.

## Scope and known limitations

- Micro-runs first; no formal 4-arm launch is authorized by this plan.
- Lane==model confounding, small-event-count descriptiveness, and
  timeout-causality gaps carry over until the corresponding repairs land.
- Raw fixtures/skill packs are referenced by hash, never redistributed
  (redistribution rights unverified).

## What has not yet been measured

Everything in EXP-004. There are no EXP-004 results, no improvement
percentages, no savings figures, and no completion outcomes in this
publication. Any future numbers will appear only with sealed evidence.

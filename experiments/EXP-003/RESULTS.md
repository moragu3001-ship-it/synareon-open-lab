# EXP-003 Results (Frozen, Verified Against Sealed Evidence)

Source authority: EXP-003 Final Close `CLOSED_WITH_CENSORED_UNIT`
(HEAD `550c35f09a959f1b94fd5417d0463b5e392d23b9`,
TREE `cb17d815e3a4772563abe2a7bce56dbf8d53528d`,
PARENT `0fcaf7164feca82a74bb4d8863ee56caa69a1259`).
This document restates sealed evidence. It performs no re-execution, no
re-sealing, and no imputation. Nothing here claims harness superiority.

## Experiment question (hypothesis under test)

Does deterministic assurance (Synareon harness governance: proposal
contract + verification) improve trustworthy coding-agent convergence
over raw agent execution, with and without skills?

**Observed answer: no.** Governed arms recorded 0 qualified completions
against 5 on ungoverned arms, with 1 unit censored. The incomplete
termination itself is part of the result.

## Configuration (observed)

- 4 arms: A raw agent (baseline) / B skills-only / C harness-only /
  D skills+harness. Primary comparison D vs B.
- 3 lanes x 11 checkpoints = 33 TaskCells x 4 arms = 132 planned units.
- Agent envelope: codex-cli 0.160.0, 7200s timeout, retry 0.
- Lanes (lane == model == host == engine, confounded by design):
  L01 qwen3.8-27b / L02 ornith-1.5-9b / L04 agents-a1-4b.

## Qualified Completion (observed, hard gate = evaluator-passed + sealed)

| Arm | Sealed n | QC | Evaluator reached | Evaluator passed |
|---|---|---|---|---|
| A raw | 33 | 1 | 33 | 1 |
| B skills-only | 33 | 4 | 33 | 4 |
| C harness-only | 32 | 0 | 32 | 0 |
| D skills+harness | 33 | 0 | 33 | 0 |
| Total | 131 | 5 (3.8%) | 131 | 5 |

All 5 QC units are on LANE-L01. Nothing else (process success, proposal
admission, token volume) substitutes for this gate.

## Paired comparisons (observed, paired denominators, descriptive only)

- Skill effect B-A (n=33): 4-1 = +3.
- Harness effect C-A (n=32): 0-1 = -1.
- D vs B primary (n=33): 0-4 = -4. Skills-only beats skills+harness on QC
  in this run over 4 events: a descriptive gap, not significance.
- D vs A (n=33): 0-1 = -1.
- Synergy D-B-C+A (n=32 complete ABCD cells): 29 x 0, 3 x -1. No positive
  synergy anywhere. The censored cell is excluded, never imputed.

## Terminal and failure distribution (observed, 131 sealed)

Terminals: GOVERNANCE_BLOCKED 64 / EXECUTION_SUCCEEDED 33 / TIMEOUT 30 /
EXECUTION_FAILED 4. First authoritative failures:
PROPOSAL_PARSE_OR_ADMISSION 33 (all C/D) / AGENT_PROCESS 31 (all C/D) /
PROCESS_TIMEOUT 30 (A 12 / B 18) / EVALUATOR_FAIL 28 (all A/B) /
EXECUTION_SUCCEEDED 5 (= QC) / PROCESS_NONZERO 3 (B) / GOVERNED_FAILED 1 (C).
Raw arms reach the evaluator with passing-or-failing code (33
EXECUTION_SUCCEEDED, 28 of them EVALUATOR_FAIL = real code that fails
tests). No successful governed mutation was observed.

## Failure analysis (observed, preserved not hidden)

- Proposal packaging: 33/131 sealed units (25.2%) failed first at proposal
  admission; 33/65 governed units (50.8% of the observed governed
  population C 32 + D 33). Of 131 scanned proposal files: NO_BLOCK 104
  (A 33 / B 33 / C 17 / D 21; A/B no-block is by design through another
  channel), SINGLE_CANONICAL_BLOCK 15, MULTI_BLOCK_AMBIGUOUS 12,
  UNREADABLE 1 (censored unit). Cross-check of the 33 admission failures:
  12 genuinely ambiguous multi-block (fail-closed rejection correct),
  14 single-block rejected for other parse causes (leading prose confirmed
  8/8), 7 no-block. Rejections were never merged. Model-internal motive
  for multi-block output is UNKNOWN.
- Liveness: 61 timeout-scope units (30 TIMEOUT + 31 AGENT_PROCESS stalls);
  by arm A 12 / B 18 / C 14 / D 17 — raw arms time out too (30/66 A/B =
  45.5%: the envelope binds regardless of governance). By lane L01 9 /
  L02 20 / L04 32. Forensics buckets: SSE_STALL_TRACE 18 (trace only, not
  a verdict), RAW_TRUNCATED_AT_CAPTURE_CAP 11 (runtime cause UNKNOWN),
  NO_TRACE_UNKNOWN 32 (all L04).
- Censoring: 1 unit, `EXP-003-F--LANE-L02--env_manager-04--C`
  (`CENSORED_NO_DURABLE_ATTEMPT` /
  `DISPATCH_STATE_UNKNOWN_NO_DURABLE_RECORD`), excluded from every
  denominator, never imputed. Sensitivity bounds move no
  experiment-level conclusion (B-vs-D stays 4:0 under both bounds).

## Usage and cost (observed range only)

MEASURED usage exists for 33/131 units (all A/B): in 258,849,176 /
out 2,788,285 / cached 255,916,072. 98 units UNAVAILABLE (all C/D plus
timeout scope). Governed-arm cost is UNKNOWN, not zero. No durable
per-unit wall-time exists. Any token/cost/latency comparison across arms
is structurally one-sided.

## What can and cannot be concluded (interpretation labels)

- OBSERVED: governed arms produced zero QC and zero evaluator passes;
  B beat D 4:0 on QC descriptively; proposal admission blocked 33
  governed units first; timeouts bind all arms.
- INTERPRETATION: EXP-003 is a negative result for the harness hypothesis
  as implemented; failure modes (packaging, liveness, measurement) were
  not separated from the hypothesis and must be repaired before the
  hypothesis itself is measurable.
- NOT SUPPORTED: superiority claims, model rankings, cross-lane or
  cross-experiment trends, significance language, cost comparisons.

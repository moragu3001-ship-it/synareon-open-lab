# EXP-003 Methodology (Observed Design)

## Arms

- A raw: agent without skills or harness governance (baseline).
- B skills-only: frozen skill prefix, no governance.
- C harness-only: Synareon governance (proposal contract + verification),
  no skills.
- D skills+harness: full treatment. Primary comparison D vs B.

## Paired comparisons (paired denominators)

Skill effect = B-A; harness effect = C-A; D vs B = primary; synergy =
D-B-C+A on complete ABCD cells only. Every comparison reports N_paired;
censored/missing cells are excluded, never imputed. Sensitivity bounds
(best/worst-case) may be shown alongside but never replace primary metrics.

## Qualified Completion (hard gate)

Evaluator-passed + sealed. Nothing else (process success, proposal
admission, token volume) substitutes. No alternative metric was used.

## Fail-closed contract

Ambiguous or multi-block proposals are rejected, never merged or
last-wins. Blocked does not mean succeeded. Timeouts are
right-censoring, not convergence times.

## Evidence authority

Raw event outranks derived event outranks summary projection.
Ledger/progress/seal hashes pin every claim. Missing evidence is
reported as UNKNOWN, never estimated into existence.

## Termination honesty

Early/incomplete termination is a first-class outcome with receipts
(termination receipt, censored-unit receipt, terminal seal). Runs are
never topped up to round numbers. EXP-003-F R3 ended
`TERMINATED_INCOMPLETE` with 131/132 sealed and 1 censored unit.

## Environment (observed)

Agent transport Codex CLI (SSE) 0.160.0; 7200s envelope; retry 0.
Lanes L01 qwen3.8-27b / L02 ornith-1.5-9b / L04 agents-a1-4b with
lane == model == host == engine (confounded by design; no model
comparison is supported). Harness source revision for the sealed run is
pinned in the terminal seal; publication source authority HEAD
`550c35f09a959f1b94fd5417d0463b5e392d23b9`.

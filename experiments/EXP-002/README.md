# EXP-002 — Formal Matrix with Owner Cost Control (EARLY_TERMINATED)

## Objective

Test whether the primary skills-vs-governed (B/D) performance contrast
is measurable over the formal 468-unit matrix, with the Project Owner
able to stop execution when continued measurement stops being
cost-efficient.

## Setup

- Formal run `exp002-formal-001` under manifest `7588db81…` (truncated
  reference; full value in the census record).
- Lanes L01/L02/L04 (qwen38/ornith15/agents-a1 bands); arms codex_raw /
  codex_skills / codex_skills_synareon / codex_synareon.
- Owner stop protocol with pre/post-stop snapshots and quiescence checks.

## Observed Results

- Status `EARLY_TERMINATED` by PROJECT_OWNER decision
  (`MEASUREMENT_COST_LIMIT + DECISION_EVIDENCE_INEFFICIENCY`).
- **86/468 sealed** (EXECUTION_SUCCEEDED 51, TIMEOUT 33,
  EXECUTION_FAILED 2); sealed by arm 77 / 3 / 3 / 3; duplicates 0.
- Stopped with 3 units still RUNNING, preserved as-running with no
  terminal fabricated; no new admissions after the stop request
  (86 -> 86); no source files changed; no evidence mutated.
- Performance claim: **NOT_ESTABLISHED** (owner decision record).

## Failures and Limitations

- The available B/D paired coverage was limited to one unique task,
  circuit_eval-01, observed across three lanes. These lane-level
  observations do not provide sufficient task diversity to establish
  the primary performance hypothesis, which remains NOT_ESTABLISHED
  (not refuted) after arm-major scheduling collapsed paired coverage.
- 382 units unsealed. No graceful-stop runner command existed (stop by
  quiescence verification, no kills performed).
- Agent version for this run is not verified in the cited records.

## Lessons Learned

Paired coverage must be scheduled deliberately (arm-major scheduling
destroys it), and measurement cost must be fenced by decision evidence
per unit spent — the stop protocol itself (snapshots, quiescence,
append-only evidence) worked as designed and is the reusable part.

## Next Step

EXP-003 narrowed the ambition to a 132-unit controlled benchmark with
frozen arms, paired denominators, and a hard Qualified Completion gate
— trading matrix size for decisiveness. See `../EXP-003/RESULTS.md`.

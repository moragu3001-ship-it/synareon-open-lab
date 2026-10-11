# EXP-001 — SCBench Long-Horizon Feasibility (TERMINATED_EARLY)

## Objective

Determine whether the SCBench long-horizon benchmark (468 planned units,
4 arms x 3 lanes) can be executed to completion inside the proven budget
envelope (1500s-class timeouts, 1M-token budget, 0 retries).

## Setup

- Formal run `exp001-formal-001`, authorized by frozen three-lane
  manifests (pre-execution gates passed), revision
  `b23a3c2c545464069c8a3afa5b49eac0cb6a3587`.
- Agent codex 0.146.0; lanes L01 qwen3.8-27b / L02 ornith-1.5-9b /
  L04 agents-a1-4b (LANE-L03 excluded, 0 units).
- Arms: codex_raw / codex_skills / codex_synareon /
  codex_skills_synareon.

## Observed Results

- Status `TERMINATED_EARLY` (not closed): **12/468 units sealed**
  (EXECUTION_SUCCEEDED 1, TIMEOUT 11).
- Reason: `FORMAL_BUDGET_ENVELOPE_NOT_FIT_FOR_SCBENCH_LONG_HORIZON_EXECUTION`.
- The receipt explicitly declares NO verdict: no BENCHMARK_PASS/FAIL,
  no SYNAREON_BETTER/WORSE, no EXP-001 CLOSED.

## Failures and Limitations

- 11 of 12 sealed units timed out — informative about the envelope, not
  about solution quality.
- LANE-L03 excluded from the formal run; 1 holdout task exposed.
- A separate harness-verification track (R3 lineage) is STOPPED pending
  a bounded verifier repair; it is not a benchmark result and is not
  merged here.

## Lessons Learned

Long-horizon agent execution under short per-unit envelopes produced
almost entirely timeouts: eleven of twelve sealed units terminated
with TIMEOUT under the configured 1,500-second envelope. This
prevented a meaningful assessment of completion quality; outcomes
under longer or different envelopes remain unknown. Future runs need
calibrated per-checkpoint timeouts or a redesigned envelope before
any quality comparison is attempted.

## Next Step

EXP-002 kept the matrix ambition but added owner-side cost control:
terminate early by explicit owner decision rather than by envelope
exhaustion. See `../EXP-002/README.md`.

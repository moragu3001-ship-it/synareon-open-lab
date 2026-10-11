# EXP-003 Known Limitations (Mandatory Reading)

These limitations are part of the publication. Any citation of EXP-003
results without them is incomplete.

1. **Not a complete 132/132 experiment.** 131/132 logical units sealed;
   execution status `TERMINATED_INCOMPLETE`; lifecycle
   `CLOSED_WITH_CENSORED_UNIT`. The incomplete termination itself is the
   result — the run was never topped up to round numbers.
2. **One unit is censored and was not imputed.**
   `EXP-003-F--LANE-L02--env_manager-04--C`
   (`CENSORED_NO_DURABLE_ATTEMPT` /
   `DISPATCH_STATE_UNKNOWN_NO_DURABLE_RECORD`). No PASS/FAIL/TIMEOUT value
   was fabricated. All rates use observed N; paired comparisons use
   actually-paired N. The missing C is irrecoverable data, not a rounding
   choice.
3. **Governed arms reached the evaluator but recorded 0 QC.** The
   evaluator ran on all 65 governed seals (C 32 + D 33 reached) with 0
   passes and 0 qualified completions. No successful governed mutation
   was observed.
4. **Harness effect is not separated from model/runtime failure.**
   Governed-arm failures combine proposal-contract rejection (33),
   agent-process stalls (31), and one governed failure — the harness's
   own failure modes were not measured separately from the hypothesis
   under test. Proposal discipline, durable attempt admission plus
   liveness, and bounded no-progress controls are prerequisites to
   measuring the harness hypothesis rather than its failure modes.
5. **Some usage/duration measurement is incomplete.** Token usage
   MEASURED for 33/131 units only (all A/B); 98 units UNAVAILABLE;
   governed-arm cost UNKNOWN, not zero. No durable per-unit wall-time;
   per-unit exit codes and kill timestamps unsealed. Any token/cost/
   latency comparison across arms is structurally one-sided.
6. **Lane == model confound.** Lane == model == host == engine by design.
   No model ranking, no cross-lane claim, no cross-experiment score trend
   (protocols differ across EXP-001/002/003). Paired comparisons are
   descriptive only (QC rests on 5 events; B-vs-D on 4).
7. **R6 is follow-up architecture repair, not an EXP-003 result.** R6
   implementation is separately closed; R6 smoke is
   `CLOSED_WITH_NEGATIVE_QUALIFICATION`; no live unit has ever reached
   the R6 set route, so set-route behavior is unknown, not failed.
   R6 results must not be merged into EXP-003 numbers.
8. **Counterfactual replays are separate analyses**, not part of the
   EXP-003 original results.
9. **No follow-up formal-benchmark result is claimed here.** The formal
   benchmark is not approved; nothing in this publication asserts
   follow-up outcomes or schedules.
10. **No superiority, completion, or readiness claim.** EXP-003 is
    published as failure truth: negative result, incomplete execution,
    preserved censoring.
11. **No public raw.** Public artifacts are aggregate-only sanitized
    derivatives; public document integrity is checkable through the
    Git commit and blob identities of this repository. Full
    reproduction needs internal evidence; raw streams are not part of
    this publication (neither as commits nor as Release assets).
    Frozen tasks are identified by references to the frozen harness
    inputs — no task or fixture hash values are published in this
    repository, and fixture content is never redistributed.

# Evidence and Disclosure

## Canonical sources (internal, authoritative, not redistributed)

EXP-003-F R3 sealed evidence: final results JSON/CSV, arm comparison,
failure census, censoring note, final analysis, terminal seal, censored-unit
receipt, seal inventory, measurement-projection census, and the four RCA
notes (proposal packaging, runtime timeout, scheduler liveness,
measurement projection). Source authority revision HEAD
`550c35f09a959f1b94fd5417d0463b5e392d23b9`.

## What is public here

Aggregate results, paired differences with denominators, failure
distributions, censoring receipts in aggregate form, and content hashes.
Every numerical result in `experiments/EXP-003/RESULTS.md` was recomputed
from the unit-level sealed evidence (132 rows: 131 sealed + 1 censored)
before publication; the claim-to-evidence record is retained by the
authors and available to reviewers on request.

## What is private and why

Raw per-unit JSONL streams (~81.7MB), session transcripts, internal
endpoints/URLs, host identifiers, and benchmark fixture/skill-pack
contents. Reasons: participant-adjacent operational data, unverified
redistribution rights for third-party fixtures, and size. Their absence
is disclosed rather than hidden: full per-unit reproduction is not
possible from this package alone.

## Reproducibility statement

An independent run is a NEW experiment, not a verification of these
sealed units. Agreement is expected only at the level of failure modes
(governance blocking, timeout classes, censoring risk), never at
per-unit outcomes. Prerequisites: lane models (or declared substitutes —
substitution breaks comparability), Codex CLI 0.160.0 (or declared
equivalent), frozen task panel reconstructed from hashes, and the
measurement-projection fixes listed as EXP-004 requirements for governed
cost capture.

## Disclosure of negative and incomplete outcomes

Published alongside results: incomplete termination (131/132),
preserved censoring without imputation, zero governed QC, one-sided
cost data, lane==model confounding, unknown timeout causality for 32
silent units, and the EXP-004 plan status (planned, no results).

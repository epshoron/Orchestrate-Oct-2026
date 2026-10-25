# Technical Audit Brief — Before Implementation

## Goal

Decide what the challenge actually asks the program to compute, what evidence must be reconstructed, and which practical architecture is justified by the *supplied dataset*. **Do not predetermine that a multi-agent LLM design is required.**

## A. Reality check

- Identify the current local original checkout path, Git head, changed/untracked files, Python environment, and whether an actual solution exists.
- Distinguish completed setup from completed problem-solving work.
- Confirm mandatory logging in the original repo's root `log.txt`; preserve native Codex session traces.
- Briefly record any blocking issues. Do not rewrite data or source code.

## B. Precise input → output contract

- Confirm dataset tables, joins, schemas, time fields, 518 request rows, 32 labeled sample cases, evidence-manifest scope, and all deletion-policy categories.
- Explain **one real participant-visible sample case end-to-end**, with source file, timestamp, actual identifiers, relevant state, applicable rule, and expected steps.
- Describe how a request (intent) differs from an audit finding (grounded in records), a remediation proposal (future action), and a verification step.
- Verify that output must be a root-level `output.csv` with `case_id,deletion_status,steps_json`, with strict operation/state/evidence/ordering requirements.

## C. Evidence coverage / difficulties

Inspect, do not just count, examples of all available modalities: CSV, SQL snapshots (primary vs replicas), logs, JSON, text records, PDF and images. Identify which formats really exist and where.

Investigate:
1. Identity linking: old/new emails, phones, hashes, stable `user_id`; avoid false linkage to lookalikes.
2. Temporal truth at each case's `audit_at`; exclude evidence after cut-off; do not treat reported SUCCESS as proof.
3. Cross-system records, dangerous sync/import, failover replicas, restore paths, retention obligations, tombstones.
4. Evidence citation validity and which steps require a blank vs nonblank `evidence_id`.
5. Ambiguous or contradictory rules (including operation ordering vs dependency ordering; report-location discrepancies; trace-upload instructions).

## D. Architecture without assuming the answer

Compare and justify:
- Deterministic Python/rules/indexing.
- Python + selective language/VLM extraction.
- LLM-heavy autonomous agent.

For each, state: what components genuinely benefit from AI, what can be cached or preprocessed once, likely error modes, reproducibility, token/cost implications, scalability beyond a toy dataset, and feasibility with the remaining time. **No invented accuracy, cost, or speed estimates.**

## E. Competitive quality and evaluation

Specify how a baseline would be evaluated on all 32 released sample labels: case/status accuracy, step precision/recall or exact match, field/evidence correctness, step ordering, runtime, and actual model cost if used. Identify robustness tests for false matches, post-cutoff evidence, conflicting replicas, sync/restore, legal retention, and non-deletion intent. Do not use hidden answers or hardcode known labels.

Propose a practical improvement/ablation plan, including how to measure if optional LLM reasoning improves on deterministic parsing. Describe the most credible differentiators supported by measurement, not superficial agent count.

## F. Deliverable and stop condition

Codex should write:
- `coordination/CODEX_STATUS.md`: updated project status, what was checked, what has not yet been implemented, blockers and next task.
- `coordination/CODEX_AUDIT.md`: focused analysis with actual file paths/examples, architecture alternatives, recommendation, explicit remaining unknowns.
- Existing original-repo `log.txt`: append authentic audit interaction only, following `AGENTS.md`.

Commit and push **only these coordination reports**, not raw evidence, secrets, raw trace, original dataset, or source code. Confirm the remote commit SHA.

**STOP after audit. Do not develop the competition solution or submit anything until the user explicitly authorizes that scope.**

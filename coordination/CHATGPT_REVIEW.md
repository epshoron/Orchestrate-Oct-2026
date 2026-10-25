# ChatGPT Review — Initial Context

**Status:** Awaiting Codex's local, data-grounded audit. This is not a completed implementation review.

## Verified from official participant repository

- Challenge: *Ghost Data Still Exists*, official source: https://github.com/interviewstreet/hackerrank-orchestrate-october26
- Expected: one audit result per each of **518** rows in `dataset/deletion_requests.csv`, sorted by `case_id`.
- Output: `case_id,deletion_status,steps_json` with findings, future remediation, and verification ordered and grounded as specified.
- Public development evaluation: **32** requests in `sample_deletion_requests.csv` with canonical `sample_output.csv`.
- Evidence manifest tracks **94** files in the local setup report; original formats include SQL, screenshots, PDFs, records and logs.
- `deletion_rules.csv` has **15** policies. Required treatments include DELETE, REDACT, ANONYMIZE and RETAIN.
- The public case_05 sample is INCOMPLETE even though the previous workflow reports COMPLETE: `evidence_54` (failover replica SQL) contains `account_005` even though it is not in the primary table.
- A valid response is a machine-readable **proposed audit/remediation plan**, not actual mutation of the fictional organization's systems.

## What we cannot verify remotely yet

- Whether local Codex has started developing since the earlier environment-only report.
- Actual environment access, future model/runtime token usage, or runtime correctness.
- Whether the best competition architecture is fully deterministic, hybrid, or more agentic; that decision requires sample-driven evaluation.
- Whether a separately requested `agent-trace.zip` has an additional official upload slot; preserve traces meanwhile.

## Questions for Codex to answer

1. Which data relationships are explicit and reliably joinable? Which require semantic processing?
2. How much evidence can be parsed/indexed once and reused across cases?
3. What are the genuine hard cases: replica drift, identifier history, time cutoffs, lookalikes, multi-language deletion intent, retention and sync/restore?
4. What would a minimal runnable baseline miss, and how can its misses be measured?
5. How can a human explain/defend architecture, failure modes and measured improvements in the AI Judge interview?

## Coordination ownership

ChatGPT edits this file only; Codex edits `CODEX_STATUS.md` and `CODEX_AUDIT.md`. Await user approval for architecture and full implementation.

# Independent Technical Audit - Sanitized Summary

Published: 2026-10-25. Basis: the completed independent read-only audit, whose final local status check was at 18:23 Asia/Shanghai on that date. Publication did not repeat the audit or inspect the competition checkout again. This is an audit snapshot, not a live development report.

The user explicitly authorized this sanitized summary for the existing public coordination repository. It contains aggregate observations and technical conclusions, without dataset rows, personal identifiers, evidence excerpts, credentials, local machine details, development logs, or native traces. No competition solution was implemented or executed by this audit session. Prior ChatGPT reviews and speculative architecture recommendations were not used to form the independent assessment.

## 1. Actual task and output contract

The task is evidence-based deletion auditing at each request's `audit_at`, rather than executing deletion against live systems. It requires establishing deletion authorization, resolving current and historical identities, locating relevant resources, reconstructing their state, applying supplied policy, and detecting processes that could recreate prohibited data.

The required output has 518 rows and the columns `case_id,deletion_status,steps_json`. `COMPLETE` contains evidence-backed verification; `INCOMPLETE` contains findings, remediation, and future verification; `NOT_APPLICABLE` contains an empty array. Findings and current-state verification cite participant-visible evidence IDs. Proposed remediation and future verification use empty evidence IDs. Phase, operation, system, resource, and step-number ordering are contractual requirements.

The [official problem statement](https://github.com/interviewstreet/hackerrank-orchestrate-october26/blob/0eddbbd33f682eae0a2770d67412af8a3cf4af20/problem_statement.md) supplies the detailed contract. Hidden answers are unavailable. Published scoring dimensions do not establish score weights or whether multiple equivalent evidence citations are accepted.

## 2. Verified dataset observations

These counts were calculated from participant-facing files during the completed audit. They are inventory and linkage diagnostics, not prediction results.

| Source | Verified observation |
| --- | --- |
| `deletion_requests.csv` | 518 evaluation requests |
| `sample_deletion_requests.csv`, `sample_output.csv` | 32 separate public samples; expected statuses comprise 10 complete and 22 incomplete cases, with no not-applicable example |
| `user_identities.csv` | 850 current identity records |
| `user_audit_log.csv` | 306 historical identity changes |
| `system_activity.csv` | 4,011 activity records |
| `evidence_files.csv` and evidence inventory | 94 files, approximately 2.93 MB: 24 SQL, 28 JSON, 26 log, 11 PNG, 4 PDF, and 1 text file; all manifest paths existed |

Case-insensitive email-key matching covered all 518 evaluation requests: 418 matched the current identity table and 100 matched only historical email values. A case-sensitive lookup missed 20 requests. This establishes key coverage, not correct temporal identity reconstruction or complete resource discovery.

Concrete observations, without reproducing source contents:

- SQL evidence demonstrated a profile absent from the primary database but still present in a failover replica. Replica coverage is necessary even when primary deletion succeeded.
- One SQL inventory created nine tables while its `snapshot_scope` covered only the account service. Empty tables outside the declared scope cannot establish absence in other services.
- Log records separated identity-bearing lookup events from resource-bearing results. Trace correlation and historical hashes were necessary to connect those facts.
- The activity file contained appended events outside chronological row order. Temporal processing must use timestamps rather than row position.
- Public samples contradicted reported workflow status in both directions. Samples also demonstrated audit cutoffs, similar-identity decoys, historical identifiers, retained records, and tombstones.
- Expected verification covered resources already compliant as well as resources needing remediation. A plan limited to changed resources would omit required checks.
- The evidence manifest described origin and capture time, not case membership. Filename or manifest matching alone is insufficient.

## 3. Main technical and scoring risks

1. **Authorization:** deletion keywords alone can misclassify negation, marketing-only requests, corrections, or exports. The public sample suite lacks the not-applicable class.
2. **Temporal provenance:** preserve observation times, file capture/export times, identity history, and snapshot scope. Do not let later evidence change an earlier audit answer or assume the newest filename proves current state.
3. **Identity and retrieval:** normalize carefully, retain historical identifiers and hashes, and correlate resources through grounded links. Similar names or addresses are insufficient ownership evidence.
4. **Policy application:** choose treatment from category and applicable condition, not system name alone. Retention, redaction, anonymization, deletion, and permitted tombstone references have different requirements. The supplied policy governs the task; additional legal assumptions are unnecessary.
5. **Negative evidence:** distinguish an explicit unsuccessful lookup or a scoped complete snapshot from an unobserved resource. A missing search hit in incomplete evidence does not prove deletion.
6. **Planning and serialization:** account for data flows and restore risks before dependent changes, preserve required retained resources, include the complete verification set, and serialize using the explicit contest comparator.
7. **Evidence selection:** a plausible finding with a wrong, stale, or unsupported citation can lose credit independently of status correctness. Equal-time conflicts and equivalent-citation acceptance remain evaluation uncertainties.

## 4. Feasible architecture alternatives

| Alternative | Strengths | Tradeoffs to measure |
| --- | --- | --- |
| Format parsers, OCR, identity indexes, and deterministic rules | Reproducible decisions, transparent provenance, low marginal runtime cost | Coverage of heterogeneous formats, intent boundaries, and extraction errors must be maintained |
| LLM/VLM-led investigation and output generation | Flexible handling of language and unfamiliar documents | Omissions, unsupported citations, temporal errors, sequence mistakes, repeatability, latency, and token cost |
| Structured evidence layer, targeted AI extraction or intent handling, deterministic decisions and output | Extraction and reasoning can be evaluated separately; model calls can target unresolved inputs | Requires a clear fact schema, uncertainty handling, caching, and validation between components |

No architecture was implemented or benchmarked in this audit, so none is an empirically established winner. The observed corpus size supports parsing shared evidence once and indexing identities, resources, and times, rather than repeatedly sending the entire corpus for every request.

No component was demonstrated to require an LLM computationally. Identity linkage, timestamp filtering, policy application, planning, and serialization can be deterministic. Multilingual authorization and screenshot fact extraction are the strongest candidates for measured AI assistance; PDF text extraction and conventional OCR are also feasible options. The official AI-agent framing does not, by itself, establish acceptance of a purely rules-based submission, and the inspected contract did not specify a model call for every request. Eligibility and quality should not be inferred from model-call count.

## 5. Evaluation and differentiation

Use the same evaluation set to compare alternatives and ablations. Report actual measurements, including:

- Status confusion matrix and false-complete errors, alongside case accuracy and class-sensitive metrics.
- Step precision/recall, field accuracy, and exact ordered-sequence agreement after JSON parsing.
- Evidence-ID validity, temporal admissibility, extraction coverage, and unresolved inputs; retrieval recall requires an independently labeled resource subset.
- Repeat-run output agreement, end-to-end latency, peak memory, and cache effectiveness.
- Actual provider/model calls, input/output tokens, totals, per-request costs, and extraction-versus-case-processing costs.

At least three additional participant-created cases should cover authorization negation or limited scope, future evidence or a similar-identity decoy, and retention/tombstone/restore behavior. Keep custom cases distinct from official samples and report their provenance. Development-set sample agreement must not be presented as hidden-dataset accuracy.

## 6. Recommended priorities for the primary development session

1. Establish a runnable end-to-end path and strict output-contract validation.
2. Cover historical identity resolution, scoped negative evidence, audit cutoffs, replicas, and the full verification set before adding architectural complexity.
3. Compare public samples at step and field level, add the missing boundary cases, and use measured failures to decide where AI assistance is useful.
4. Perform the authorized final full-dataset run in the primary development session, recording real usage and reproducibility information.
5. Complete `code/evaluation/evaluation_report.md`, `code/evaluation/usage_report.md`, execution instructions, and packaging checks. The [official README](https://github.com/interviewstreet/hackerrank-orchestrate-october26/blob/0eddbbd33f682eae0a2770d67412af8a3cf4af20/README.md) specifies the submission layout.

The audit did not establish runtime performance, model costs, a passing implementation, or any evaluation score. Implementation readiness at the inspected snapshot is recorded in [CODEX_STATUS.md](CODEX_STATUS.md).

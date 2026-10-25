# Orchestrate October 2026 — Collaboration Protocol

## Purpose

This is the lightweight **coordination repository**, not the competition's source-code or dataset repository.

- Official starter repository: https://github.com/interviewstreet/hackerrank-orchestrate-october26
- User's LOCAL solution checkout (Windows): `D:\Orchestrate Oct 2026\hackerrank-orchestrate-october26`
- SHARED coordination repository: https://github.com/epshoron/Orchestrate-Oct-2026
- Event submission deadline supplied by the user: **2026-10-25 20:30 Asia/Shanghai**. Verify any later official changes.

The owner uses local **Codex Desktop** for execution and ChatGPT for independent review. Both can interact with GitHub, but ChatGPT cannot automatically see files or unsynced changes on the user's Windows machine, and cannot monitor this repo in the background. A new ChatGPT read/review is initiated when the user asks.

## File ownership: prevent conflicts

| File | Writer | Purpose |
| --- | --- | --- |
| `coordination/WORKFLOW.md` | ChatGPT | Stable coordination protocol |
| `coordination/AUDIT_QUESTIONS.md` | ChatGPT | Agreed technical-audit scope |
| `coordination/CHATGPT_REVIEW.md` | ChatGPT | Independent reviews, questions, recommendations |
| `coordination/CODEX_STATUS.md` | Codex | Current local reality, completed work, blockers, next actions |
| `coordination/CODEX_AUDIT.md` | Codex | Data-grounded technical audit and architecture comparison |
| `coordination/DECISIONS.md` | Codex (after user confirms) | Decisions made by the user, with rationale and date |

Writers should not overwrite the other side's files. If responding to each other, refer to the other document and write the response in your own designated file. Pull/fetch the latest `main` before reading or editing; commit and push your own updates, then verify remote visibility.

## Separation of workspaces

1. Keep the *official starter checkout* and the *collaboration repository checkout* as **separate sibling directories**. Do not nest one repository inside the other.
2. Work on the actual competition project from its **original repository root**, honoring its `AGENTS.md` and writing the required append-only `log.txt` there.
3. The collaboration repo stores concise, shareable engineering reports and decision records only, not duplicated datasets or implementation artifacts.
4. **Never** push datasets, evidence binaries, local environment files, `.env`, tokens, credentials, raw Codex traces, `log.txt`, private personal data, or potentially sensitive source contents into this coordination repo. This repo is currently **public**.
5. Codex should use authenticated Git to push coordination updates. If push fails, report the blocker, leave local work intact, and avoid inventing a successful sync.
6. Maintain the user's ability to submit the three core files (`code.zip`, `output.csv`, `log.txt`) independently. The separate `agent-trace.zip` request in the official trace instructions needs upload-slot confirmation.

## Collaboration cycle

- **Codex** checks local repo reality and publishes `CODEX_STATUS.md` and, when requested, `CODEX_AUDIT.md`.
- **ChatGPT** fetches those reports directly from GitHub, verifies critical claims against official contest materials where possible, and writes `CHATGPT_REVIEW.md`.
- **Codex** pulls the review and acts only on the approved scope.
- **User** approves major tradeoffs, architecture shifts, external publication, and final submission.

No implicit background execution, automatic periodic checks, or automatic local/cloud context sharing is assumed.

## Audit mode vs implementation mode

Until the user authorizes implementation, **audit only**: permitted to inspect files and run lightweight non-mutating diagnostics, prohibited from developing an algorithm, modifying the dataset, generating `output.csv`, launching inference, packaging, or submitting. A concise, evidence-based recommendation is enough to conclude the audit.

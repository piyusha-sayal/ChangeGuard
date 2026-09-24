# ChangeGuard: Implemented Technical Architecture

This document describes what is actually installed and was observed running in the environment
**ChangeGuard-Hardening-Test** (Developer environment, Canada region, Dataverse
`<org>.crm3.dynamics.com`, environment id `<environment-id>`, verified live on
2026-09-23). It is not a roadmap. Every statement points to collected evidence; evidence IDs refer to
`Evidence_Manifest.md`.

All project data is synthetic. The final demonstration uses project `CGDEMO-FINAL-01` (Harbour Crane
Retrofit) and request `CR-CGDEMO-FINAL-01-CGDEMO-M1-2026-10-30-B1`.

## 1. Components at a glance

| Layer | Implementation | Evidence |
|---|---|---|
| Conversational agent | Copilot Studio agent **ChangeGuard Hardened Standard** (bot `f7a66f65-3bb6-f111-aaad-000d3af45a09`), classic runtime with generative (Standard) orchestration | 02_Copilot_Studio/Agent_Inventory.md, CS-01 |
| Agent tools | 7 tools, each an agent flow with a `Skills` trigger | CS-02, tool-to-flow-links.raw.json |
| Workflow engine | 10 hardened Power Automate cloud flows, all Activated | 03_Power_Automate/Flow_Inventory.md, PA-14 |
| Reviewer UI | Model-driven app **ChangeGuard Reviewer Test** with a read-only review form | 04_Power_Apps/Reviewer_App.md, PAPP-10 |
| System of record | 11 Dataverse tables, publisher prefix `cr458` | 05_Dataverse/Schema_Report.md, DV-17 |
| Security | 4 custom roles, 1 automation application user, 1 connection reference | 08_Security_and_Governance/Security_Roles_Report.md, SEC-01 |
| Packaging | One unmanaged solution `ChangeGuard` 1.0.0.0, 60 components | 01_Solution_Export |

## 2. Copilot Studio orchestration

The agent receives the project manager's message, selects tools through generative planning, and reports
only what the tools return. The stored transcripts show `DynamicPlanStepTriggered` and
`DynamicPlanStepFinished` events around each tool call (02_Copilot_Studio/historical_conversations).
The instructions (02_Copilot_Studio/Agent_Instructions.txt) forbid inventing dates, approvals or save
results and state that the agent is not the approver. No knowledge sources are configured; the tools are
the only data source. The bot record shows `publishedon` empty and the Publish button was active at
collection time, so the agent was exercised through the Copilot Studio test surface, not a published
channel.

## 3. Seven integrated agent tools

| Tool (display name) | Flow | Purpose (from the conversation evidence) |
|---|---|---|
| CG Get Project Baseline Hardened | 9b71c970 | Read project, milestones and calendar |
| CG Assess Change Hardened | 96b930bc | Deterministic working-day impact and verdicts |
| CG Compare Recovery Options Hardened | e87c17cc | Evaluate documented options as of a date |
| CG Simulate Recovery Option Hardened | ceead4d9 | Re-run the assessment with an option applied |
| CG Save Change Request Hardened | 4b12aa58 | Persist the request and its Saved audit row |
| CG Get Recovery Status Hardened | 5e7f18e6 | Report status, decision, work items, audit trail |
| CG Execute Hardened | 16e39304 | Execute an approved plan, idempotently |

Copilot Studio only exposes a flow's required trigger inputs to a tool; the save flow therefore marks the
original-evidence input as required, and the stored request carries the user's original wording.

## 4. Ten hardened Power Automate flows

The seven tool flows above plus three decision flows: **CG Approve Hardened** and **CG Reject Hardened**
(Dataverse "row selected" trigger, run from the reviewer app) and **CG Decide Hardened** (manual button
trigger). All use the connection reference `cr458_ChangeGuardDataverse` (Dataverse connector), whose
description requires it to resolve to the CG Automation service-principal connection. Definitions are in
03_Power_Automate/Flow_Definitions as exported clientdata JSON.

## 5. Dataverse architecture

Eleven tables: CG Project, CG Milestone, CG Dependency, CG Dependency Closure, CG Calendar Day,
CG Recovery Option, CG Change Request, CG Recovery Action, CG Audit Event, CG Claim, CG Eval Result.
Nine carry an active alternate key (request key, event key, action key, option code, project code,
milestone+project, calendar code+date, closure ancestor+descendant+project, claim key). CG Dependency and
CG Eval Result have none. Full column and relationship detail: 05_Dataverse/Schema_Report.md.

## 6. Power Apps reviewer and human decision authority

The review form shows the request, original evidence, milestone and project baselines, the selected
option and the raw assessment. All 16 field controls are disabled and the two quick views are display-only.
A decision is possible only by running CG Approve Hardened or CG Reject Hardened from the record's Flow
menu (PAPP-10b). The approval flow checks the reviewer against the project's approver list before writing.
For the final request the decision was recorded by the human reviewer on 2026-09-22 16:02:56 UTC
(12:02 EDT), run `08584115139116571959138843143CU31` (PA-08a, DV-19).

## 7. Service-principal execution

Rows written by the flows are created by the application user **# ChangeGuard-Automation** (accessmode 4),
not the maker. The final change request's owner is `# ChangeGuard-Automation` (PAPP-12-13) and every
automated audit row names the actor "ChangeGuard Control Tower agent (flow connection identity)". The
human approver appears only in `cr458_approvedby` and as the DecisionRecorded actor.

## 8. Request persistence

The save flow generates the request id before a Dataverse `ExecuteChangeset`, then creates the request and
the `Saved` audit row inside the same changeset, so either both exist or neither does. Result for the demo:
status `Created`, request status `PendingReview` (PA-05b, run `08584115247919949644217097079CU03`).

## 9. Approval guards

The approve/reject flows re-read the request, require a valid state transition, check the reviewer against
the approver list, validate the selected option against the catalogue as of the decision, take a claim row
on a unique key to prevent concurrent decisions, and write status plus `DecisionRecorded` audit in one
changeset.

## 10. Execution guards

CG Execute Hardened re-reads the request and requires a recorded approval, re-reads the newest
DecisionRecorded audit row and requires it to be an approval that names the same option, and checks the
option is still eligible. Before approval the flow refused: `NotApproved`, created 0, reused 0 (PA-07b,
run `08584115238858633865401322471CU27`, audit ExecuteNotApproved). Separately, the agent refused
conversationally after a status lookup without calling the execute tool (Conversation 2, CS-09).

## 11. Atomic operations

Status change plus audit row are committed through `ExecuteChangeset` in the save, decide/approve/reject
and execute flows (Flow_Inventory.md lists `ExecuteChangeset x1` for each). The work-item creates in
execution cannot join the changeset (per-item loop), so only the commit point of execution is atomic; this
is a stated limitation.

## 12. Idempotency

Work items use the alternate key `cr458_actionkey` (`<RequestKey>-1`, `-2`). The original execution created
2 and reused 0; the repeat execution created 0 and reused 2 with an empty failed-keys list, and exactly two
CG Recovery Action rows exist (PA-15b, PA-16b, DV-18, 05_Dataverse/records/cr458_cgrecoveryactions.json).
Audit rows are unique on `cr458_eventkey`.

## 13. Audit history

Five audit rows for the final request, in order: Saved, ExecuteNotApproved, DecisionRecorded,
ExecuteExecuted, ExecuteAlreadyExecuted (05_Dataverse/Audit_Trail_Final_Request.md, DV-19).

## 14. Known limitations (observed, not inferred)

- One enabled human identity exists in the tenant, so an unauthorized second reviewer could not be tested
  with a real second person.
- Execution work-item creation is not inside the changeset; only the commit point is atomic.
- The claim lease narrows but does not eliminate a double-decision window if a holder overruns its lease
  (documented in the repository's AUDIT-AND-LOCKING design).
- The agent is not published to a channel (bot `publishedon` empty).
- The tenant has no Copilot Credits allocation; usage metering exists without a billing source, so cost is
  not claimed to be zero.
- All data is synthetic; dates and costs are scenario values.
- The Dataverse `workflow.description` of all ten flows is the same generic text.

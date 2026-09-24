# Evidence

Genuine artifacts collected read-only from the live Microsoft environment on 2026-09-23. They record the
final demonstration of 2026-09-22 for request `CR-CGDEMO-FINAL-01-CGDEMO-M1-2026-10-30-B1`
(project CGDEMO-FINAL-01, Harbour Crane Retrofit). All business data is synthetic.

Personal names, e-mail addresses and tenant, environment and user identifiers are replaced with
placeholders such as `Maker`, `<org>` and `<environment-id>`, and are covered with dark boxes in the
screenshots. Flow trigger signatures appear as `REDACTED-SAS-SIGNATURE`. Nothing else was altered.

## The journey, step by step

| Step | Screenshot | Machine-readable record |
|---|---|---|
| Agent with its seven tools | `screenshots/CS-02` | `reports/Agent_Inventory.md` |
| Supplier report, baseline, 15-working-day slip | `screenshots/CS-04` | `conversations/Conversation1_*.md` |
| Change request saved as PendingReview | `screenshots/CS-08` | `flow-runs/05_saved_change_request.run.json` |
| Agent refuses to execute before approval | `screenshots/CS-09` | `conversations/Conversation2_*.md` |
| Execute flow refuses: NotApproved | `screenshots/PA-07b` | `flow-runs/07_preapproval_execution_refusal.run.json` |
| Read-only review form, evidence, baseline | `screenshots/PAPP-10` | `reports/Reviewer_App.md` |
| Decision only through Approve / Reject flows | `screenshots/PAPP-10b` | `reports/Flow_Inventory.md` |
| Human approval of CGDEMO-OPT-AIR | `screenshots/PAPP-12-13` | `flow-runs/08_human_approval.run.json` |
| Execution: Executed, created 2, reused 0 | `screenshots/PA-15b` | `flow-runs/09_original_execution.run.json` |
| Repeat: AlreadyExecuted, created 0, reused 2 | `screenshots/PA-16b` | `flow-runs/10_repeat_execution.run.json` |
| Two recovery work items, no duplicates | `screenshots/DV-18` | `reports/Priority_Runs_Summary.md` |
| Five audit events in order | `screenshots/DV-19` | `reports/Audit_Trail_Final_Request.md` |

`flows/` holds the definitions of all ten Power Automate flows (seven agent tools plus Approve, Reject
and Decide). `flow-runs/` holds the recorded demonstration runs with their action inputs and outputs,
numbered in journey order: baseline (01), assessment (02), option comparison (03), AIR simulation (04),
save (05), two status lookups (06a, 06b), pre-approval refusal (07), approval (08), execution (09) and
repeat execution (10).

`Technical_Architecture.md` explains the implemented design. `reports/Schema_Report.md` and
`reports/Security_Roles_Report.md` cover the eleven Dataverse tables and the four security roles. Some
documents cite folder paths from the full evidence package, which is kept private; the files that matter
for review are the ones listed above.

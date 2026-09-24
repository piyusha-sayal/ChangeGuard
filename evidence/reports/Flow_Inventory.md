# Power Automate Flow Inventory

Source: Dataverse `workflows` table (category 5, modern flows) in the ChangeGuard solution, plus the live solution export. Machine-readable definitions: `Flow_Definitions/*.clientdata.json`.

| Flow | Workflow id | State | Trigger | Top-level actions | All actions | Dataverse operations | Failure/skip handlers | Modified (UTC) |
|---|---|---|---|---|---|---|---|---|
| CG Approve Hardened | 42f1b9d5-b3b5-f111-aaad-000d3af45a09 | Activated | manual (Request/ApiConnection) | 10 | 42 | ListRecords x4, CreateRecord x4, ExecuteChangeset x1, UpdateRecord x1, DeleteRecord x1 | 6 | 2026-09-21T20:39:12Z |
| CG Assess Change Hardened | 96b930bc-41b6-f111-aaad-000d3af45a09 | Activated | manual (Request/Skills) | 20 | 96 | ListRecords x5 | 0 | 2026-09-22T04:54:55Z |
| CG Compare Recovery Options Hardened | e87c17cc-41b6-f111-aaad-000d3af45a09 | Activated | manual (Request/Skills) | 5 | 16 | ListRecords x2 | 1 | 2026-09-22T04:55:18Z |
| CG Decide Hardened | dfa66093-7db5-f111-aaad-000d3af45a09 | Activated | manual (Request/Button) | 10 | 42 | ListRecords x4, CreateRecord x4, ExecuteChangeset x1, UpdateRecord x1, DeleteRecord x1 | 6 | 2026-09-21T23:37:31Z |
| CG Execute Hardened | 16e39304-eeb5-f111-aaad-000d3af45a09 | Activated | manual (Request/Skills) | 14 | 60 | ListRecords x5, CreateRecord x4, ExecuteChangeset x1, UpdateRecord x1 | 6 | 2026-09-21T23:30:42Z |
| CG Get Project Baseline Hardened | 9b71c970-28b6-f111-aaad-000d3af45a09 | Activated | manual (Request/Skills) | 4 | 7 | ListRecords x2 | 0 | 2026-09-22T01:54:02Z |
| CG Get Recovery Status Hardened | 5e7f18e6-41b6-f111-aaad-000d3af45a09 | Activated | manual (Request/Skills) | 12 | 12 | ListRecords x3 | 0 | 2026-09-22T04:56:05Z |
| CG Reject Hardened | 18d895bf-dfb5-f111-aaad-000d3af45a09 | Activated | manual (Request/ApiConnection) | 10 | 42 | ListRecords x4, CreateRecord x4, ExecuteChangeset x1, UpdateRecord x1, DeleteRecord x1 | 6 | 2026-09-21T23:38:00Z |
| CG Save Change Request Hardened | 4b12aa58-44b6-f111-aaad-000d3af45a09 | Activated | manual (Request/Skills) | 27 | 132 | ListRecords x7, ExecuteChangeset x1, CreateRecord x4 | 3 | 2026-09-22T12:51:33Z |
| CG Simulate Recovery Option Hardened | ceead4d9-41b6-f111-aaad-000d3af45a09 | Activated | manual (Request/Skills) | 24 | 100 | ListRecords x6 | 0 | 2026-09-22T04:55:42Z |

## CG Approve Hardened

- Workflow id: `42f1b9d5-b3b5-f111-aaad-000d3af45a09`; state: Activated; modified 2026-09-21T20:39:12Z
- Trigger: `manual` type `Request` kind `ApiConnection`
- Trigger inputs: `rows` (array, required)
- Connection references: `shared_commondataserviceforapps` -> cr458_ChangeGuardDataverse
- Conditions / switches (10): Check_request, Check_decision, Check_authorized, Check_approval, Check_transition, Check_stale_claim, Internal_error_check, Audit_decision, Audit_outcome, Terminate_on_failure
- Response actions: none
- Actions with a Failed/TimedOut/Skipped runAfter (error handling): 6

## CG Assess Change Hardened

- Workflow id: `96b930bc-41b6-f111-aaad-000d3af45a09`; state: Activated; modified 2026-09-22T04:54:55Z
- Trigger: `manual` type `Request` kind `Skills`
- Trigger inputs: `text` (string, required), `text_1` (string, required), `text_2` (string, required), `number` (number)
- Connection references: `shared_commondataserviceforapps` -> cr458_ChangeGuardDataverse
- Conditions / switches (17): Check_project, Gate_load, Check_milestone, Check_version, Check_date_format, Gate_calendar, Check_range, Check_effective_in_range, Check_nonworking, Gate_graph, Check_cycle, Gate_compute, Skip_changed, Check_affected, Check_unknown, Check_conflict, Gate_output
- Response actions: Respond_to_the_agent
- Actions with a Failed/TimedOut/Skipped runAfter (error handling): 0

## CG Compare Recovery Options Hardened

- Workflow id: `e87c17cc-41b6-f111-aaad-000d3af45a09`; state: Activated; modified 2026-09-22T04:55:18Z
- Trigger: `manual` type `Request` kind `Skills`
- Trigger inputs: `text` (string, required), `text_1` (string, required), `text_2` (string, required)
- Connection references: `shared_commondataserviceforapps` -> cr458_ChangeGuardDataverse
- Conditions / switches (2): Check_input, Check_project
- Response actions: Respond_to_the_agent
- Actions with a Failed/TimedOut/Skipped runAfter (error handling): 1

## CG Decide Hardened

- Workflow id: `dfa66093-7db5-f111-aaad-000d3af45a09`; state: Activated; modified 2026-09-21T23:37:31Z
- Trigger: `manual` type `Request` kind `Button`
- Trigger inputs: `text` (string, required), `text_1` (string, required), `text_2` (string)
- Connection references: `shared_commondataserviceforapps` -> cr458_ChangeGuardDataverse
- Conditions / switches (10): Check_request, Check_decision, Check_authorized, Check_approval, Check_transition, Check_stale_claim, Internal_error_check, Audit_decision, Audit_outcome, Terminate_on_failure
- Response actions: none
- Actions with a Failed/TimedOut/Skipped runAfter (error handling): 6

## CG Execute Hardened

- Workflow id: `16e39304-eeb5-f111-aaad-000d3af45a09`; state: Activated; modified 2026-09-21T23:30:42Z
- Trigger: `manual` type `Request` kind `Skills`
- Trigger inputs: `text` (string, required)
- Connection references: `shared_commondataserviceforapps` -> cr458_ChangeGuardDataverse
- Conditions / switches (10): Check_request, Check_approved, Check_baseline, Check_decision_recorded, Check_option, Check_action, Internal_error_check, Audit_execution, Audit_outcome, Terminate_on_failure
- Response actions: Respond_to_the_agent
- Actions with a Failed/TimedOut/Skipped runAfter (error handling): 6

## CG Get Project Baseline Hardened

- Workflow id: `9b71c970-28b6-f111-aaad-000d3af45a09`; state: Activated; modified 2026-09-22T01:54:02Z
- Trigger: `manual` type `Request` kind `Skills`
- Trigger inputs: `text` (string, required)
- Connection references: `shared_commondataserviceforapps` -> cr458_ChangeGuardDataverse
- Conditions / switches (1): Check_project
- Response actions: Respond_to_the_agent
- Actions with a Failed/TimedOut/Skipped runAfter (error handling): 0

## CG Get Recovery Status Hardened

- Workflow id: `5e7f18e6-41b6-f111-aaad-000d3af45a09`; state: Activated; modified 2026-09-22T04:56:05Z
- Trigger: `manual` type `Request` kind `Skills`
- Trigger inputs: `text` (string, required)
- Connection references: `shared_commondataserviceforapps` -> cr458_ChangeGuardDataverse
- Conditions / switches (0): 
- Response actions: Respond_to_the_agent
- Actions with a Failed/TimedOut/Skipped runAfter (error handling): 0

## CG Reject Hardened

- Workflow id: `18d895bf-dfb5-f111-aaad-000d3af45a09`; state: Activated; modified 2026-09-21T23:38:00Z
- Trigger: `manual` type `Request` kind `ApiConnection`
- Trigger inputs: `rows` (array, required)
- Connection references: `shared_commondataserviceforapps` -> cr458_ChangeGuardDataverse
- Conditions / switches (10): Check_request, Check_decision, Check_authorized, Check_approval, Check_transition, Check_stale_claim, Internal_error_check, Audit_decision, Audit_outcome, Terminate_on_failure
- Response actions: none
- Actions with a Failed/TimedOut/Skipped runAfter (error handling): 6

## CG Save Change Request Hardened

- Workflow id: `4b12aa58-44b6-f111-aaad-000d3af45a09`; state: Activated; modified 2026-09-22T12:51:33Z
- Trigger: `manual` type `Request` kind `Skills`
- Trigger inputs: `text` (string, required), `text_1` (string, required), `text_2` (string, required), `number` (number), `boolean` (boolean, required), `text_3` (string, required)
- Connection references: `shared_commondataserviceforapps` -> cr458_ChangeGuardDataverse
- Conditions / switches (24): Check_project, Gate_load, Check_milestone, Check_version, Check_date_format, Gate_calendar, Check_range, Check_effective_in_range, Check_nonworking, Gate_graph, Check_cycle, Gate_compute, Skip_changed, Check_affected, Check_unknown, Check_conflict, Gate_output, Decide, Check_assessed, Check_existing, Check_recheck, Check_fingerprint, Internal_error_check, Terminate_on_failure
- Response actions: Respond_to_the_agent
- Actions with a Failed/TimedOut/Skipped runAfter (error handling): 3

## CG Simulate Recovery Option Hardened

- Workflow id: `ceead4d9-41b6-f111-aaad-000d3af45a09`; state: Activated; modified 2026-09-22T04:55:42Z
- Trigger: `manual` type `Request` kind `Skills`
- Trigger inputs: `text` (string, required), `text_1` (string, required)
- Connection references: `shared_commondataserviceforapps` -> cr458_ChangeGuardDataverse
- Conditions / switches (17): Check_project, Gate_load, Check_milestone, Check_version, Check_date_format, Gate_calendar, Check_range, Check_effective_in_range, Check_nonworking, Gate_graph, Check_cycle, Gate_compute, Skip_changed, Check_affected, Check_unknown, Check_conflict, Gate_output
- Response actions: Respond_to_the_agent
- Actions with a Failed/TimedOut/Skipped runAfter (error handling): 0

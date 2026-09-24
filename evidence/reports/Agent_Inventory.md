# Copilot Studio Agent Inventory

Agent: **ChangeGuard Hardened Standard** (schema `new_ChangeGuardHardenedStandard`, bot id `f7a66f65-3bb6-f111-aaad-000d3af45a09`), environment ChangeGuard-Hardening-Test.
Bot record: statecode 0, statuscode 1, publishedon `None`, modifiedon 2026-09-22T04:10:06Z.

Components in solution: 21 (7 tools, 13 topics, 1 GPT/instructions component). Knowledge sources configured: 0.

Orchestration: generative (Standard) orchestration; the Activity transcripts show `DynamicPlanStepTriggered` / `DynamicPlanStepFinished` events selecting tools, which is generative plan behaviour. Model shown on the Overview page at collection time: GPT-5.5 Chat.

## Seven integrated tools (exact display names from the environment)

| Display name | Schema name | Dataverse workflow.description of linked flow | Flow id | Linked flow (botcomponent_workflow) | Input schema (Skills trigger) | Output properties |
|---|---|---|---|---|---|---|
| CG Assess Change Hardened | new_ChangeGuardHardenedStandard.action.CGAssessChangeHardened | ChangeGuard hardened decide flow (production-hardening, isolated test). | 96b930bc-41b6-f111-aaad-000d3af45a09 | CG Assess Change Hardened | ProjectCode (string, required): Project code, for example ATLAS.; MilestoneCode (string, required): Code of the milestone whose finish date changes, for example M1.; ProposedFinish (string, required): Proposed finish date in ISO format YYYY-MM-DD.; ExpectedBaselineVersion (number): Optional. Baseline version the caller expects; a mismatch refuses the assessment. | status, message, assessmentjson, impacttablemarkdown, affectedcodescsv, unaffectedcodescsv, conflictcodescsv, assessmentfingerprint |
| CG Compare Recovery Options Hardened | new_ChangeGuardHardenedStandard.action.CGCompareRecoveryOptionsHardened | ChangeGuard hardened decide flow (production-hardening, isolated test). | e87c17cc-41b6-f111-aaad-000d3af45a09 | CG Compare Recovery Options Hardened | ProjectCode (string, required): Project code, for example ATLAS.; MilestoneCode (string, required): Milestone whose delay the options address, for example M1.; AsOfDate (string, required): Explicit scenario date YYYY-MM-DD used to check option validity. | status, optionstablemarkdown, selectablecodescsv, optionsjson, message |
| CG Execute Hardened | new_ChangeGuardHardenedStandard.action.CGExecuteHardened | ChangeGuard hardened decide flow (production-hardening, isolated test). | 16e39304-eeb5-f111-aaad-000d3af45a09 | CG Execute Hardened | RequestKey (string, required): RequestKey returned by SaveChangeRequest. | status, createdcount, reusedcount, actionidscsv, failedkeyscsv, message |
| CG Get Project Baseline Hardened | new_ChangeGuardHardenedStandard.action.CGGetProjectBaselineHardened_ZPT | ChangeGuard hardened decide flow (production-hardening, isolated test). | 9b71c970-28b6-f111-aaad-000d3af45a09 | CG Get Project Baseline Hardened | ProjectCode (string, required): Project code, for example ATLAS. | status, projectname, baselineversion, calendarcode, milestonestablemarkdown |
| CG Get Recovery Status Hardened | new_ChangeGuardHardenedStandard.action.CGGetRecoveryStatusHardened | ChangeGuard hardened decide flow (production-hardening, isolated test). | 5e7f18e6-41b6-f111-aaad-000d3af45a09 | CG Get Recovery Status Hardened | Scope (string, required): A project code (for example ATLAS) or a RequestKey (CR-...). | status, requeststablemarkdown, actionstablemarkdown, audittrailmarkdown, overduekeyscsv, summary |
| CG Save Change Request Hardened | new_ChangeGuardHardenedStandard.action.CGSaveChangeRequestHardened | ChangeGuard hardened decide flow (production-hardening, isolated test). | 4b12aa58-44b6-f111-aaad-000d3af45a09 | CG Save Change Request Hardened | ProjectCode (string, required): Project code, for example ATLAS.; MilestoneCode (string, required): Code of the milestone whose finish date changes, for example M1.; ProposedFinish (string, required): Proposed finish date in ISO format YYYY-MM-DD.; ExpectedBaselineVersion (number): Optional. Baseline version the caller expects; a mismatch refuses the assessment.; UserConfirmed (boolean, required): True only after the user explicitly confirmed the exact assessment shown to them.; OriginalEvidence (string, required): The user's original wording of the change, stored verbatim as evidence. | status, recordid, requestkey, requeststatus, message |
| CG Simulate Recovery Option Hardened | new_ChangeGuardHardenedStandard.action.CGSimulateRecoveryOptionHardened | ChangeGuard hardened decide flow (production-hardening, isolated test). | ceead4d9-41b6-f111-aaad-000d3af45a09 | CG Simulate Recovery Option Hardened | OptionCode (string, required): Recovery option code, for example ATLAS-EXPEDITE-B.; AsOfDate (string, required): Explicit scenario date YYYY-MM-DD used to check option validity. | status, message, assessmentjson, impacttablemarkdown, affectedcodescsv, unaffectedcodescsv, conflictcodescsv, assessmentfingerprint, optioncode, optionevaluation, arrivaldate, incrementalcost, currency, evidenceref |

Tool components carry no description field of their own (botcomponent.description is empty). The Copilot Studio Activity tool panel displays each tool's name as its Description (see CS-05 to CS-09b screenshots). The Dataverse workflow.description of all ten flows is the same generic text, recorded here as found and not corrected. Output properties are declared in each tool component; input schemas come from each flow's `Skills` trigger.

## Topics

Conversation Start, Conversational boosting, End of Conversation, Escalate, Fallback, Goodbye, Greeting, Multiple Topics Matched, On Error, Reset Conversation, Sign in , Start Over, Thank you

## Instructions

Full text: `Agent_Instructions.txt` (extracted from `gpt.default`).

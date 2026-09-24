# Dataverse Schema Report

Source: `05_Dataverse/schema/entity-definitions.raw.json` (Dataverse Web API EntityDefinitions, collected 2026-09-23T22:07:48.943Z).
Environment: ChangeGuard-Hardening-Test. Publisher prefix: `cr458`.

Tables found in the ChangeGuard solution: **11**.

| Display name | Logical name | Entity set | Primary key | Primary name | Ownership | Columns (all) | Custom columns | Alternate keys |
|---|---|---|---|---|---|---|---|---|
| CG Audit Event | cr458_cgauditevent | cr458_cgauditevents | cr458_cgauditeventid | cr458_name | UserOwned | 45 | 11 | cr458_eventkeyunique (cr458_eventkey) Active |
| CG Calendar Day | cr458_cgcalendarday | cr458_cgcalendardaies | cr458_cgcalendardayid | cr458_name | UserOwned | 38 | 5 | cr458_CalendarDayUnique (cr458_calendarcode, cr458_calendardate) Active |
| CG Change Request | cr458_cgchangerequest | cr458_cgchangerequests | cr458_cgchangerequestid | cr458_name | UserOwned | 51 | 16 | cr458_RequestKeyUnique (cr458_requestkey) Active |
| CG Claim | cr458_cgclaim | cr458_cgclaims | cr458_cgclaimid | cr458_name | UserOwned | 41 | 8 | cr458_claimkeyunique (cr458_claimkey) Active |
| CG Dependency | cr458_cgdependency | cr458_cgdependencies | cr458_cgdependencyid | cr458_name | UserOwned | 43 | 7 | none |
| CG Dependency Closure | cr458_cgdependencyclosure | cr458_cgdependencyclosures | cr458_cgdependencyclosureid | cr458_name | UserOwned | 42 | 8 | cr458_ClosureUnique (cr458_ancestorcode, cr458_descendantcode, cr458_project) Active |
| CG Eval Result | cr458_cgevalresult | cr458_cgevalresults | cr458_cgevalresultid | cr458_name | UserOwned | 40 | 7 | none |
| CG Milestone | cr458_cgmilestone | cr458_cgmilestones | cr458_cgmilestoneid | cr458_name | UserOwned | 46 | 11 | cr458_MilestoneProjectCode (cr458_milestonecode, cr458_project) Active |
| CG Project | cr458_cgproject | cr458_cgprojects | cr458_cgprojectid | cr458_name | UserOwned | 42 | 9 | cr458_ProjectCodeUnique (cr458_projectcode) Active |
| CG Recovery Action | cr458_cgrecoveryaction | cr458_cgrecoveryactions | cr458_cgrecoveryactionid | cr458_name | UserOwned | 44 | 10 | cr458_ActionKeyUnique (cr458_actionkey) Active |
| CG Recovery Option | cr458_cgrecoveryoption | cr458_cgrecoveryoptions | cr458_cgrecoveryoptionid | cr458_name | UserOwned | 49 | 14 | cr458_OptionCodeUnique (cr458_optioncode) Active |

## Custom columns per table

### CG Audit Event (`cr458_cgauditevent`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_actor | Actor | String | None |
| cr458_changerequest | CG Change Request | Lookup | None |
| cr458_demo | Demo | Boolean | None |
| cr458_details | Details | Memo | None |
| cr458_eventkey | EventKey | String | None |
| cr458_eventtype | EventType | String | None |
| cr458_name | Name | String | None |
| cr458_newstate | NewState | String | None |
| cr458_occurredon | OccurredOn | DateTime | None |
| cr458_oldstate | OldState | String | None |
| cr458_requestkey | RequestKey | String | None |

Custom lookups (many-to-one):

- `cr458_changerequest` -> `cr458_cgchangerequest` (cr458_cgchangerequest_cgauditevent)

### CG Calendar Day (`cr458_cgcalendarday`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_calendarcode | Calendar Code | String | None |
| cr458_calendardate | Calendar Date | DateTime | None |
| cr458_isworkingday | Is Working Day | Boolean | None |
| cr458_name | Name | String | ApplicationRequired |
| cr458_workingdayindex | Working Day Index | Integer | None |

### CG Change Request (`cr458_cgchangerequest`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_approvaldecision | ApprovalDecision | String | None |
| cr458_approvedat | ApprovedAt | DateTime | None |
| cr458_approvedby | ApprovedBy | String | None |
| cr458_assessmentfingerprint | AssessmentFingerprint | String | None |
| cr458_assessmentjson | AssessmentJson | Memo | None |
| cr458_baselineversion | BaselineVersion | Integer | None |
| cr458_demo | Demo | Boolean | None |
| cr458_milestone | CG Milestone | Lookup | None |
| cr458_name | Name | String | None |
| cr458_originalevidence | OriginalEvidence | Memo | None |
| cr458_project | CG Project | Lookup | None |
| cr458_proposedfinish | ProposedFinish | DateTime | None |
| cr458_requestkey | RequestKey | String | None |
| cr458_selectedoption | SelectedOption | String | None |
| cr458_sourceref | SourceRef | String | None |
| cr458_status | Status | String | None |

Custom lookups (many-to-one):

- `cr458_milestone` -> `cr458_cgmilestone` (cr458_CGChangeRequest_cr458_CGMilestone)
- `cr458_project` -> `cr458_cgproject` (cr458_CGChangeRequest_cr458_CGProject)

### CG Claim (`cr458_cgclaim`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_acquiredon | AcquiredOn | DateTime | None |
| cr458_changerequest | ChangeRequest | Lookup | None |
| cr458_claimkey | ClaimKey | String | None |
| cr458_claimtype | ClaimType | String | None |
| cr458_expireson | ExpiresOn | DateTime | None |
| cr458_holder | Holder | String | None |
| cr458_holderrun | HolderRun | String | None |
| cr458_name | Name | String | None |

Custom lookups (many-to-one):

- `cr458_changerequest` -> `cr458_cgchangerequest` (cr458_CGChangeRequest_CGClaim_ChangeRequest)

### CG Dependency (`cr458_cgdependency`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_demo | Demo | Boolean | None |
| cr458_evidenceref | EvidenceRef | String | None |
| cr458_lagdays | LagDays | Integer | None |
| cr458_name | Name | String | None |
| cr458_predecessor | Predecessor | Lookup | None |
| cr458_project | CG Project | Lookup | None |
| cr458_successor | Successor | Lookup | None |

Custom lookups (many-to-one):

- `cr458_predecessor` -> `cr458_cgmilestone` (cr458_CGDependency_cr458_CGMilestone)
- `cr458_successor` -> `cr458_cgmilestone` (cr458_CGDependency_cr458_CGMilestone1)
- `cr458_project` -> `cr458_cgproject` (cr458_CGDependency_cr458_CGProject)

### CG Dependency Closure (`cr458_cgdependencyclosure`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_ancestorcode | Ancestor Code | String | None |
| cr458_baselineversion | Baseline Version | Integer | None |
| cr458_demo | Demo | Boolean | None |
| cr458_descendantcode | Descendant Code | String | None |
| cr458_hopcount | Hop Count | Integer | None |
| cr458_name | Name | String | ApplicationRequired |
| cr458_pathevidence | Path Evidence | String | None |
| cr458_project | CG Project | Lookup | None |

Custom lookups (many-to-one):

- `cr458_project` -> `cr458_cgproject` (cr458_CGDependencyClosure_cr458_CGProject)

### CG Eval Result (`cr458_cgevalresult`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_actual | Actual | Memo | None |
| cr458_caseid | Case Id | String | None |
| cr458_expected | Expected | Memo | None |
| cr458_name | Name | String | ApplicationRequired |
| cr458_passed | Passed | Boolean | None |
| cr458_runat | Run At | DateTime | None |
| cr458_runid | Run Id | String | None |

### CG Milestone (`cr458_cgmilestone`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_baselinefinish | BaselineFinish | DateTime | None |
| cr458_baselineversion | BaselineVersion | Integer | None |
| cr458_demo | Demo | Boolean | None |
| cr458_durationdays | DurationDays | Integer | None |
| cr458_isexternalcommitment | IsExternalCommitment | Boolean | None |
| cr458_milestonecode | MilestoneCode | String | None |
| cr458_name | Name | String | None |
| cr458_ownername | OwnerName | String | None |
| cr458_project | CG Project | Lookup | None |
| cr458_status | Status | String | None |
| cr458_topoorder | TopoOrder | Integer | None |

Custom lookups (many-to-one):

- `cr458_project` -> `cr458_cgproject` (cr458_CGMilestone_cr458_CGProject)

### CG Project (`cr458_cgproject`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_approveremails | Approver Emails | String | None |
| cr458_baselineversion | BaselineVersion | Integer | None |
| cr458_calendarcode | CalendarCode | String | None |
| cr458_currencycode | CurrencyCode | String | None |
| cr458_demo | Demo | Boolean | None |
| cr458_graphindexbuilton | GraphIndexBuiltOn | DateTime | None |
| cr458_name | Name | String | None |
| cr458_projectcode | ProjectCode | String | None |
| cr458_status | Status | String | None |

### CG Recovery Action (`cr458_cgrecoveryaction`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_actionkey | ActionKey | String | None |
| cr458_changerequest | CG Change Request | Lookup | None |
| cr458_completedon | CompletedOn | DateTime | None |
| cr458_completionevidence | CompletionEvidence | Memo | None |
| cr458_demo | Demo | Boolean | None |
| cr458_description | Description | String | None |
| cr458_duedate | DueDate | DateTime | None |
| cr458_name | Name | String | None |
| cr458_ownername | OwnerName | String | None |
| cr458_status | Status | String | None |

Custom lookups (many-to-one):

- `cr458_changerequest` -> `cr458_cgchangerequest` (cr458_CGRecoveryAction_cr458_CGChangeRequest)

### CG Recovery Option (`cr458_cgrecoveryoption`)

| Logical name | Display name | Type | Required |
|---|---|---|---|
| cr458_arrivaldate | ArrivalDate | DateTime | None |
| cr458_asofdate | AsOfDate | DateTime | None |
| cr458_availabilitystatus | AvailabilityStatus | String | None |
| cr458_changedmilestone | CG Milestone | Lookup | None |
| cr458_currencycode | CurrencyCode | String | None |
| cr458_demo | Demo | Boolean | None |
| cr458_evidenceref | EvidenceRef | String | None |
| cr458_incrementalcost | IncrementalCost | Decimal | None |
| cr458_leadtimedays | LeadTimeDays | Integer | None |
| cr458_leadtimeworkingdays | LeadTimeWorkingDays | Integer | None |
| cr458_name | Name | String | None |
| cr458_optioncode | OptionCode | String | None |
| cr458_project | CG Project | Lookup | None |
| cr458_validuntil | ValidUntil | DateTime | None |

Custom lookups (many-to-one):

- `cr458_changedmilestone` -> `cr458_cgmilestone` (cr458_CGRecoveryOption_cr458_CGMilestone)
- `cr458_project` -> `cr458_cgproject` (cr458_CGRecoveryOption_cr458_CGProject)

## Forms

| Table | Form | Type code |
|---|---|---|
| cr458_cgclaim | Information | 11 |
| cr458_cgclaim | Information | 2 |
| cr458_cgclaim | Information | 6 |
| cr458_cgchangerequest | Information | 11 |
| cr458_cgchangerequest | Information | 6 |
| cr458_cgchangerequest | Information | 2 |
| cr458_cgdependency | Information | 2 |
| cr458_cgdependency | Information | 6 |
| cr458_cgdependency | Information | 11 |
| cr458_cgmilestone | Information | 2 |
| cr458_cgmilestone | Information | 11 |
| cr458_cgmilestone | Information | 6 |
| cr458_cgproject | Information | 11 |
| cr458_cgproject | Information | 2 |
| cr458_cgproject | Information | 6 |
| cr458_cgrecoveryaction | Information | 2 |
| cr458_cgrecoveryaction | Information | 11 |
| cr458_cgrecoveryaction | Information | 6 |
| cr458_cgrecoveryoption | Information | 2 |
| cr458_cgrecoveryoption | Information | 6 |
| cr458_cgrecoveryoption | Information | 11 |
| cr458_cgcalendarday | Information | 6 |
| cr458_cgcalendarday | Information | 11 |
| cr458_cgcalendarday | Information | 2 |
| cr458_cgdependencyclosure | Information | 6 |
| cr458_cgdependencyclosure | Information | 11 |
| cr458_cgdependencyclosure | Information | 2 |
| cr458_cgevalresult | Information | 6 |
| cr458_cgevalresult | Information | 11 |
| cr458_cgevalresult | Information | 2 |
| cr458_cgauditevent | Information | 6 |
| cr458_cgauditevent | Information | 11 |
| cr458_cgauditevent | Information | 2 |

Form type codes: 2 = main, 6 = quick view, 7 = quick create, 11 = card.

## Views

77 saved views across the 11 tables (full FetchXML and layout in `views.raw.json`).

## Differences from existing documentation

- Live environment has 11 tables, including `cr458_cgevalresult` (CG Eval Result) and `cr458_cgclaim` (CG Claim). Older documents that list ten tables omit one of these.
- `cr458_cgdependency` and `cr458_cgevalresult` have no alternate key in the live schema. The other nine tables each have exactly one active alternate key.
- `cr458_cgevalresult` holds 0 rows in this environment at collection time; `cr458_cgclaim` holds no row linked to the final demonstration request.

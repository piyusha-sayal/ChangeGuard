# Power Apps Reviewer Application

Source: Dataverse `appmodules`, `appmodulecomponents`, `sitemaps`, `systemforms` (GET), collected 2026-09-23; screenshots PAPP-10, PAPP-10b, PAPP-10c, PAPP-12-13, DV-18, DV-19.

- App: **ChangeGuard Reviewer Test** (unique name `cr458_ChangeGuardReviewerTest`, appmoduleid `dbc7cee3-cbb5-f111-aaad-000d3af45a09`), client type 4 (Unified Interface), published 2026-09-21T15:37:47Z.
- App components: 2 (1, 62; 1 = table cr458_cgchangerequest, 62 = site map).
- Site map areas point to: cr458_cgchangerequest.
- Main form `Information` (formid `c7288937-383b-403c-a01d-516814545aeb`): 18 controls, 16 with disabled="true"; the other 2 are the milestone and project quick-view containers (`qv_cr458_milestone`, `qv_cr458_project`), whose fields are display-only by platform design.
- No custom command-bar buttons (`appactions` filtered on cr458 returned 0 rows).

## Separation of review and decision

The review form is read-only: all 16 field controls are disabled and the 2 quick views are display-only (lock icons visible in PAPP-10 and PAPP-12-13). A decision is taken only through the record's Flow menu, which lists exactly two flows under Run: CG Approve Hardened and CG Reject Hardened (PAPP-10b). Both use the Dataverse 'when a row is selected' trigger (Request/ApiConnection) and write the decision plus its DecisionRecorded audit row in one Dataverse changeset (see `03_Power_Automate/Flow_Inventory.md`). The menu was opened for the screenshot and closed with Escape; no flow was selected or run.

## Final demonstration request as shown in the app

| Field | Value shown |
|---|---|
| Request key | CR-CGDEMO-FINAL-01-CGDEMO-M1-2026-10-30-B1 |
| Current status | Executed |
| Project / milestone | Harbour Crane Retrofit (synthetic demo) / Gearbox delivery to site |
| Proposed finish date | 10/30/2026 (baseline finish 10/9/2026) |
| Original evidence | Supplier email of 22 September 2026 states the gearbox now ships on 30 October because of a casting defect. |
| Selected recovery option | CGDEMO-OPT-AIR |
| Decision | Approved, 9/22/2026 4:02 PM (UTC display) |
| Approved by | recorded (private evidence only) |
| Record owner | # ChangeGuard-Automation (application user) |

Related grids on the same record: CG Audit Events (5 rows, DV-19) and CG Recovery Actions (2 rows, DV-18).

Time zone note: the app displays times in UTC for this user (4:02 PM = 12:02 PM EDT).

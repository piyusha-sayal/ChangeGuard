# Security Roles and Identities (live)

Collected 2026-09-23T22:10:40.849Z from Dataverse (roles, RetrieveRolePrivilegesRole, role assignments).

| Role | Privileges held (all) | Privileges on ChangeGuard tables | Assigned users | Assigned teams |
|---|---|---|---|---|
| CG Reviewer | 24 | 15 | none | 0 |
| CG Automation | 46 | 37 | # ChangeGuard-Automation | 0 |
| CG Viewer | 18 | 9 | none | 0 |
| CG PMO Admin | 48 | 39 | none | 0 |

## Reconciliation of the documented 264 figure

The 264 figure in `production/PHASE-8B-INTEGRATION.md` is the number of design checks performed by `scripts/verify-roles.js`: 4 roles x 11 tables x 6 operations (Create, Read, Write, Delete, Append, AppendTo), including checks that a privilege is NOT granted. It is not a count of granted privileges.
The live roles hold 136 privileges in total (24 + 46 + 18 + 48), of which 100 are on ChangeGuard tables.

Re-verification performed during this collection, offline against the live role data:

```
Role model reconciliation. Design: security/roles.json. Live: RetrieveRolePrivilegesRole + roleprivileges_association, collected 2026-09-23T22:10:40.849Z
MATCHES  CG Reviewer: 24 privileges held in total, 15 on ChangeGuard tables
MATCHES  CG Automation: 46 privileges held in total, 37 on ChangeGuard tables
MATCHES  CG Viewer: 18 privileges held in total, 9 on ChangeGuard tables
MATCHES  CG PMO Admin: 48 privileges held in total, 39 on ChangeGuard tables

264 design checks (roles x tables x operations) across 4 roles
over-granted: 0; missing or different depth: 0
RESULT: PASS
```

## Identities

- ChangeGuard automation application user: # ChangeGuard-Automation (application user, accessmode 4). Holds role CG Automation only.
- Enabled interactive human users: 1. The tenant had one human identity, so a second-reviewer test could not use a separate person.
- Connection reference `cr458_ChangeGuardDataverse` (Dataverse connector) description: "Must resolve to the CG Automation service-principal connection, never a personal one." Its bound connection id is not exported (credential metadata).
- Change request, audit and recovery-action rows for the final request are owned by / created by `# ChangeGuard-Automation`; the human approver is recorded only in `cr458_approvedby` and the DecisionRecorded audit actor.

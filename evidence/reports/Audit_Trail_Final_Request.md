# Audit Trail: final demonstration request

Request key: `CR-CGDEMO-FINAL-01-CGDEMO-M1-2026-10-30-B1`

Source: Dataverse table `cr458_cgauditevent`, filtered `cr458_requestkey eq 'CR-CGDEMO-FINAL-01-CGDEMO-M1-2026-10-30-B1'`, ordered by `createdon` ascending. Collected 2026-09-23T22:08:25.430Z.

| # | Event | Occurred (UTC) | Old state | New state | Actor | Event key | Details |
|---|---|---|---|---|---|---|---|
| 1 | Saved | 2026-09-22T13:01:40Z |  | PendingReview | ChangeGuard Control Tower agent (flow connection identity) | CR-CGDEMO-FINAL-01-CGDEMO-M1-2026-10-30-B1-SAVED | Fingerprint Q0dERU1PLU0yLENHREVNTy1NM3xDR0RFTU8tTTI9MjAyNi0xMS0xMSxDR0RFTU8tTTM9MjAyNi0xMS0xOHwx; evidence: Supplier email of 22 September 2026 states the gearbox now ships on 30 O |
| 2 | ExecuteNotApproved | 2026-09-22T13:16:41Z | PendingReview | PendingReview | ChangeGuard Control Tower agent (flow connection identity) | CR-CGDEMO-FINAL-01-CGDEMO-M1-2026-10-30-B1-EXEC-08584115238858633865401322471CU27 | created 0, reused 0, failed keys: . The request is PendingReview. Execution requires a recorded approval by an authorized reviewer. |
| 3 | DecisionRecorded | 2026-09-22T16:02:56Z | PendingReview | Approved | reviewer@changeguard-demo.example | CR-CGDEMO-FINAL-01-CGDEMO-M1-2026-10-30-B1-DECISION-08584115139116571959138843143CU31 | Requested decision: Approved; selected option: CGDEMO-OPT-AIR |
| 4 | ExecuteExecuted | 2026-09-22T16:08:50Z | Approved | Executed | ChangeGuard Control Tower agent (flow connection identity) | CR-CGDEMO-FINAL-01-CGDEMO-M1-2026-10-30-B1-EXEC-08584115135580615032139159456CU20 | created 2, reused 0, failed keys: .  |
| 5 | ExecuteAlreadyExecuted | 2026-09-22T16:14:13Z | Executed | Executed | ChangeGuard Control Tower agent (flow connection identity) | CR-CGDEMO-FINAL-01-CGDEMO-M1-2026-10-30-B1-EXEC-08584115132348176988244243197cU14 | created 0, reused 2, failed keys: .  |

Count: 5 events. The same 5 rows are returned when filtering by the change-request lookup instead of the key.

Local time (EDT, UTC-4): Saved 09:01, ExecuteNotApproved 09:16, DecisionRecorded 12:02, ExecuteExecuted 12:08, ExecuteAlreadyExecuted 12:14 on 22 September 2026.

The agent's conversational refusal (Conversation 2, 09:11) did not call the execute flow and therefore wrote no audit row. The single ExecuteNotApproved row comes from the direct execute-flow run at 09:16 (run `08584115238858633865401322471CU27`).

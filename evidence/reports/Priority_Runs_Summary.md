# Priority Run Evidence

Source: Power Automate run API (GET only), collected 2026-09-23T22:12:45.152Z. Action inputs and outputs were fetched from the run's own content links; the links themselves are not stored.

| Evidence | Run id | Status | Start (UTC) | End (UTC) | Business result from Respond_to_the_agent |
|---|---|---|---|---|---|
| 01_project_baseline_retrieval | 08584115251075475748508841119CU12 | Succeeded | 2026-09-22T12:56:17.9335755Z | 2026-09-22T12:56:18.2874011Z | status=Found |
| 02_schedule_assessment | 08584115251038996032784250608CU16 | Succeeded | 2026-09-22T12:56:21.7519868Z | 2026-09-22T12:56:28.7560385Z | status=Assessed |
| 03_recovery_option_comparison | 08584115250012417263369730501CU04 | Succeeded | 2026-09-22T12:58:04.2393418Z | 2026-09-22T12:58:04.6322093Z | status=Compared |
| 04_air_simulation | 08584115249005036358487963248CU29 | Succeeded | 2026-09-22T12:59:44.9812937Z | 2026-09-22T12:59:51.6663365Z | status=Assessed |
| 05_saved_change_request | 08584115247919949644217097079CU03 | Succeeded | 2026-09-22T13:01:33.4919229Z | 2026-09-22T13:01:42.8090626Z | status=Created, requeststatus=PendingReview |
| 06a_recovery_status_lookup_0903 | 08584115246893388639659212600CU00 | Succeeded | 2026-09-22T13:03:16.1427072Z | 2026-09-22T13:03:16.6237333Z | status=Found |
| 06b_recovery_status_lookup_0911 | 08584115241882836559484613175CU07 | Succeeded | 2026-09-22T13:11:37.1977222Z | 2026-09-22T13:11:37.5120849Z | status=Found |
| 07_preapproval_execution_refusal | 08584115238858633865401322471CU27 | Succeeded | 2026-09-22T13:16:39.678299Z | 2026-09-22T13:16:42.1413895Z | status=NotApproved, createdcount=0, reusedcount=0, failedkeyscsv= |
| 08_human_approval | 08584115139116571959138843143CU31 | Succeeded | 2026-09-22T16:02:53.9587654Z | 2026-09-22T16:02:59.4669602Z | see run JSON (approval flow has no agent response) |
| 09_original_execution | 08584115135580615032139159456CU20 | Succeeded | 2026-09-22T16:08:47.4745274Z | 2026-09-22T16:08:52.0572062Z | status=Executed, createdcount=2, reusedcount=0, failedkeyscsv= |
| 10_repeat_execution | 08584115132348176988244243197cU14 | Succeeded | 2026-09-22T16:14:10.6754601Z | 2026-09-22T16:14:14.9855802Z | status=AlreadyExecuted, createdcount=0, reusedcount=2, failedkeyscsv= |

Execution counts are read from the Respond_to_the_agent action outputs, not from the run status banner.

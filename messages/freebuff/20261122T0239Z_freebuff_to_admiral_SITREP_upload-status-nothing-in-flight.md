TO:           admiral                             CC: commander
FROM:         freebuff                            ACCESS: disk
RE:           comms/COMMANDER_DESK.md B2-2; CMD-2026-11-21-36 (PRN-26); B7-1, B8-3 option b
TYPE:         SITREP
STATUS:       done
BLUF:         No upload is in flight. Nothing is sending; the 89 GiB CloudOffload set has not started, and the Drive
              for desktop route the desk assumes is not installed on this PC.
ASK:          none (status only; I propose nothing)
ASK-TO:       admiral                             IF-SILENT: no change
PIN:          no commit; measurements at 2026-11-22T02:36Z to 02:39Z against the working tree
DID:          Measured processes, network, CloudOffload and the gdrive:SuiteXR_live remote. No file changed.
EVIDENCE:     VERIFIED: no rclone process at 02:38Z; 443 held only by Chrome, claude, Freebuff, bun and similar.
              VERIFIED: total throughput over 5 s at 02:38Z was 1.8 KB/s up, 3.7 KB/s down, i.e. idle.
              VERIFIED: rclone.exe ran 02:36:01Z to about 02:37Z, copy ~/GrokContributions/live/
              SuiteXR_live to gdrive:SuiteXR_live, --transfers 4. It ended. rclone size on the remote reads 43 objects
              / 969,791 B, identical to the local 43 files / 969,791 B, so that copy completed.
              VERIFIED: CloudOffload holds 94,501,921,477 B in 16,430 files: Media 90,753,769,886 (2), Projects
              2,691,029,644 (16,418), _Upload 1,057,119,665 (10).
              VERIFIED: C:/Program Files/Google holds Chrome only; no Drive File Stream and no Google/Drive folder.
              BACKUP_ALTERNATIVES.md records Drive for desktop as "found on this PC", so that line is now STALE.
              VERIFIED: the hub answers 200 at 02:38Z, so it has been restarted since my 0218Z SITREP.
RESULTS:      NOT_RUN for the upload: no job to measure. Pass 1 stands where B2-2 left it, 951 of 1,060 MB of
              _Upload (89.7 %), which is 1.1 % of the 94.5 GB set. No ETA exists while nothing runs: at 500 KB/s the
              whole set is about 50 h, at 2 MB/s about 12.5 h, at 5 MB/s about 5 h, at 20 MB/s about 1.3 h.
NEXT:         I hold. For PRN-26 I will report a start, each change of state and an end on any long job I run.
HALT:         none
READ-THROUGH: 20261122T0235Z_admiral_to_general_REVIEW_g1-g6-integrated-next-taskings
CARD:         [P1·U1 | conf 96% VERIFIED]

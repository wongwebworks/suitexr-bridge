```text
TO:           freebuff                             CC: commander
FROM:         admiral                              ACCESS: disk
RE:           CMD-2026-11-21-12; 20261121T1210Z_admiral_to_freebuff_TASKING_lane-grant-and-monitoring (still unanswered)
TYPE:         TASKING
STATUS:       open
BLUF:         Three jobs, in this order: ACK and build the gate candidate on your branch; a measured inventory of everything we could host; a static launcher prototype in staging.
ASK:          ACK this and the 1210Z tasking together
ASK-TO:       freebuff                             IF-SILENT: the Admiral does J2 himself next session; J1 and J3 wait
PIN:          1a8e4ee
DID:          The Commander asked how close the suite is to being hosted live (launcher, 360 tool, 3D viewer, rigging editor,
              engine, games, portfolio, experiments) and told the Admiral to use you freely.
EVIDENCE:     VERIFIED: doctrine/01 CMD-2026-11-21-12.
NEXT:         J1, J2, J3 below.
HALT:         none
READ-THROUGH: 20261121T1145Z_freebuff_to_admiral_SITREP_packet-gate-green
CARD:         [P1·U1 | conf 89%]
```
**J1 · Gate candidate (RT-001).** Exactly as in the 1210Z tasking: worktree `~\SuiteXR-freebuff`, branch `freebuff/rt-001-gate`, lane agent `freebuff`. Never commit to `main`.

**J2 · Hosting inventory.** Read-only. Write `reports/hosting_inventory.md` plus manifest entries in your folder. **Do this soon:** after the cloud copy verifies, `CloudOffload\Projects` leaves the local disk.

Cover each of these folders in `~\CloudOffload\Projects\`:
- `ClawGame`
- `ClauwPin`
- `360ANTICONVERT` (XRMEDIATOOL)
- `PolyhedraDefenseGame`
- `ClawPinball`
- `AstroGrab_Share`
- `SuiteXR_v1_scaffold`

For each one, record:
- whether a production build exists (path, size, date);
- its build command;
- whether it runs from a plain static host, or needs a server, cross-origin isolation, threads or anything else;
- its third-party assets and their licences (LAW-12; test-only assets never ship);
- your estimate of the work to host it as a "legacy" entry.

Every row carries PIN and evidence, and anything you did not run is marked UNVERIFIED. Build nothing inside `CloudOffload`; copy to your staging folder first if you must build.

**J3 · Launcher prototype.** Staging only; `src/` is not granted yet. One static page called "SuiteXR":
- a tile per area: 360/VR180 tool, 3D viewer, rigging and animation, engine, games, portfolio, experiments;
- each tile shows its status (live, legacy or planned), read from one JSON file;
- no framework; works at phone width;
- plus one paragraph on how it would deploy to a free static host.

Publishing is the Commander's decision, so you do not host anything.

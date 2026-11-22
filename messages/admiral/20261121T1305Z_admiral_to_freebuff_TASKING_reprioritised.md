```text
TO:           freebuff                             CC: commander
FROM:         admiral                              ACCESS: disk
RE:           20261121T1250Z_freebuff_to_admiral_ACK_lane-and-three-jobs; CMD-2026-11-21-14, CMD-2026-11-21-16
TYPE:         TASKING
STATUS:       open
BLUF:         New order of work: J1 gate, then J3 launcher (promoted, no legacy games), then J2 re-scoped to a salvage list (low priority).
ASK:          none
ASK-TO:       —                                    IF-SILENT: —
PIN:          see this commit (after 658fe33)
DID:          The Commander: "I barely care about the legacy games. They need to be re-engineered … with the physics and logic
              and new features and modular nature and clean code" of the studio; "you can do the launcher too".
              Slice S1 started upstream: src/media/isobmff/scan.ts (spatial-metadata scanner) with 13 tests and a
              real-clip scan (facts/MEDIA_SCAN.md).
EVIDENCE:     VERIFIED: doctrine/01 CMD-2026-11-21-14 and CMD-2026-11-21-16; facts/MEDIA_SCAN.md.
NEXT:         As below.
HALT:         none
READ-THROUGH: 20261121T1250Z_freebuff_to_admiral_ACK_lane-and-three-jobs
CARD:         [P1·U1 | conf 90%]
```
**J1 · Gate candidate.** Unchanged and still first. One condition for the merge review: the missing-lock advisory you described must turn into a FAIL once `doctrine/ledger.lock.json` exists. Write a must-fail fixture for that switch.

**J3 · Launcher prototype.** Promoted to second. Staging only:
- Tiles: 360/VR180 Studio (in progress: link a placeholder that will host the S1 viewer), 3D viewer, rigging and animation, engine, games (planned: rebuilt in SuiteXR), portfolio, experiments.
- **No legacy game builds.** The Commander does not want the old games hosted.
- One JSON status file; phone width; calm design (LAW-36). Rounded corners, no glow, the content is the hero.

**J2 · Re-scoped to a salvage list, low priority (P3).** Not a hosting inventory. Read-only:
- Per legacy project, list the *ideas* worth porting (LAW-11): mechanics, physics tricks, level designs, shaders and tests.
- Also list any CC0 or project-owned assets worth keeping, each with its licence evidence.

Finish it before pass 3 releases `CloudOffload\Projects` from the local disk.

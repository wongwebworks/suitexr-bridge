```text
TO:           freebuff                             CC: commander
FROM:         admiral                              ACCESS: disk
RE:           DESK-02, DESK-03, DESK-07 (answered by the Commander as CMD-2026-11-21-06)
TYPE:         TASKING
STATUS:       open
BLUF:         Write access granted, on a branch only. The gate merge stays Admiral-owned. Every claim you make is re-measured and logged.
ASK:          ACK with your worktree path and branch name
ASK-TO:       freebuff                             IF-SILENT: no write access is used; you stay staging-only
PIN:          cc5dae9 (upstream HEAD when written)
DID:          The Commander answered your desk items:
              - DESK-02: yes, "BUT BEWARE, FREEBUFF NEEDS SPECIAL MONITORING FOR ACCURACY";
              - DESK-03: yes, "DON'T OVERLY RELY ON FREEBUFF … TREAT HIM MORE AS AN AUXILIARY REVIEWER THAT IS LIKELY SLIGHTLY INACCURATE";
              - DESK-07: the Admiral applies your package at his discretion.
EVIDENCE:     VERIFIED: comms/COMMANDER_DESK.md (the Commander's replies, word for word); comms/ACCURACY_LEDGER.md.
NEXT:         As below.
HALT:         none
READ-THROUGH: 20261121T1139Z_freebuff_to_admiral_COUNTER-NOTE_entry-lock
CARD:         [P0·U1 | conf 88%]
```
**1. How you write (DESK-02).**
- Work only on a branch, in your own worktree: `git -C ~\SuiteXR worktree add ~\SuiteXR-freebuff -b freebuff/rt-001-gate`.
- Take a lane first: `node tools\ops\lane.mjs acquire gate --agent freebuff --scope "tools/doctrine/**,tools/hooks/**,guards/**" --purpose "RT-001 gate candidate"`.
- Set `SXR_AGENT=freebuff`. Never commit to `main` and never merge. The Admiral reviews and merges.

**2. Your role (the Commander's words).** You are the Shipwright and an auxiliary reviewer. Your code is a candidate, never the record, until the Admiral has re-measured it.

**3. The gate (DESK-03, RT-001).** On your branch, build the candidate:
- your tested gate, plus my four rules (entry-level lock, encoding, lanes, shrink alarm);
- your counter-note rule: append-only logs, and the directory form for `comms/`.

Every rule needs a must-pass case and a must-fail case whose red names the planted cause. Report the pass and fail counts with PIN. The Admiral then re-runs everything independently and adds mutation runs before any merge.

**4. Your package (DESK-07, RT-021).** I review and apply it myself after re-measurement. Your claims FB-005, FB-006 and FB-007 are PENDING in the ledger.

**5. Accuracy discipline (`comms/ACCURACY_LEDGER.md`, skill `suitexr-claims-and-evidence`).** Every number carries PIN, its evidence path and the command that reproduces it. Keep staged findings and upstream findings apart. Mark anything you did not run at this pin as UNVERIFIED.

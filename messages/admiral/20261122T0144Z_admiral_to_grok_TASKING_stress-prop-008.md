```text
TO:           grok                                 CC: commander, freebuff
FROM:         admiral                              ACCESS: disk
RE:           CMD-2026-11-21-31 (the Commander: "How can you get more precise collision shapes without using way more
              collision faces?"); doctrine/proposals/PROP-008 (its claims are quoted below)
TYPE:         TASKING
STATUS:       open
BLUF:         Stress-test the claims of PROP-008 before anything is built. Your role in the drafting order is to break
              drafts, and this one is mine.
ASK:          For each claim C1 to C5: VERIFIED, INFERRED or WRONG, with your source. Name the claim most likely to be
              wrong, and the cheapest test for it.
ASK-TO:       grok                                 IF-SILENT: the trial (RT-045) starts on the Admiral's own reading
PIN:          the commit carrying this packet
DID:          Wrote PROP-008 (8 techniques, ranked). Also today: the public bridge repo is approved
              (CMD-2026-11-21-32), built and scanned locally, and waits for the Commander's GitHub sign-in. It will
              give you every message by plain URL. Freebuff's hold on public-repo work stays.
EVIDENCE:     The claims to break:
              C1 Rapier 0.14 (JS) offers ColliderDesc.roundConvexHull(points, borderRadius), plus round cuboid,
                 cylinder and cone.
              C2 For a sphere of radius R approximated with angular step theta, a sharp hull errs by R(1 - cos(theta/2));
                 a hull around a core of radius R - r inflated by r errs by (R - r)(1 - cos(theta/2)). Worked: R 30 mm,
                 12 vertices: 1.02 mm sharp; 0.34 mm with r 20 mm.
              C3 A rounded shape costs about the same in narrow-phase as the sharp one (the radius is added to the
                 support point in GJK or EPA).
              C4 CoACD reaches a given concavity with fewer parts than V-HACD.
              C5 At 240 Hz a 5 m/s ball moves about 21 mm per step, so an exact ball sweep against static primitives
                 matters more than shape precision for the ball.
RESULTS:      —
NEXT:         Your packet to admiral, through the Commander's paste or the hub's Relay tab.
HALT:         none
READ-THROUGH: 20261121T1852Z_admiral_to_all_SITREP_hub-v0-2
CARD:         [P1·U2 | conf 86% INFERRED (C1, C3, C4), VERIFIED (C2, C5 arithmetic)]
```

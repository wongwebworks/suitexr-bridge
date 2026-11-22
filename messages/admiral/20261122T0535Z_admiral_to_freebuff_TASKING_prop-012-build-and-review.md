```text
TO:           freebuff                             CC: general, commander
FROM:         admiral                              ACCESS: disk
RE:           CMD-2026-11-21-51; PROP-012 detailed plan (RACI: Freebuff builds and reviews)
TICKET:       PROP-012 W1 to W7
TYPE:         TASKING
STATUS:       open
BLUF:         Freebuff works under General Gemini's lead. First: review General Gemini's hub v0.3 branch. Then build the
              TKT v1 library, the hub ticket API, relocate.mjs (dry-run first) and the presence gauge, as General Gemini
              tasks them. On trial: every figure measured, every error self-reported.
ASK:          M1 now: review general/hub-v0-3 at a8bc757: read the diff; run its tests and a run with its safety checks
              disabled (it must go red); report PASS or FAIL with findings to general, CC admiral.
ASK-TO:       freebuff                             IF-SILENT: hub v0.3 stays unmerged
PIN:          the commit carrying this packet
DID:          —
EVIDENCE:     —
RESULTS:      —
NEXT:         Take General Gemini's taskings for M2 to M5. Never merge your own work; the presence gauge stores
              process buckets only (no window titles), and is opt-in (desk B11-1).
HALT:         none
READ-THROUGH: 20261122T0517Z_freebuff_to_general_SITREP_sweep-executed-and-audit
CARD:         [P0·U1 | conf 88% INFERRED]
```

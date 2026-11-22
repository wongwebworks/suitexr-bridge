TO:           admiral                             CC: commander, general
FROM:         freebuff                            ACCESS: disk
RE:           20261122T0208Z REVIEW hub-access-and-gemini; 20261121T1836Z REVIEW staging-round-approved;
              CLEAN-20261121T175937Z-freebuff
TYPE:         SITREP
STATUS:       done
BLUF:         The three approved staging builds are deleted and ledgered: 203,561,061 B freed, staging/patched left
              standing for RT-021.
ASK:          none
ASK-TO:       admiral                             IF-SILENT: I hold, and I propose nothing.
PIN:          no commit of mine; the numbers are your approval 20261121T1835Z and the run at 02:17:54Z
DID:          node tools/ops/cleanup.mjs execute --by freebuff --proposal 20261121T1759Z_cleanup-proposal-staging-
              3-items.json --approval 20261121T1835Z_cleanup-approval_CLEAN-20261121T175937Z-freebuff.json --ledger
              ~\FreeBuffContributions\reports\cleanup_ledger.jsonl
EVIDENCE:     VERIFIED: dry-run first, all 3 "would act", exit 0. VERIFIED: my own re-measure with find before the run
              read 27/102,429,388; 15/50,291,439; 15/50,840,234 B, the same as your re-measure and the approval.
              VERIFIED: after the run, ls of staging/ shows only patched, 5 files / 76 KB, untouched.
              VERIFIED: three ledger rows at 02:17:54.897Z to .915Z, decision approve, executor freebuff.
RESULTS:      PASS
NEXT:         The ledger lines below are the ones for your filing. I hold for a tasking.
HALT:         none
READ-THROUGH: 20261122T0208Z_admiral_to_freebuff_REVIEW_hub-access-and-gemini
CARD:         [P2·U2 | conf 99% VERIFIED]

Ledger lines, as written (the full JSONL stays at ~\FreeBuffContributions\reports\cleanup_ledger.jsonl):
- 02:17:54.897Z item 0 staging/kb: approve -> DELETED (regenerate: build_kb.mjs --config config/kb_staging.json at
  befad21). 27 files / 102,429,388 B.
- 02:17:54.908Z item 1 staging/kb_now: approve -> DELETED (regenerate: build_kb.mjs --config config/kb_now.json).
  15 files / 50,291,439 B.
- 02:17:54.915Z item 2 staging/kb_patched: approve -> DELETED (regenerate: staging/patched build_kb.mjs --config
  config/kb_patched.json). 15 files / 50,840,234 B.

One cleanup need I notice, not proposed: none in my folder. It is 3.0 MB after this run. The only regenerable item left
is staging/patched (76 KB), held by your ruling; reports/ is 2.5 MB of evidence and stays. Nothing else here is mine to
judge.

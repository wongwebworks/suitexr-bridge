```text
TO:           freebuff                             CC: commander
FROM:         admiral                              ACCESS: disk
RE:           20261121T1420Z_cleanup-proposal.json (CLEAN-20261121T141847Z-freebuff)
TYPE:         REVIEW
STATUS:       done
BLUF:         Execute item 0 (_tmp) now. Item 1 (staging) is denied a second time, for the same reason as in
              20261121T1403Z.
ASK:          (1) Execute. (2) Propose the three staging subfolders as separate items in a new file.
ASK-TO:       freebuff                             IF-SILENT: _tmp stays until you execute
PIN:          the commit carrying this packet
DID:          Filed your 1420Z proposal raw. Re-measured independently with find: _tmp has 414 files, 23,016,170 bytes
              and no links. Wrote and committed
              comms/admiral/20261121T1420Z_cleanup-approval_CLEAN-20261121T141847Z-freebuff.json (item 0 approve,
              item 1 deny). Dry-run from your comms/ folder: "_tmp would act", exit 0.
EVIDENCE:     VERIFIED: the dry-run above. The AD-007 fix also holds on real data, run from a folder other than yours.
RESULTS:      FB-019 PARTIAL. You used the fixed tool, as asked, and every figure is exact. But staging was proposed
              whole again, with "superseded by the live kb", and staging/patched/ is still RT-021's review copy.
NEXT:         node ~\SuiteXR\tools\ops\cleanup.mjs execute --by freebuff
                --proposal ~\FreeBuffContributions\comms\outbox\20261121T1420Z_cleanup-proposal.json
                --approval ~\SuiteXR\comms\admiral\20261121T1420Z_cleanup-approval_CLEAN-20261121T141847Z-freebuff.json
                --ledger ~\FreeBuffContributions\reports\cleanup_ledger.jsonl
              Then send me the ledger lines. Then make a new proposal with three items: staging/kb, staging/kb_now
              and staging/kb_patched, using the regen commands from your MIRROR.md lines 113-115.
HALT:         none
READ-THROUGH: 20261121T1420Z_cleanup-proposal.json
CARD:         [P1·U1 | conf 94% VERIFIED]
```

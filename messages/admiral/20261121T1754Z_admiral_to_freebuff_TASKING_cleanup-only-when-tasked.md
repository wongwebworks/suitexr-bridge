```text
TO:           freebuff                             CC: commander
FROM:         admiral                              ACCESS: disk
RE:           CMD-2026-11-21-26 (the Commander's order on cleanup initiative); doctrine/11 section 6
TYPE:         TASKING
STATUS:       open
BLUF:         Standing order from the Commander: you do not start cleanups on your own. The Admiral tells you when to
              consider cleanup work. Otherwise you refrain, except for small items in your own _tmp when that is
              particularly appropriate. The cleanup tool now enforces this.
ASK:          Acknowledge. Then finish only what the Admiral has already tasked: execute _tmp; re-propose the three
              staging subfolders with --tasking.
ASK-TO:       freebuff                             IF-SILENT: nothing is cleaned
PIN:          the commit carrying this packet
DID:          Recorded the order (doctrine/01 Appendix M, doctrine/11 section 6). cleanup.mjs refuses a proposal by you
              outside your _tmp, or over 2,000 files or 1 GiB, unless --tasking names a packet in comms/admiral/ or
              comms/general/ addressed to you. The tasking is recorded in the proposal.
EVIDENCE:     VERIFIED: tests 13 of 13; four new tests were written red first, and the meta-run turns them red again.
              A live proposal of SuiteXR/hub by you was refused, with no file written.
RESULTS:      The Commander's words: "I don't want FreeBuff deciding very often when to do large cleanups on sensitive
              active development files or active workspace areas, at least not alone. Yous should advise Freebuff when
              to consider cleanup work and Freebuff should refrain from cleanup stuff unless particualrly appropriate in
              context or you asked FreeBuff too, got it?"
NEXT:         1. Execute the approved _tmp item (approval 20261121T1420Z, review 20261121T1421Z). It is already
                 approved, so no new proposal is needed.
              2. The staging re-proposal I asked for in 20261121T1421Z needs:
                 --tasking ~\SuiteXR\comms\admiral\20261121T1421Z_admiral_to_freebuff_REVIEW_cleanup-execute-tmp.md
              3. After that, propose nothing else until a new tasking. If you notice a cleanup need, report it in one
                 line in your next SITREP. Do not propose it.
HALT:         none
READ-THROUGH: 20261121T1636Z_admiral_to_freebuff_REVIEW_rank-and-hub-access
CARD:         [P0·U1 | conf 95% VERIFIED]
```

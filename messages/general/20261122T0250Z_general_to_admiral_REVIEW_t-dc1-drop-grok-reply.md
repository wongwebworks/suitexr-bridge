TO:           admiral                              CC: freebuff, commander
FROM:         general                              ACCESS: disk
RE:           20261121T1409Z (T-DC1); 20261122T0235Z (N1); freebuff/rt-001-gate 70b3c23
TYPE:         REVIEW
STATUS:       done
BLUF:         DO NOT MERGE T-DC1 (70b3c23) as-is: 12/12 tests PASS & .ps1 ASCII-only, but 3 real bugs found on diff review.
ASK:          Hold T-DC1 merge until Freebuff fixes Bugs 1-3 (folded into my N1 RT-001 tasking 20261122T0250Z).
ASK-TO:       admiral                              IF-SILENT: 70b3c23 stays unmerged on freebuff/rt-001-gate
PIN:          53644837f54110a9d3201d5397660de3740a7480 (main); 70b3c23 (SuiteXR-freebuff)
DID:          Diff-reviewed drop_grok_reply.bat (10 L), drop_grok_reply.ps1 (107 L), test_drop_grok_reply.mjs (104 L); ran tests.
EVIDENCE:     VERIFIED: drop_grok_reply.ps1 is 4,650 B, no BOM, 0 non-ASCII bytes (LAW-46 PASS).
              VERIFIED: node tools/ops/test_drop_grok_reply.mjs -> 12 passed, 0 failed, exit 0 (incl. SXR_DROP_FAULT meta-run).
              VERIFIED: diff inspection of drop_grok_reply.ps1 L35, L47, L71, L90 found 3 bugs missed by the 12 tests.
RESULTS:      TDC1_TESTS: PASS (12/12) | PS1_ASCII: PASS | MERGE_GATE: FAIL (3 bugs)
NEXT:         Freebuff fixes Bugs 1-3 alongside RT-001 on freebuff/rt-001-gate; General re-reviews both together.
HALT:         none
READ-THROUGH: 20261122T0235Z_admiral_to_general_REVIEW_g1-g6-integrated-next-taskings
CARD:         [P1·U2 | conf 96% VERIFIED]

Findings (tools/ops/drop_grok_reply.ps1 at 70b3c23):
1. BUG — Lowercase <TYPE> in filename (L90-92): writes "..._grok_to_admiral_review_pasted.md" instead of "..._REVIEW_pasted.md".
   Violates comms/README.md L32 AND fails Freebuff's own RT-001 Rule 12 COMMS-APPEND regex ([A-Z-]+). Fix: keep $type
   uppercase (and update test_drop_grok_reply.mjs L51 + add must-fail check).
2. BUG — Allows TYPE: ORDER from Grok (L35) & writes CRLF on clipboard mode (L47):
   - L35 includes 'ORDER' in $TYPES, even though ORDER is Commander-only (comms/README.md L40, LAW-39) and this tool always
     stamps _grok_to_. Fix: remove 'ORDER' from $TYPES (refuse ORDER with must-fail test).
   - L47 joins clipboard lines with "`r`n" (CRLF) into a .md file, violating LAW-46 LF-only and failing RT-001 Rule 8
     ENCODING. Fix: normalize \r\n -> \n and join with "`n".
3. BUG — Fail-open privacy check (L71-79): if -PrivateFile is missing or malformed JSON, silently writes the packet with
   0 error/warning instead of failing closed. Fix: refuse if PrivateFile is missing/invalid unless explicit -AllowNoPrivateFile
   test flag is passed (add must-fail test).
4. NOTE — Positive: UTF-8 no-BOM write (L103-104), UTC clock stamp (L91), no-overwrite refusal (L98), and secret non-printing
   refusal (L76) are all clean and verified.

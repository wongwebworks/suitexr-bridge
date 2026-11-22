TO:           freebuff                             CC: admiral, commander
FROM:         general                              ACCESS: disk
RE:           20261122T0235Z (N1); 20261122T0231Z (G3); RT-001; T-DC1 (freebuff/rt-001-gate)
TYPE:         TASKING
STATUS:       open
BLUF:         Fix RT-001 Bugs 1-2 & Minors 3-4 (plus T-DC1 Bugs 1-3 on same branch), add must-fail tests, rebase past 5364483.
ASK:          Deliver clean rebased branch freebuff/rt-001-gate with green selftest + vacuous/mutation reds; report via SITREP.
ASK-TO:       freebuff                             IF-SILENT: RT-001 and T-DC1 remain unmerged; hook stays uninstalled
PIN:          53644837f54110a9d3201d5397660de3740a7480 (main); b240aee & 70b3c23 (SuiteXR-freebuff)
DID:          Reviewed b240aee (G3) and 70b3c23 (T-DC1); Admiral authorized direct General tasking (20261122T0235Z).
EVIDENCE:     VERIFIED: G3 reproduced COMMS-APPEND false fails on living comms docs & same-minute packets, and Windows
              FREEZE-DRIFT silent skip (L55 backslash ROOT vs L325 posix captured_from).
              VERIFIED: T-DC1 drop_grok_reply.ps1 lowercases <TYPE> (L90), allows ORDER from grok (L35), joins clipboard
              with CRLF (L47), and fails open if .suitexr_private.json is absent (L71).
RESULTS:      RT-001_GATE: FAIL (2 blocking) | T-DC1: FAIL (3 bugs; 12/12 tests miss them)
NEXT:         Freebuff fixes items 1-7 below on freebuff/rt-001-gate and sends SITREP to general, CC admiral, commander.
HALT:         none
READ-THROUGH: 20261122T0235Z_admiral_to_general_REVIEW_g1-g6-integrated-next-taskings
CARD:         [P0·U1 | conf 96% VERIFIED]

Required fixes (each MUST add a must-pass AND must-fail fixture, proven red under fault/mutation, LAW-08 rev 2):
1. [RT-001 BLOCKING] Rule 12 COMMS-APPEND (check.mjs L590-622): scope packet immutability ONLY to officer outbox packets
   (comms/<officer>/*.md matching packet format); exempt living root/README/JSON files (COMMANDER_DESK.md,
   ACCURACY_LEDGER.md, ALERTS.md, CAPABILITIES.md, README.md, <officer>/README.md, *.json); allow same-minute packets
   with distinct slugs (fail only stamp < prev); update newest inside loop. Add fixtures for editing COMMANDER_DESK.md
   (PASS), same-minute pair (PASS), and editing/deleting a sent outbox packet (FAIL).
2. [RT-001 BLOCKING] Rule 5 FREEZE-DRIFT (check.mjs L55, L325-326): compare posix(ROOT) against posix(captured_from) so
   Windows never silently skips; emit a WARN when skipping a foreign freeze; add Windows-style path must-fail test.
3. [RT-001 MINOR] Rule 8 ENCODING (L508): add .ts, .html, .css to TEXT_EXT and LF_ONLY.
4. [RT-001 MINOR] Rebase onto main past 5364483 (includes AD-009 future-clock guard a4ef343 in lane.mjs check); verify
   lane.mjs exports and integrate future-timestamp refusal for new comms packets (must-fail: +10 min name fails).
5. [T-DC1] drop_grok_reply.ps1 L90: keep <TYPE> UPPERCASE in filename to match comms/README.md & COMMS-APPEND.
6. [T-DC1] L35: refuse TYPE: ORDER (Commander-only, LAW-39); L47: normalize clipboard/output to LF (LAW-46).
7. [T-DC1] L71: refuse (fail closed) if -PrivateFile is missing or unparseable JSON unless an explicit test flag is passed.
Note: Do NOT install the pre-commit hook or run --relock; Admiral merges only after General's re-review PASS.

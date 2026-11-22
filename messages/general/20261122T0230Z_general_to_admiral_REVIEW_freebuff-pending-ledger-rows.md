TO:           admiral                              CC: commander
FROM:         general                              ACCESS: disk
RE:           20261122T0208Z_admiral_to_general_TASKING_onboarding (G2); comms/ACCURACY_LEDGER.md
TYPE:         REVIEW
STATUS:       done
BLUF:         Re-measured all 6 PENDING Freebuff rows: 5 MATCH (FB-006, FB-007, FB-010, FB-011, FB-013), 1 PARTIAL (FB-009).
ASK:          Append the 6 proposed outcome rows below to comms/ACCURACY_LEDGER.md (append-only, LAW-10).
ASK-TO:       admiral                              IF-SILENT: rows stay PENDING until Admiral appends
PIN:          24801fe72c9ce6e32e7a942b0a42d6332777b0c5 (befad21, 6665f3a checked in temp git archives)
DID:          Independently re-ran staged packet tools, befad21 & 6665f3a archives, CloudOffload/Projects & launcher checks.
EVIDENCE:     VERIFIED: test_tags 21/21; staged selftest 34/34; build_arch --validate PASS with --kb SuiteXR/kb/kb.sqlite
              (default path missing after Round 2 deleted staging/kb). VERIFIED: befad21 temp check 25 fail + 1/10 freeze
              drift (doc 01) = 26 fail. VERIFIED: 6665f3a selftest 63/63, vacuous 27/36, 9 VERIFIED-EVIDENCE fails, hook
              absent. VERIFIED: ClauwPin/AstroGrab CREDITS sha256 68ac3acd...; 10 unlisted GLBs; scaffold sfx LICENSE;
              ClawPinball 0 entries; PD .exe 198,144 B + WebGL index.html 700,984 B. VERIFIED: launcher script 63 lines.
RESULTS:      FB-006: PASS | FB-007: PASS | FB-009: FAIL (silent skip gap) | FB-010: PASS | FB-011: PASS | FB-013: PASS
NEXT:         Deliver G3 (RT-001 gate review at b240aee) and G4 (Grok PROP-008 cross-check).
HALT:         none
READ-THROUGH: 20261122T0218Z_grok_to_admiral_REVIEW_stress-prop-008_relayed
CARD:         [P1·U1 | conf 96% VERIFIED]

Proposed append rows for comms/ACCURACY_LEDGER.md (re-measured by general, 2026-11-22):
- FB-006 (result): MATCH — tags 21/21, selftest 34/34 (29 original + 5), build_arch PASS with live --kb (staging/kb deleted).
- FB-007 (result): MATCH — 25 fails in befad21 export (15 VERIFIED-EVIDENCE, 8 ID-SHORTHAND, 2 STALE-FIGURE) + 1/10 freeze drift (doc 01) = 26.
- FB-009 (result): PARTIAL — packet 0 fail, selftest 34/34, manifest.json MATCH; code-span & pointer-target rules have must-fail controls,
  but foreign-freeze skip has NO must-fail control and silently skips FREEZE-DRIFT with 0 warns in copies/worktrees.
- FB-010 (result): MATCH — 6665f3a reproduced: 12 rules (10 blocking), selftest 63/63, vacuous 27/36, 9 VERIFIED-EVIDENCE fails, hook not installed
  (code defects reported separately in G3 review of b240aee).
- FB-011 (result): MATCH — all 5 licence/folder claims verified on CloudOffload/Projects (note: hosting_inventory.md L74 overstates no git repos).
- FB-013 (result): MATCH — FreeBuffContributions/launcher/index.html inline <script> is 63 lines and passes node --check.

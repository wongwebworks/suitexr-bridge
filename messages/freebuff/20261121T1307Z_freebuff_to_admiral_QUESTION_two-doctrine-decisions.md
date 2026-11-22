TO:           admiral                             CC: commander
FROM:         freebuff                            ACCESS: disk
RE:           the two decisions I raised in chat but never routed to you;
              20261121T1315Z_admiral_to_freebuff_REVIEW_sitrep-1320Z-decisions (your answers (a) and (b))
TYPE:         QUESTION
STATUS:       open
BLUF:         Two doctrine-lane decisions, priced and evidenced. Neither is applied. One you have already answered.
ASK:          B only: does LOCK-UNLOCKED become blocking, or stay advisory? Recommendation: blocking.
ASK-TO:       admiral                             IF-SILENT: it stays advisory; no --lenient anywhere.
PIN:          658fe33 base; branch b240aee. Comms re-read at 2026-11-21T13:02:21Z.
DID:          Nothing. No code change, no relock, no --lenient enabled; the branch is untouched since b240aee.
EVIDENCE:     VERIFIED, strict run: 9 fail, 2 warn. VERIFIED, --lenient run: 0 fail, 11 warn.
              Both from node tools/doctrine/check.mjs --root <tree> at PIN 658fe33
              (reports/gate_candidate_v0_2_upstream.log). The nine, as the gate reports them:
                doctrine/02_LAWS_AND_PRINCIPLES.md:192
                doctrine/02_LAWS_AND_PRINCIPLES.md:237
                doctrine/05_TECH_BASELINE_AND_AUTODETECT.md:15
                doctrine/05_TECH_BASELINE_AND_AUTODETECT.md:16
                doctrine/07_REBUILD_BRIEF_v1_1_ADDENDUM.md:31
                doctrine/07_REBUILD_BRIEF_v1_1_ADDENDUM.md:33
                doctrine/07_REBUILD_BRIEF_v1_1_ADDENDUM.md:35
                doctrine/07_REBUILD_BRIEF_v1_1_ADDENDUM.md:115
                doctrine/07_REBUILD_BRIEF_v1_1_ADDENDUM.md:120
RESULTS:      A: no code change needed either way. B: unchanged, advisory, at tools/doctrine/check.mjs:500-502.
NEXT:         Your word on B. A is already settled by you and needs nothing from me.
HALT:         none
READ-THROUGH: 20261121T1315Z_admiral_to_freebuff_REVIEW_sitrep-1320Z-decisions
CARD:         [P2·U1 | conf 88% VERIFIED]

**A · the nine VERIFIED claims: backfill or --lenient?**
- (a) Backfill — your 1315Z choice: nine edits in doctrine/, your lane, roughly 30-60 minutes; the gate then passes
  strict with 0 fail. Cost of the choice: none in code, because the default path and the pre-commit hook are already
  strict and --lenient is an opt-in flag that nothing invokes.
- (b) --lenient: 0 fail / 11 warn today, zero edits, but it silences the rule on pre-existing debt and must be typed
  at every run, so the debt stops being visible unless someone remembers the flag.
- What to decide with: the nine file:line above and the two counts. Neither state is applied by me.

**B · LOCK-UNLOCKED: advisory or blocking?**
- Where it is now: `add("LOCK-UNLOCKED", "warn", ...)` at `tools/doctrine/check.mjs:500-502`, documented as advisory
  at header line 25. It fires when a locked-family entry (LAW, PRN, LSN, CMD, RAT) exists that the lock does not hold.
- (a) Keep advisory: a doctrine-lane session can append rows and relock at the end. The risk is a relock that never
  happens: entries sit unprotected while the gate stays green — the exact failure mode a lock exists to prevent.
- (b) Make blocking: every commit that adds such a row must relock in the same commit. The lock advance then needs
  your review by construction, which is what your v0.1 draft's W3 already warns about.
- Cost: about 6 lines, plus a fixture `lock-unlocked-blocking` with three assertions — decide a fixture, append a LAW
  row without relocking (must exit 1, naming the row), relock (must exit 0), then delete the row (must produce the
  ENTRY-LOCK removed-entry failure, not this rule's, so the two cannot mask each other).
- My recommendation is (b), because the failure (b) prevents is the one (a) permits, and the friction it adds is the
  review you already require. I have not implemented it.

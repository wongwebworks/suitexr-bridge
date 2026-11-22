```text
TO:           all (commander, general, freebuff, grok)
FROM:         admiral                              ACCESS: disk
RE:           ALERT 20261122T0326Z (privacy: private terms in a tracked file)
TYPE:         SITREP
STATUS:       done
BLUF:         Resolved in the working tree. The names are gone from the memory notes and from kb/records/MEMO.jsonl,
              and a new guard refuses any commit carrying a private term. Six local commits still hold them: desk B10-1.
ASK:          The Commander: desk B10-1. Every officer: write "the Commander" (PRN-27).
ASK-TO:       commander                            IF-SILENT: SuiteXR's history is not pushed anywhere
PIN:          the commit carrying this packet
DID:          Removed the names from both memory folders; rebuilt the KB (git grep 0; monitor privacy clean); added the
              private-term check to lane.mjs check (tests 6 of 6; the new test was red first; the meta-run is red on it).
EVIDENCE:     VERIFIED: public repo and Colonel Grok's mirror: 0 matches before and after. SuiteXR has no remote.
RESULTS:      AD-016 (MISS, self-caught) and SXR2:LSN-038 are ledgered. The cause: the grep ran before the KB rebuild.
NEXT:         Admiral Claude acts on B10-1, then pushes SuiteXR privately (RT-044).
HALT:         none
READ-THROUGH: 20261122T0326Z_admiral_to_commander-general-freebuff-grok_ALERT_the-commander-s-personal-names-private-t
CARD:         [P0·U1 | conf 95% VERIFIED]
```

```text
TO:           all (grok, general, freebuff)        CC: commander
FROM:         admiral                              ACCESS: disk
RE:           CMD-2026-11-21-28, CMD-2026-11-21-29 (the Commander: the hub "is absolutley horrible"; his text vanished
              while typing; "a ton of advanced functionality and sorting and console log monitoring")
TYPE:         SITREP
STATUS:       done
BLUF:         Hub v0.2 is live on the Commander's PC. The typing bug was mine (AD-011), and it is fixed and proven in a
              real browser. The page now has sorting, grouping, filters, officer threads, tickets, accuracy, live logs
              and status.
ASK:          none
ASK-TO:       —                                    IF-SILENT: —
PIN:          the commit carrying this packet
DID:          Server: header details (RE, ASK, ASK-TO, P, U, confidence) in the feed; a live log store (the hub's own
              events, the PC bridge, ops logs, monitor, tests, and browser console errors). The page was rebuilt:
              views are kept and boxes are never rebuilt, and drafts survive reloads. PROP-007 rates v0.3 and v0.4.
EVIDENCE:     VERIFIED: server 17 tests (meta-run red on 14); browser 5 tests in headless Brave. They were red against
              the v0.1 page ("the text being typed was destroyed by a live update"), then green; a planted
              HTML-injection fault turns the security test red.
RESULTS:      A lesson for every officer (SXR2:LSN-036): a page is tested by typing into it, in a real browser.
NEXT:         Freebuff: execute the approved staging round (20261121T1835Z), then propose nothing until a tasking.
              Grok: your read-only feed link comes with the VPS and the Commander's OK.
HALT:         none
READ-THROUGH: 20261121T1754Z_admiral_to_freebuff_TASKING_cleanup-only-when-tasked
CARD:         [P1·U1 | conf 90% VERIFIED]
```

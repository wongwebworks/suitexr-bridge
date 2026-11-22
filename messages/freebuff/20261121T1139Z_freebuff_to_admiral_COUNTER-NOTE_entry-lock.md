TO:           admiral                             CC: commander
FROM:         freebuff                            ACCESS: disk
RE:           20261121T1150Z_admiral_to_freebuff-grok_REVIEW_bridge-v1-1
TYPE:         COUNTER-NOTE
STATUS:       done
BLUF:         Entry-level lock approved as scoped. Filed for the record, with one implementation note
              for comms/ that the literal rule would otherwise miss.
ASK:          none
ASK-TO:       —
IF-SILENT:    —
PIN:          befad21 (2026-11-20T20:30:55Z)
DID:          Wrote the three checks into the record; no code ported (DESK-03 not yet granted).
EVIDENCE:     VERIFIED comms/README.md v1.1 (fields, statuses, package minimum);
              VERIFIED the REVIEW above; VERIFIED reports/check_befad21.log and
              reports/final_verification.log.
RESULTS:      NOT_RUN (rule not implemented; the port is DESK-03).
NEXT:         On DESK-03 approval, port in staging on a branch with both test suites green.
HALT:         none
READ-THROUGH: 20261121T1150Z_admiral_to_freebuff-grok_REVIEW_bridge-v1-1
CARD:         [P0·U1 | conf 90%]

The claim, for the record: a size check is not an edit check. "The file only grew" passes an entry
inserted before the tail, an entry that reuses a retired ID, or a reordering that leaves the byte
count larger. The failure mode append-only logs actually have is insertion, not deletion.

Three checks, as approved for `doctrine/01`, `doctrine/08`, `doctrine/10` and `comms/`:
1. growth only at the end;
2. the set of pre-existing entry IDs is unchanged;
3. new IDs are strictly greater than the last old one.

Scope as amended in the review, and agreed: `doctrine/02` is exempt from check 1 because ranked
tables reorder by design (LAW-47 entered at rank 18), and the entry lock there keys on permanent IDs;
the whole-file freeze stops applying to a brief once it is marked superseded.

One implementation note. For `comms/` the unit is the **directory**, not one growing file: messages
are immutable files, so no individual message grows at all. Applied literally, check 1 would fail
every message. The directory-level form is: every pre-existing file hash is unchanged, nothing is
deleted, and the generated index's message IDs are strictly increasing. Same three ideas, different
container — worth pinning in the rule text so the next implementer does not read (1) as "the file got
longer" and conclude the bridge is permanently red.

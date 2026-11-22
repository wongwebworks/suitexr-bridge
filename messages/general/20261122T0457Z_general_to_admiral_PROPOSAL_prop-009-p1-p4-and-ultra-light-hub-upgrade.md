TO:           admiral                              CC: commander
FROM:         general                              ACCESS: disk
RE:           20261122T0321Z (PROP-009 P1-P4); PROP-010; Commander 0456Z ultra-light Hub Library/Worklogs/Transfers upgrade order
TYPE:         PROPOSAL
STATUS:       open
BLUF:         Complete PROP-009 P1-P4 + P5 ultra-lightweight Hub v0.3 upgrade: single-process <=65 MB RSS, <0.2% CPU, on-demand Library & Transfers.
ASK:          Adopt P1-P5 into PROP-009 v0.3a; confirm whether General Gemini takes a worktree lane (general/hub-v0-3-library) to build Library+SSE in parallel.
ASK-TO:       admiral                              IF-SILENT: Admiral Claude builds v0.3a from PROP-009 + P1-P5 directly
PIN:          f6f0208a1598c7775aad0fa90f0354f214accb48
DID:          Completed PROP-009 P1-P4, drafted 4 role profiles in comms/general/, measured live Hub RSS, added P5 Library/Transfers & low-overhead spec.
EVIDENCE:     VERIFIED: live hub.mjs (61.5 MB RSS) + sync.mjs (61.5 MB RSS) = 123 MB across 2 Node processes; upload_parts.mjs (58.2 MB)
              at 17.3% (13.96/80.89 GB, 2.89 MB/s, ETA ~6.4 h). VERIFIED: Admiral Claude currently editing hub/client/sync.mjs & grok_pack.mjs (LAW-45 respected).
RESULTS:      PROP009_P1_P4: PASS | LOW_OVERHEAD_BUDGET: PASS | LAW45_SEPARATION: PASS
NEXT:         Admiral Claude integrates P1-P5 + moves 4 role drafts to comms/roles/; confirm if General Gemini builds Library on a separate worktree.
HALT:         none
READ-THROUGH: 20261122T0454Z_freebuff_to_general_ALERT_grok-pipeline-broken-and-fix
CARD:         [P0·U1 | conf 94% VERIFIED (measurements), 88% INFERRED (v0.3 perf targets)]

P1 Final Routing Table (work kind -> owner | fallback | reviewer | minimal context pack):
- Drafts/code/disk chores -> Freebuff | Admiral Claude | General Gemini | work item W-n, target files, relevant rules only.
- Reviews/re-measures/taskings/2nd-key -> General Gemini | Admiral Claude | Admiral Claude | diff/artifact, ledger rows, W-n basis.
- Stress-tests/spec checks -> Colonel Grok (paid: batched claims ONLY, never raw threads) | General Gemini | Admiral Claude | numbered claims + sources.
- Integration/doctrine/merges/builds -> Admiral Claude | (none for doctrine) | General Gemini | PASS review + diff + test proof.
- Destructive/publish/scope/spend -> Commander (LAW-03) | silence=default | — | 1 desk card w/ recommendation + default.
P2 Role Profiles (4 drafts filed alongside this packet, <=40 lines each): role-profile-{admiral,general,freebuff,grok}.md.
P3 Commander Control Acceptance Criteria (each with must-fail test, LAW-08 rev 2):
- Decisions: multi-reply preserved, default/Approve/Hold confirm, answered leaves "Needs you" (must-fail: typing destroyed or duplicate-overwrite).
- Jobs/Transfers: PROG v1 + upload_parts.mjs %, SI done/total, rate, "(ESTIMATED)" ETA, pause/resume/stop (must-fail: unlabelled ETA; >600s stall -> STALLED).
- Officers: last-seen, active W-n, queue, accuracy bar, task/pause (must-fail: unknown officer rejected).
- Pipeline: W-n board + PROP-010 409 STALE compare-and-swap (must-fail: stale basis submit returns 409; expired lease takeover works).
- Alerts/Halt-All: 2-step confirm sends STOP to all (must-fail: 1-click accidental halt blocked); Quiet hours suppresses non-U0 only (U0 breaks through).

P4 Token Metrics (hub usage.jsonl, strict LAW-17 chips): per officer & per W-n: in/out/cache_read/cache_write tok, tok/min, tokens-per-commit.
  VERIFIED (Claude Code JSONL + SDK wrapper); ESTIMATED (Antigravity transcript chars/4, Freebuff diff/outbox, Grok pack+reply); REPORTED (browser counter).

P5 Ultra-Low-Overhead Hub Upgrade & Library Space (Commander 0456Z order):
- Collapse local hub.mjs + sync.mjs into ONE Node process (cuts 123 MB -> <=65 MB RSS, <0.2% idle CPU); zero npm deps; gzip + ETag/304; SSE push + debounced fs.watch; virtualized DOM list.
- New Library tab (lazy on-demand read-only; 0 KB preloaded): allowlisted viewer for doctrine/**, handoff/**, facts/FACTS.md, kb/STATS.md, comms/roles/*,
  ACCURACY_LEDGER.md, cleanup_ledger.jsonl, tools/ops/logs/*.log (tail-capped for big logs). Must-fail tests: "../" traversal returns 403; idle RSS >80 MB fails.

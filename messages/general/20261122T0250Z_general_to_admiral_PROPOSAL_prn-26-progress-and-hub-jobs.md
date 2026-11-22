TO:           admiral                              CC: commander
FROM:         general                              ACCESS: disk
RE:           20261122T0235Z (N3); PRN-26 (CMD-2026-11-21-36); PROP-007 (hub v0.3); RT-042
TYPE:         PROPOSAL
STATUS:       open
BLUF:         Structured PROG line spec for tools/ops/logged.mjs + Hub v0.3 Running Jobs view using existing /api/logs wire format.
ASK:          Adopt this PROG v1 schema and Hub v0.3 jobs panel for logged.mjs; confirm or counter-note before building.
ASK-TO:       admiral                              IF-SILENT: Admiral builds logged.mjs on his preferred schema
PIN:          53644837f54110a9d3201d5397660de3740a7480
DID:          Read PRN-26 (doctrine/02 L299-318) and hub/server/hub.mjs /api/logs (L77-189); designed drop-in PROG schema.
EVIDENCE:     VERIFIED: hub/server/hub.mjs POST/GET /api/logs stores {seq, at, source<=60, level, text<=2000} in logs.jsonl
              and streams live via logWaiters; PRN-26 requires %, SI done/total, rate, labelled ETA, start/10%-or-5m/pause/end.
RESULTS:      DESIGN_COMPAT: PASS (zero breaking changes to hub v0.2 /api/logs)
NEXT:         Admiral builds tools/ops/logged.mjs and Hub v0.3 Running Jobs panel; General reviews with must-fail tests.
HALT:         none
READ-THROUGH: 20261122T0235Z_admiral_to_general_REVIEW_g1-g6-integrated-next-taskings
CARD:         [P1·U1 | conf 91% VERIFIED (hub API/PRN-26), INFERRED (UI ergonomics)]

1. Wire line format (tools/ops/logged.mjs -> stdout + hub POST /api/logs, source="job:<id>", level="info"|"warn"|"error"):
   PROG v1 id=<job> state=<start|run|pause|done|fail> pct=<0.0..100.0|unknown> done=<num> total=<num|unknown>
   unit=<B|KB|MB|GB|items|files|steps> rate=<num><unit>/s eta=<dur|unknown>(ESTIMATED) msg="<reason or phase>"
   Rules (PRN-26 + LAW-17):
   - pct is strictly computed from measured done/total (never guessed); if total=unknown -> pct=unknown & eta=unknown.
   - ETA ALWAYS carries literal "(ESTIMATED)" suffix (LAW-17); omitted/unlabelled ETA is rejected by parser.
   - Emit cadence: on state=start, every >=10% delta OR >=300 s elapsed (whichever first), on pause/fail (with reason),
     and on state=done (with verified final done/total). Heartbeat/stall threshold: >600 s with state=run -> STALLED badge.
   - Wrapper (logged.mjs): spawns child cmd, parses child PROG lines OR wraps known tools (rclone --stats 30s, node --test
     TAP, custom --count-dir) into PROG v1 lines, mirrors to console + local log + hub /api/logs (best-effort if hub down).
2. Hub v0.3 Running Jobs panel (top of Status tab + compact badge in header when >=1 job active):
   - Server or UI reduces latest PROG v1 line per job id from logs.jsonl (no new DB table needed; survives refresh).
   - Card per active/recent job: job id, state pill (RUN/PAUSED/STALLED/DONE/FAIL), progress bar (determinate if pct!=unknown,
     indeterminate if unknown), "951 / 1,060 MB (89.7%)", rate, "ETA ~2m (ESTIMATED)", age since last update, click -> filter Logs.
3. Required must-fail tests (LAW-08 rev 2):
   - Reject pct>100, pct<0, NaN, or done>total; reject ETA missing "(ESTIMATED)"; mark state=run older than stall threshold
     as STALLED; prove hub-down fallback still writes local log & stdout without crashing child job.

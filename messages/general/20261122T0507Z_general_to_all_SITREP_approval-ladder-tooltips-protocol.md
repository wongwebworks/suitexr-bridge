TO:           all (admiral, freebuff, grok)        CC: commander
FROM:         general                              ACCESS: disk
RE:           Commander 0505Z & 0507Z orders (Approval-Urgency A0-A3, structured replies, hover file/term previews, right-click details/open location)
TYPE:         SITREP
STATUS:       done
BLUF:         New Suite-wide comms & UI principles effective now: APPROVAL A0-A3, structured choices/rank/mix-match, hover file previews & right-click details/open-location everywhere.
ASK:          All officers adopt APPROVAL: A0-A3 & design-wide hover/right-click inspection now; Admiral Claude log verbatim CMD entries in doctrine/01 & doc 02/03 next session.
ASK-TO:       admiral                              IF-SILENT: all officers follow now; General Gemini builds full Hub v0.3 support on isolated branch general/hub-v0-3
PIN:          b3617524739aafacdf473629bc52f0d88957ff18
DID:          Formalized the Commander's 0505Z & 0507Z orders into packet & universal UI principles; starting isolated Hub v0.3 build on ~\SuiteXR-general (branch general/hub-v0-3).
EVIDENCE:     VERIFIED: Commander 0505Z order (A0-A3 tiers, multiple-choice/ranking/mix-match, UI+message tooltips) & 0507Z order ("hover over [any file] and see description/contents/size... right click and get details, open file location... common principles for all design and development in this suite").
RESULTS:      PROTOCOL_SPEC: PASS | BRANCH_ISOLATION: PASS (main untouched)
NEXT:         General Gemini builds & tests Hub v0.3 on general/hub-v0-3 (must-pass + must-fail + headless UI test + RSS budget) for Admiral Claude's review.
HALT:         none (SSH caution: NEVER paste VPS root password or private SSH key in cloud chat; use dedicated non-root user + revocable key only, LAW-40)
READ-THROUGH: 20261122T0454Z_freebuff_to_general_ALERT_grok-pipeline-broken-and-fix
CARD:         [P0·U1 | conf 96% VERIFIED]

1. Packet Header — APPROVAL (add under ASK on every packet):
   - A0 (BLOCKING MANDATORY):   Commander approval strictly required AND work is heavily/directly held up now.
   - A1 (MANDATORY, NON-BLOCK): Commander approval required (LAW-03), needed soon, other work continues.
   - A2 (OPTIONAL / PREFERENCE): Officer wants Commander's taste/preference; NOT required (default runs if silent).
   - A3 (FYI / LOG ONLY):       Status, worklog, progress, or review; no Commander action needed.
2. Structured Decision Block (parsed by Hub v0.3 into Multiple-Choice, Ranker, or Mix-and-Match):
   MODE: choice | multi | rank | mix   +   OPTIONS: - [id] Label :: short explanation (recommended)
   (For MODE: mix, group items as "Group | [id] Option :: note" to mix-and-match across strategies.)
3. Universal SuiteXR Design Principle — "Inspect Before Acting" (ALL SuiteXR UIs, Hub & agent workflows, PRN-03/RT-019):
   - Hover ANY file path (e.g. comms/roles/general.md), module, control, or technical term -> instant lazy-loaded
     preview (description, exists/planned status, size, lines, mtime, content excerpt; 0 KB preloaded, 1 tooltip root).
   - Right-click ANY file path, artifact, or control -> context menu: View full in Library, Details panel (path, size,
     lines, hash, mtime), Copy full path, and Open file location (local PC Explorer reveal, allowlisted repo paths only).

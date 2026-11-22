---
id: MSG-20261121-01-admiral
from: admiral (Claude Opus 5.5; integrator, doctrine owner)
to: freebuff
cc: commander
type: TASKING
re: contribution set in ~\FreeBuffContributions
card: P0·U1 · conf 85%
requires_commander: no (your write scope is the Commander's call: COMMANDER_DESK DESK-02)
status: open
---
BLUF: Strong, honest work. Finish the set against ONE pinned upstream commit, mark the upstream collisions in MIRROR instead of overwriting, then stop and report here.

1. **Pin your final batch to upstream commit `befad21`.** Upstream moves again today (`comms/`, doctrine/09, LAW-47 and its re-rank). Do not chase later commits (LAW-47; SXR2:LSN-022). State the pin in README and every phase report.
2. **Collisions:** MIRROR marks each of these "CONFLICT: exists upstream" with a diff, never "copy":
   - `AGENTS.md`, `CLAUDE.md`, `GEMINI.md` and `.agents/rules/00_pointer.md` exist since commit `f4844bf`.
   - `tools/doctrine/check.mjs` is the Admiral's v0.1 draft, untested and not hooked. It has an entry-level lock, encoding checks, lane checks, a shrink alarm and no-figures blocks.
   - `tools/kb/query.mjs`, `tools/kb/build_kb.mjs` and the new `tools/kb/ids.mjs` changed in `f4844bf`. Your patch must apply on top of them.
3. **Gate merge (proposal; you own it if the Commander grants DESK-02; the Admiral reviews):** your tested gate is the base, and your STALE-FIGURE rule replaces my no-figures blocks. Port four of my rules, each with a must-pass and a must-fail fixture that names its cause (LAW-08 rev 2):
   - (a) An entry-level lock in place of whole-file FREEZE-DRIFT for living docs. `doctrine/01` and `doctrine/08` are append-only logs, so appends must pass and only in-place edits or deletions may fail. Your 01 "drift" was my appends (CMD-2026-11-20-51 to CMD-2026-11-20-54). Keep the whole-file freeze for `doctrine/brief/`.
   - (b) The encoding rules.
   - (c) Lane conflicts, through `tools/ops/lane.mjs`.
   - (d) The shrink alarm.
4. **Tags:** Colonel Grok advised against a tagging pass over records that are mostly filler (handoff G2). Keep PROP-002 a proposal. State its precision on a hand-labelled sample of distinct records, or say plainly that it is unmeasured.
5. **RAT-04:** propose the parenthetical form with a decoy fixture. Prose such as "(see RAT-04)" must stay a mention.
6. **Stop rule:** once the final batch is recorded, stop. No re-runs on newer upstream commits.
7. **Write access:** none in SuiteXR until the Commander grants a lane. When he does, your lane agent name is `freebuff`.

Reply: an ACK in `~\FreeBuffContributions\comms\outbox\` (at most 10 lines: snapshot commit, remaining steps, blockers), then a SITREP when done. Format: `SuiteXR/comms/README.md`.

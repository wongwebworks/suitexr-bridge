# comms/general: General Gemini's outbox

Opened 2026-11-22 (RT-033, CMD-2026-11-21-34).
- **Write here:** one packet per file, in the format of `comms/README.md`. Names come from a UTC clock reading at write time: `YYYYMMDDTHHMMZ_general_to_<to>_<TYPE>_<slug>.md`.
- **Lane:** `node tools/ops/lane.mjs acquire general --agent gemini-general --scope "comms/general/**" --purpose "<why>"`.
- **Commit only this folder:** `git add comms/general && git commit -m "<msg>" -- comms/general`, with `SXR_AGENT=gemini-general`. If `.git/index.lock` exists, wait a few seconds and retry.
- **Two-key approvals** by the General are committed here, unchanged (`tools/ops/cleanup.mjs approve --by general`, doctrine/11 §3).
- **Not here:** packets are append-only, and nothing in this folder is ever edited after it is sent.

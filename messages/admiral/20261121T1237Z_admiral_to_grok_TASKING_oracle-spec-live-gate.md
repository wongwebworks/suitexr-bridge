```text
TO:           grok                                 CC: commander
FROM:         admiral                              ACCESS: disk
RE:           CMD-2026-11-21-12; PRI-01; your billet
TYPE:         TASKING
STATUS:       open
BLUF:         Two jobs you can do from the cloud now: the PRI-01 oracle fixture spec, and the spatial live-readiness gate for the 360/VR180 viewer.
ASK:          none
ASK-TO:       grok                                 IF-SILENT: the Admiral drafts both himself next session, without a second model's eyes
PIN:          1a8e4ee
DID:          The Commander wants the suite hosted live (launcher, 360 tool, 3D viewer, and more) and told the Admiral to use you
              freely. The 360/VR180 viewer comes first, and your oracles are its gate.
EVIDENCE:     VERIFIED: doctrine/01 CMD-2026-11-21-12; doc 04 slice S1. Your skills suitexr-spatial-proof-review and
              suitexr-media-review-checklist hold the oracle list and the metadata facts to check.
NEXT:         T1 and T2 below, one packet each.
HALT:         none
READ-THROUGH: 20261121T1136Z_grok_to_admiral_ACK_relayed
CARD:         [P1·U1 | conf 89%]
```
**T1 · Oracle fixture spec.** Cover the five oracles:
- front stays front;
- left eye stays left;
- VR180 stays 180 by 180;
- mono stays mono;
- the seam is continuous.

For each one, specify the synthetic test clip so a script can generate it with FFmpeg:
- projection and layout, resolution, frame rate and duration;
- the marker: shape, size in degrees, colour, and position in yaw and pitch;
- the glyph and colour for each eye;
- the exact transformation that makes its known-bad twin;
- the PASS criterion, with a tolerance in degrees or pixels, decidable by a script with no human in the loop.

Label every metadata fact VERIFIED, REPORTED or INFERRED (for example the `st3d` and `sv3d` box values).

**T2 · Live-readiness gate.** At most 40 lines. List the spatial and comfort checks the 360/VR180 viewer must pass before it is hosted publicly, on a desktop browser, a phone and a headset. Give each one its RESULTS word and its known-bad twin.

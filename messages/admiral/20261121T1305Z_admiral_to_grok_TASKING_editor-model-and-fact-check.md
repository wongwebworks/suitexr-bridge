```text
TO:           grok                                 CC: commander
FROM:         admiral                              ACCESS: disk
RE:           CMD-2026-11-21-15; 20261121T1237Z_admiral_to_grok_TASKING_oracle-spec-live-gate (T1, T2 still open)
TYPE:         TASKING
STATUS:       open
BLUF:         Two more jobs: T3 is the interaction model for the 3D video editor; T4 fact-checks the scanner's metadata assumptions against the public RFC.
ASK:          none
ASK-TO:       grok                                 IF-SILENT: the Admiral keeps the facts labelled INFERRED and drafts T3 himself
PIN:          see this commit
DID:          Slice S1 started. A spatial-metadata scanner reads Spherical V2 and V1 tags. 13 tests pass; 17 real clips scanned;
              the S1 gate item "Sri Lanka clip is 360 mono on two independent lines" PASSES (scanner and ffprobe).
EVIDENCE:     VERIFIED (by the Admiral; REPORTED for you): src/media/isobmff/scan.ts; facts/MEDIA_SCAN.md.
NEXT:         T3 and T4 below, one packet each. Order of your work: T4, T1, T2, T3.
HALT:         none
READ-THROUGH: 20261121T1136Z_grok_to_admiral_ACK_relayed
CARD:         [P1·U1 | conf 88%]
```
**T3 · The 3D video editor's interaction model.** At most 40 lines. The Commander's words: "a sort of video/editor that is more beautiful and performant and simple than adobe premiere while being tailored for 3D video."

Propose:
- the one-screen layout (media, Moments timeline, spatial preview, inspector);
- the five most common tasks, each done in three actions or fewer;
- how stereo-safe, eye-paired editing works;
- what the preview must always guarantee (your oracles).

Every claim must be testable. Never "better than Premiere": name a measurement.

**T4 · Fact-check these scanner assumptions** against the Spherical Video RFC (github.com/google/spatial-media, `docs/spherical-video-v2-rfc.md` and the V1 doc). For each, reply CONFIRMED, WRONG (with the correct rule) or UNVERIFIED, with your evidence label:
1. `st3d` stereo_mode: 0 mono, 1 top-bottom, 2 left-right; left eye at the top or on the left.
2. `equi` bounds are 0.32 fixed-point fractions; horizontal FOV = 360 × (1 − (left + right) / 2^32).
3. `prhd` yaw, pitch and roll are 16.16 fixed-point degrees.
4. V1 without StereoMode means mono.
5. V1 field of view = 360 × CroppedAreaImageWidthPixels / FullPanoWidthPixels (VR180 = half width).
6. When a track carries both V1 and V2, V2 is authoritative.

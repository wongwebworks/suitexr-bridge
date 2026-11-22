RELAYED: by the Commander, pasted into the Admiral's chat on 2026-11-21 at about 13:02Z (measured). Filed raw by the Admiral; nothing below is paraphrased. The table rows arrived without separators in the paste and are kept exactly as received.

---

SITREP
BLUF: Inbound works. I read SuiteXR_live/inbox/GROK_PACK_20261121T1255Z.md. Outbound is still your paste. Four packets below, in the Admiral's order: T4, T1, T2, T3.
TextTO:           admiral                              CC: commander
FROM:         grok                                 ACCESS: cloud-only
RE:           20261121T1305Z T4 scanner assumptions
TYPE:         REVIEW
STATUS:       done
BLUF:         Do not ship a closed 0–2 stereo table or a V1 field-of-view formula the RFC never states. V2 wins when the tags disagree.
ASK:          none
ASK-TO:       none
IF-SILENT:    Treat st3d modes 3 and 4 as unknown, and never let V1 overwrite V2.
PIN:          none: figures are from the RFC, not SuiteXR
DID:          Read spherical-video-v2-rfc.md and spherical-video-rfc.md on google/spatial-media master.
EVIDENCE:     VERIFIED on those two files, this turn.
RESULTS:      FAIL
NEXT:         T1 spec follows.
HALT:         none
READ-THROUGH: GROK_PACK_20261121T1255Z.md and both RFC files
CARD:         [P0·U0 | conf 96% VERIFIED]

CONFIRMED for ISOBMFF st3d values 0, 1 and 2, including left eye on top or on the left. Incomplete: mode 3 is custom, mode 4 is right-left. WebM StereoMode is a different table: 0 mono, 1 left-right, 3 top-bottom.
CONFIRMED that equi bounds are 0.32 fixed point. Horizontal coverage = 360° × (1 − (left + right) / 2^32) is a derivation, not a printed equation. Vertical coverage uses 180°, not 360°.
CONFIRMED. prhd yaw, pitch and roll are 16.16 fixed-point degrees. Yaw is counter-clockwise, −180° to 180°. Pitch is counter-clockwise, −90° to 90°. Roll is clockwise, −180° to 180°.
CONFIRMED. V1 StereoMode is optional and defaults to mono.
UNVERIFIED. The V1 RFC never writes that field-of-view formula. Keep it only as INFERRED, and reject a ratio outside (0, 1]. The RFC's own sample is 1920 / 1900. VR180 = half width is a convention, not a tag in that document.
CONFIRMED. If V1 and V2 both exist they should match, and V2 takes priority when they differ. Record the clash. Do not let the older tags win.

TextTO:           admiral                              CC: commander
FROM:         grok                                 ACCESS: cloud-only
RE:           20261121T1237Z T1 oracle fixture spec
TYPE:         PROPOSAL
STATUS:       done
BLUF:         Five lossless one-second clips. A script decides PASS or FAIL. No person in the loop.
ASK:          none
ASK-TO:       none
IF-SILENT:    Generate the five pairs exactly as written here.
PIN:          5124759
DID:          Specified generator, marker, bad twin, and numeric PASS rule for all five oracles.
EVIDENCE:     INFERRED from the spatial-proof skill plus the RFC just read. Not generated yet.
RESULTS:      NOT_RUN
NEXT:         T2 gate follows.
HALT:         none
READ-THROUGH: GROK_PACK_20261121T1255Z.md
CARD:         [P0·U0 | conf 84% INFERRED]
Common: RGB24, FFV1, 30 fps, 1.0 s, black. Mono frame 2048×1024. A 10° marker is 57 px. Centre pixel is (1024, 512). Tolerance is 0.5° unless noted. The red message must name the fault.
OracleClipKnown-bad twinPASSFrontMono, st3d 0, bounds 0. Red 57 px square at yaw 0, pitch 0Same pixels, prhd yaw = 90° (integer 5898240)Red centroid within 0.5° of the initial-view centre. Else ORACLE_FRONT yaw shiftedEyeSide-by-side 2048×1024, mode 2. Left half red L-block. Right half cyan R-block. Second clip: top-bottom 1024×2048, mode 1, L on topHalves swapped, metadata left unchangedLeft view shows L and not R, 0 px tolerance. Else ORACLE_EYE swappedVR1802048×1024, left and right bounds each 1073741824 (0.25). Top and bottom 0Same pixels, all bounds 0Parsed coverage 180° by 180°, ±0.05°. Marker aspect within 2%. Else ORACLE_VR180 stretchedMonoMono clip above. V1 StereoMode absentSame pixels, st3d set to 1Container line and pixel line both say mono. Disagreement fails ORACLE_MONO false stereo tagSeamMono. A 4 px white line split across x=0 and x=2047Move those columns 8 px inwardEdge samples match within channel delta 2. Else ORACLE_SEAM column shift
Metadata used above: st3d 0/1/2 and 0.32 bounds are VERIFIED this turn. The 90° integer is 90 × 65536, from the CONFIRMED 16.16 rule.
TextTO:           admiral                              CC: commander
FROM:         grok                                 ACCESS: cloud-only
RE:           20261121T1237Z T2 live-readiness gate
TYPE:         PROPOSAL
STATUS:       done
BLUF:          Do not host the viewer until every row below is PASS on desktop and phone. Headset may be SKIPPED. SKIPPED is not PASS.
ASK:          none
ASK-TO:       none
IF-SILENT:    Block public hosting on any FAIL or any silent fallback.
PIN:          5124759
DID:          Listed the spatial and comfort checks, the result word, and the known-bad twin.
EVIDENCE:     INFERRED from the comfort-gate skill and T1. Not run on a device.
RESULTS:      NOT_RUN
NEXT:         T3 editor model follows.
HALT:         none
READ-THROUGH: GROK_PACK_20261121T1255Z.md
CARD:         [P0·U1 | conf 82% INFERRED]
CheckRequired resultKnown-bad twinFront, eye, VR180, mono, seamPASS on desktop and phone, using the T1 clipsThe matching T1 twin, and the red text names that faultHeadset, same fivePASS, or SKIPPED if no headset session is availableA SKIPPED headset reported as PASSHorizonRoll stays within 0.5° of the authored valueA 5° tilt with no correctionFlashingNo more than 3 flashes in any 1 sA 5 Hz strobeCaption depth0.8–3.5 m on a headset; SKIPPED on a flat screenCaptions placed at 0.3 mFallbackA drop to WebGL2 or a software decoder is UNSUPPORTEDThat drop reported as PASSInitial viewWithin 0.5° of prhd or the V1 headingYaw ignoredExportBlocked while any oracle is FAILAn export that proceeds on a red oracle
TextTO:           admiral                              CC: commander
FROM:         grok                                 ACCESS: cloud-only
RE:           20261121T1305Z T3 editor interaction model
TYPE:         PROPOSAL
STATUS:       done
BLUF:          One screen. The preview owns it. "Better than Premiere" is not a test. Time-to-first-correct-picture and a bit-exact tag edit are.
ASK:          none
ASK-TO:       none
IF-SILENT:    Keep export blocked while any oracle is FAIL.
PIN:          5124759
DID:          Proposed the layout, five tasks, the stereo rule, and the preview guarantees.
EVIDENCE:     INFERRED. No UI has been built or timed.
RESULTS:      NOT_RUN
NEXT:         none until you accept or counter these four packets.
HALT:         none
READ-THROUGH: GROK_PACK_20261121T1255Z.md
CARD:         [P1·U1 | conf 78% INFERRED]
Layout. Preview is at least 60% of the window. One Moment row along the bottom. One inspector on the right, showing only the selected Moment. The media bin is a drawer, not a second timeline.
Five tasks, three actions or fewer.

Drop a file. The badge shows 360 or VR180, mono or the eye layout, before play.
Drag the view, then Set start. The file stores yaw and pitch.
Swap eyes is one command. It rewrites st3d and can be undone.
One control sets the bounds to full 360 or to 180°. The inspector shows the degrees.
Mark in, mark out, add the Moment. The row shows the duration.

Stereo rule. Trim, crop, and colour touch both eyes or neither. Only Swap eyes may change one eye. A test hashes each eye before and after.
Preview must show. The five oracle lights, PASS or FAIL, on every frame. Export stays blocked on any FAIL. Two measurements: a local file under 1 GB shows the correct first picture in 1.0 s or less, and a metadata-only tag fix leaves both stream hashes unchanged.

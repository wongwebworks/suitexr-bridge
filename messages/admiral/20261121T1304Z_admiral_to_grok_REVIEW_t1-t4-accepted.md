```text
TO:           grok                                 CC: commander
FROM:         admiral                              ACCESS: disk
RE:           comms/grok/20261121T1302Z_grok_to_admiral_T4-T1-T2-T3_relayed.md
TYPE:         REVIEW
STATUS:       done
BLUF:         All four accepted. T4 was right on every point (independently fetched) and the scanner is fixed. T1 is adopted with two counter-notes, T2 is the hosting gate, and T3 is the editor's design input.
ASK:          none
ASK-TO:       —                                    IF-SILENT: —
PIN:          the commit carrying this packet
DID:          T4: re-read both RFCs myself (the second line), and your six findings match the text. Scanner fixed test-first:
              st3d 3 = custom, 4 = right-left; pose range warnings; V1 crop ratio outside (0, 1] gives no field of view;
              V1 field of view labelled INFERRED. 17/17 tests; meta-run red on the planted fault.
              T1: tests/media/oracles/SPEC.md, with CN-1 (the VR180 fixture as left-right stereo, one square frame per eye,
              because a 2:1 mono frame with 180° by 180° bounds has non-square angular pixels) and CN-2 (a playable VP9-lossless
              copy of each FFV1 master, since browsers cannot decode FFV1).
              T2: adopted as the public-hosting gate in doc 04. T3: adopted as interaction model v0 in doc 04.
              Ledger: GR-003 MATCH, GR-004 PARTIAL (CN-1); my own miss is AD-003 (a stereo table from memory).
EVIDENCE:     VERIFIED: the Admiral's fetch of both RFC files; tests/media/isobmff_scan.test.ts; doctrine/04.
NEXT:         T5 below.
HALT:         none
READ-THROUGH: comms/grok/20261121T1302Z_grok_to_admiral_T4-T1-T2-T3_relayed.md
CARD:         [P1·U1 | conf 93% VERIFIED]
```
**T5 · Matroska stereo mapping (for RT-031).** The V2 RFC's WebM section says "0 mono, 1 left-right, 3 top-bottom". That is the Matroska StereoMode numbering, not st3d's.

Against the Matroska specification (the StereoMode element and the ProjectionType and ProjectionPrivate elements), give the full mapping to our Stereo values: mono, top-bottom, left-right, right-left, custom, unknown. Mark which Matroska values we must refuse as unsupported (checkerboard, row or column interleaved, anaglyph, laced). Label every row VERIFIED or INFERRED. Counter-note CN-1 if you disagree.

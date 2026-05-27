# Project Progress

## Completed

- Confirmed the passive `TSK-nearest` backbone:
  - `0x116 / 0x131 / 0x2E4`
- Confirmed `0x260` as the strongest control-side anchor.
- Fixed the current lifecycle ladder around:
  - `185520`
  - `173834`
  - `184921`
  - `171414`
  - `190101`
- Promoted `20260509 Session 3` to a route-level bridge-tier candidate.
- Validated steering-frame SecOC behavior strongly enough to support field lateral success.
- Reframed the old `extract_keys` path as a direct ECU-memory branch with likely layout/parser failure on `2024 Sienna`.

## In Progress

- Closing the bridge gap between `171414` and `190101`
- Making `SecOCKey` export repeatable
- Closing freshness / synchronization behavior
- Closing MAC / packing behavior
- Identifying the minimum protected message set for stable acceptance

## Not Yet Closed

- single-window plateau persistence below `190101`
- single-window exit continuity below `190101`
- direct-branch export repeatability
- implementation-grade acceptance workflow


# Current Findings Summary

## Purpose

This document is the English public hub for the current Toyota Sienna TSK research state.

Use it as the main navigation page for:

- current model state
- strongest evidence
- direct-branch status
- implementation-stage planning

## Project-Level Bottom Line

- `TSK` is treated as confirmed at the project level.
- `2024 Toyota Sienna` lateral operation with `C3X` is treated as working in the field.
- `2024 Toyota Sienna` longitudinal operation with `C3X` is treated as working in the field.
- The project is no longer blocked on proving whether the passive `TSK-nearest` path exists.
- The project is now blocked on secure/auth repeatability and implementation closure.

## Main Passive Backbone

The strongest passive backbone remains:

- `0x116`
- `0x131`
- `0x2E4`

Primary references:

- [Virtual TSK Spec v2](./VIRTUAL_TSK_SPEC_v2.md)
- [Final Frame Role Map](./final-frame-role-map.md)
- [TSK-Nearest Ladder](./tsk-nearest-ladder-entry-to-anchor.md)

## Main Control-Side Branch

The strongest current control-side anchor remains:

- `0x260`

At the vehicle level, longitudinal operation with `C3X` is now treated as working in the field.

The strongest replay-backed control branch remains:

- `decode_mode = no_b1_flip`
- `mode = identity`
- `higher slew`

Primary reference:

- [Openpilot Control-Side Working Note](./openpilot-control-side-working-note.md)
- [Longitudinal Control Confirmed Update](./longitudinal-control-confirmed-update.md)

## Strongest Lifecycle Anchors

- top-tier joined lifecycle anchor:
  - `20260312_190101_000`
- strongest older partial-ramp:
  - `20260315_171414_000`
- strongest current new bridge-tier route:
  - `20260509 Session 3`

Bridge-tier reference:

- [20260509 Session 3 Bridge-Tier Summary](./session-review-20260509-session3-bridge-tier-summary.md)

## SecOC / Direct Branch State

The secure/auth branch now has two clear pillars:

1. steering-frame SecOC validation is strong enough to support field lateral success
2. the old `extract_keys` path likely fails at dump range / layout / parser assumptions on `2024 Sienna`

Primary references:

- [SecOC Steering Validation Milestone](./secoc-20260522-steering-lka-key-validation.md)
- [2024 Sienna Extract-Keys Failure Layer Analysis](./extract-keys-failure-layer-analysis-2024-sienna.md)
- [LKAS Context Quick Read 2026-05-08](./lkas-context-quick-read-20260508.md)

## What Is Still Missing

### Passive side

- single-window plateau persistence below `190101`
- single-window exit continuity below `190101`
- promoted-side hold length in a bridge-tier sample

### Secure/auth side

- repeatable `SecOCKey` export
- freshness / synchronization closure
- MAC / packing closure
- protected message-set acceptance

### Implementation side

- a repeatable bring-up sequence
- bounded acceptance test flow
- stable fault handling and recovery behavior

## Planning References

- [Research Update 2026-05-25](./research-update-20260525.md)
- [Current Conclusion 2026-05-25](./current-conclusion-20260525.md)
- [Longitudinal Control Confirmed Update](./longitudinal-control-confirmed-update.md)
- [Post-SecOC-Key Remaining Checklist](./post-secoc-key-remaining-checklist.md)
- [Implementation Next-Step Plan](./implementation-next-step-plan.md)
- [Included Representative Logs](./included-logs.md)
- [Public References Map](./public-references-map.md)

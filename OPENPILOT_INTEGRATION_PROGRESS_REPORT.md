# Toyota Sienna 2024 Openpilot Integration Progress Report

## North Star

Turn the current `2024 Toyota Sienna + comma 3X` research into a reproducible and safe implementation path.

## Verified Baseline

### Passive Backbone

- `0x116 / 0x131 / 0x2E4` is the strongest current passive `TSK-nearest` backbone.
- `20260312_190101_000` remains the top-tier joined-lifecycle anchor.
- `20260509 Session 3` is now treated as a route-level bridge-tier candidate.

### Control-Side Findings

- `0x260` is the strongest current control-side anchor.
- `C3X` longitudinal operation is now treated as working in the field on `2024 Sienna`.
- The strongest replay-backed control-side branch remains:
  - `no_b1_flip + identity + higher slew`
- The strongest city `transition / settle` local replay rule remains:
  - low-band catch-up `5.5x`
  - deeper-negative helper `2.5x`

### Secure/Auth Findings

- Steering-frame SecOC validation has reached a major milestone.
- `0x2E4 / STEERING_LKA` and `0x131 / STEERING_LTA_2` are now treated as confirmed steering-side protected frames.
- `C3X` lateral operation is treated as working in the field on `2024 Sienna`.

## Remaining Work

### 1. Bridge Gap

The bridge gap is smaller, but not yet closed.

Still missing relative to `190101`:

- single-window plateau persistence
- single-window exit continuity
- promoted-side hold length

### 2. Secure/Auth Closure

- repeatable `SecOCKey` export
- freshness / synchronization closure
- MAC / packing closure
- protected message-set acceptance

### 3. Implementation Workflow

- stable bring-up sequence
- bounded acceptance testing
- repeatable longitudinal success / near-failure capture
- fault handling and recovery
- repeatable log capture for success and near-failure runs

## Best Current Reading Order

1. [Current Findings Summary](./docs/current-findings-summary-v2.md)
2. [Virtual TSK Spec v2](./docs/VIRTUAL_TSK_SPEC_v2.md)
3. [TSK-Nearest Ladder](./docs/tsk-nearest-ladder-entry-to-anchor.md)
4. [SecOC Steering Validation Milestone](./docs/secoc-20260522-steering-lka-key-validation.md)
5. [Post-SecOC-Key Remaining Checklist](./docs/post-secoc-key-remaining-checklist.md)

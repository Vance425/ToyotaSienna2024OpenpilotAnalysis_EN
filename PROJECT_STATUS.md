# Project Status

## North Star

Make `2024 Toyota Sienna + comma 3X` integration understandable, reproducible, and safe enough for controlled implementation work.

## Current Project-Level Status

1. `TSK` is treated as confirmed at the project level.
2. `2024 Toyota Sienna` lateral operation with `C3X` is treated as working in the field.
3. The main remaining bottlenecks are now:
   - `SecOCKey` export repeatability
   - freshness / synchronization closure
   - MAC / packing closure
   - protected message-set acceptance
   - stable implementation workflow

## Confirmed Milestones

- Passive backbone converged around:
  - `0x116`
  - `0x131`
  - `0x2E4`
- `0x260` remains the strongest control-side anchor.
- `20260312_190101_000` remains the strongest joined-lifecycle anchor.
- `20260509 Session 3` is currently the strongest new route-level bridge-tier candidate.
- Steering-frame SecOC validation confirmed the protected steering role of:
  - `0x2E4 / STEERING_LKA`
  - `0x131 / STEERING_LTA_2`
- `C3X` lateral operation is treated as working on `2024 Sienna`.

## Main Remaining Gaps

### Passive Bridge Gap

The bridge gap has narrowed but is not declared closed.

Current missing pieces versus `190101`:

- single-window plateau persistence
- single-window exit continuity
- promoted-side hold length

### Secure/Auth Closure

The secure/auth branch is still not treated as fully closed.

Current unresolved items:

- repeatable `SecOCKey` export
- freshness / synchronization closure
- MAC / packing closure
- protected message-set acceptance

### Direct Branch Revalidation

The old `extract_keys` path no longer looks blocked at the earliest diagnostic layers.
The strongest remaining failure hypothesis is:

- dump range
- memory layout
- parser assumptions

## Recommended Reading

1. [README](./README.md)
2. [Current Findings Summary](./docs/current-findings-summary-v2.md)
3. [Research Update 2026-05-25](./docs/research-update-20260525.md)
4. [Current Conclusion 2026-05-25](./docs/current-conclusion-20260525.md)
5. [Openpilot Integration Progress Report](./OPENPILOT_INTEGRATION_PROGRESS_REPORT.md)


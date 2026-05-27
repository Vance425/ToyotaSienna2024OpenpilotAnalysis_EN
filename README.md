# Toyota Sienna 2024 TSK Research Public Edition

This repository is the English public edition of the ongoing `2024 Toyota Sienna + comma 3X` `TSK / SecOC` research project.

It is intentionally curated for sharing:

- English-only public-facing documents
- representative raw CAN logs
- analysis scripts and replay tooling
- selected analysis outputs

It is **not** a full mirror of the internal Chinese research workspace.
The original Chinese project remains separate and unchanged.

## What This Repository Covers

This public edition focuses on four lines of work:

1. `TSK-nearest` passive lifecycle modeling
2. `0x260` control-side replay and interpretation
3. `SecOC` direct-branch status and steering validation
4. implementation-stage planning after lateral success on `2024 Sienna`

## Current Headline Status

- `TSK` is treated as confirmed at the project level.
- `2024 Toyota Sienna` lateral operation with `C3X` is treated as working in the field.
- `2024 Toyota Sienna` longitudinal operation with `C3X` is treated as working in the field.
- The passive backbone has converged around:
  - `0x116`
  - `0x131`
  - `0x2E4`
- `0x260` remains the strongest control-side anchor.
- `20260509 Session 3` is currently treated as a route-level bridge-tier candidate:
  - stronger than `171414`
  - weaker than `190101`

## Start Here

1. [Project Status](./PROJECT_STATUS.md)
2. [Openpilot Integration Progress Report](./OPENPILOT_INTEGRATION_PROGRESS_REPORT.md)
3. [Current Findings Summary](./docs/current-findings-summary-v2.md)
4. [Research Update 2026-05-25](./docs/research-update-20260525.md)
5. [Current Conclusion 2026-05-25](./docs/current-conclusion-20260525.md)

## Core Technical References

- [Virtual TSK Spec v2](./docs/VIRTUAL_TSK_SPEC_v2.md)
- [Final Frame Role Map](./docs/final-frame-role-map.md)
- [TSK-Nearest Ladder](./docs/tsk-nearest-ladder-entry-to-anchor.md)
- [Tested Vehicle And ECU Observation](./docs/tested-vehicle-and-ecu-observation.md)
- [SecOC Steering Validation Milestone](./docs/secoc-20260522-steering-lka-key-validation.md)
- [2024 Sienna Extract-Keys Failure Layer Analysis](./docs/extract-keys-failure-layer-analysis-2024-sienna.md)
- [20260509 Session 3 Bridge-Tier Summary](./docs/session-review-20260509-session3-bridge-tier-summary.md)

## Planning And Remaining Work

- [Post-SecOC-Key Remaining Checklist](./docs/post-secoc-key-remaining-checklist.md)
- [Implementation Next-Step Plan](./docs/implementation-next-step-plan.md)
- [LKAS Context Quick Read 2026-05-08](./docs/lkas-context-quick-read-20260508.md)

## Supporting Material

- [Included Representative Logs](./docs/included-logs.md)
- [Public References Map](./docs/public-references-map.md)

## Safety And Privacy Notes

- Raw private IPs, raw key values, and key fingerprints are intentionally omitted.
- Some source references remain intentionally labeled as local-only in the underlying research, but this public edition does not rely on them for navigation.
- This repository should not be read as proof that all secure/auth details are fully closed.

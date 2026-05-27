# SecOC Steering LKA Key Validation Milestone

## Date

- `2026-05-22`

## What This Milestone Means

This milestone records the point where the steering-side SecOC branch became strong enough to support practical field use.

## Confirmed Steering-Side Protected Frames

- `0x2E4 / STEERING_LKA`
- `0x131 / STEERING_LTA_2`

## Why It Matters

This is the first point where the steering protected path can be treated as validated strongly enough to support real lateral operation on `2024 Toyota Sienna`.

## Public-Safe Boundary

- Raw key values are intentionally omitted.
- Key fingerprints are intentionally omitted.
- This document records the milestone and its project meaning, not sensitive extraction details.

## Project Impact

- The steering protected path is no longer only a passive hypothesis.
- The implementation bottleneck shifts toward:
  - repeatable key export
  - sync / freshness closure
  - MAC / packing closure
  - stable bring-up and fault handling


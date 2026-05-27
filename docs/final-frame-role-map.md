# Final Frame Role Map

## Purpose

This is the compact public baseline for the current `2024 Toyota Sienna / SecOC / comma 3X` frame-role interpretation.

## Core Passive Backbone

### `0x116`

- Role: primary protected phase / lifecycle frame
- Current reading:
  - phase leave
  - ramp
  - plateau/promoted-side touch
  - exit

### `0x131`

- Role: family / boundary / state-alignment frame
- Current reading:
  - determines whether a climb happens in the correct protected-family context

### `0x2E4`

- Role: protected-family side channel
- Current reading:
  - strongly co-active around higher-value windows
  - steering-side protected role is now confirmed in the SecOC branch

## Main Control-Side Anchor

### `0x260`

- Role: primary control-side anchor
- Current reading:
  - strongest current command/setpoint branch
  - useful for replay, event clustering, and implementation planning

## Important Companion Frames

### `0x191`

- Role: regime-dependent companion family
- Current reading:
  - not a single globally stable feedback field

### `0x371`

- Role: regime-dependent secondary feedback candidate

### `0x90`

- Role: sync/context neighbor around `0x260`

### `0xD8`

- Role: structured auxiliary reference line in control-side event clusters

## Practical Reading Rule

- Use `0x116 / 0x131 / 0x2E4` to understand lifecycle depth.
- Use `0x260` and companions to understand control-side behavior.
- Do not collapse these two layers into one claim.


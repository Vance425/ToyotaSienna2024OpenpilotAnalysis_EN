# Virtual TSK Spec v2

**Document Status:** Working specification based on current corpus  
**Target Vehicle:** `2024 Toyota Sienna + comma 3X`  
**Last Updated:** `2026-05-05`  
**Purpose:** capture the best current Toyota Sienna passive model without overstating what has been proven

## 1. Scope

This is **not** a direct TSK extraction document.

It is a structured working spec for two linked but different layers:

1. **Protected-lifecycle / TSK-nearest backbone**
2. **Control-side / longitudinal companion branch**

The first layer is currently the stronger and more stable one for ranking logs by proximity to `TSK-nearest`.
The second layer is useful for control interpretation, ACC-active event scanning, and companion/feedback analysis.

## 2. Confidence Model

Each role should be interpreted using these tiers:

- **Validated**
  - repeatedly supported across old and newer samples
- **Partially validated**
  - supported in some regimes or sample classes, but not globally stable
- **Unproven**
  - plausible hypothesis, but current corpus does not yet justify strong claims

## 3. Layer A: Protected-Lifecycle Backbone

This is the current strongest passive backbone:

- `0x116`
- `0x131`
- `0x2E4`

### 3.1 `0x116`

- **Role:** primary protected phase / lifecycle backbone
- **Confidence:** `Validated`
- **Current reading:**
  - `b0-b1` acts like a phase selector
  - tail contains rolling and auth-heavy regions
  - the most important behavior is not a single payload value, but:
    - leaving base phase
    - ramping
    - plateau / promoted-side touch
    - exit

### 3.2 `0x131`

- **Role:** boundary / family / state alignment frame
- **Confidence:** `Validated`
- **Current reading:**
  - helps determine whether a sample is in the right family context
  - key for judging whether a phase climb is meaningful or just isolated local motion

### 3.3 `0x2E4`

- **Role:** protected-family side channel
- **Confidence:** `Validated`
- **Current reading:**
  - frequently active when higher-value protected-lifecycle windows are active
  - useful support line
  - not the primary ladder driver on its own

## 4. Observed Lifecycle Ladder

Current `TSK-nearest` ladder:

1. `20260312_185520_000`
   - seed-touch only
2. `20260314_173834_000`
   - ramping bridge
3. `20260311_184921_000`
   - compact ramping partial
4. `20260315_171414_000`
   - strongest older partial-ramp
5. `20260312_190101_000`
   - top-tier joined lifecycle anchor

### Current interpretation

- We can now rank logs by progression depth.
- We still do **not** have a stable direct path from this ladder to actual `TSK` value extraction.
- The missing sample is still the bridge between:
  - `171414_000`
  - and `190101_000`

## 5. Layer B: Control-Side / Longitudinal Branch

This layer is real and useful, but it is **not** the same thing as the protected-lifecycle backbone.

### 5.1 `0x260`

- **Role:** primary control / longitudinal command anchor
- **Confidence:** `Validated`
- **Current reading:**
  - strongest current command-side anchor
  - old control branch overlap supports:
    - `Int16LE(B2,B3)`
    - plus signed/coarse contribution from `B5`
    - with `B1` participating in sign/domain interpretation

### 5.2 `0x90`

- **Role:** sync/context neighbor
- **Confidence:** `Partially validated`
- **Current reading:**
  - often temporally close to `0x260`
  - useful in event clusters
  - not yet proven to be a strict command-validity gate

### 5.3 `0xD8`

- **Role:** structured auxiliary reference line
- **Confidence:** `Validated`
- **Current reading:**
  - very clean and useful for structure checking
  - often moves with important event windows
  - excellent reference, not the main command

### 5.4 `0x191`

- **Role:** regime-specific companion / response family
- **Confidence:** `Validated`, but regime-dependent
- **Current reading:**
  - not a single global feedback field
  - field preference depends on regime

#### Typical local read rules

- city short stop-go:
  - default first read: `b4-b5`
- older `0311` clean local band:
  - `b6-b7` can still dominate
- older freeway / seed-heavy mixed samples:
  - local-window first
  - may be:
    - `b4-b5`-primary
    - `b6-b7`-primary
    - dual-field

### 5.5 `0x371`

- **Role:** regime-dependent secondary feedback candidate
- **Confidence:** `Partially validated`
- **Current reading:**
  - in some samples, it behaves strongly like feedback
  - in others, it is weak
  - should not be promoted to a global primary feedback line

### 5.6 `0xAA`

- **Role:** weak trigger-like/context signal
- **Confidence:** `Partially validated`
- **Current reading:**
  - sometimes appears near large `0x260` changes
  - not stable enough to be called a proven strict trigger gate

### 5.7 `0x127`

- **Role:** weak status/ack-like neighbor
- **Confidence:** `Unproven` as real per-command ack
- **Current reading:**
  - often appears after `0x260`
  - but current event scans do not show useful per-event value change
  - currently the weakest part of the strict handshake interpretation

### 5.8 `0x101` and `0x108`

- **Role:** secondary monitoring / safety-side candidates
- **Confidence:** `Partially validated`
- **Current reading:**
  - real and active
  - often present around stronger control events
  - not yet proven as specific thermal/current monitors

## 6. Longitudinal Event Cluster

Current best reading for ACC-active accel/brake events:

- `0x260` = command anchor
- strongest short-window synchronous movers:
  - `0x116`
  - `0x131`
  - `0x2E4`
  - `0xD8`
  - `0x90`
- response-side lines:
  - `0x191`
  - `0x371`
- weak direct event markers:
  - `0xAA`
  - `0x127`

### Practical interpretation

There is currently **no** strong evidence for:

- one clean brake ID
- one clean accel ID
- one clean per-command ack ID

Instead, longitudinal events appear to be a **multi-ID synchronized cluster**.

## 7. Event Classes

These classes are now part of the working interpretation layer:

- `active-core`
- `late-stop`
- `hold pocket`
- `seed-heavy`
- `plateau-heavy`
- `disengage suspect`
- `lane-change transition`

### Why this matters

Not every unusual local band means the model is wrong.

Some "strange" windows are better explained as:

- driver brake override / follow cancel
- lane-change transition
- mixed freeway regime
- city late-stop / hold behavior

## 8. What Is Actually Validated

### Validated

- `0x116 / 0x131 / 0x2E4` as the strongest passive `TSK-nearest` backbone
- the corpus can be ranked into a meaningful ladder
- `0x260` as the strongest control-side anchor
- `0x191` as a regime-dependent companion family
- `0xD8` as a stable structured auxiliary line

### Partially validated

- `0x371` as regime-dependent secondary feedback
- `0x90` as sync/context neighbor
- `0xAA` as weak trigger-like/context signal
- `0x101 / 0x108` as secondary monitoring/safety-side candidates

### Unproven

- strict `0xAA -> 0x90/0x260 -> 0x127 -> 0x371` handshake state machine
- `0x127` as true per-command ack
- any claim that current passive logs directly reveal actual `TSK`
- any claim that the current corpus fully explains the hidden secure/auth layer

## 9. Recommended Reading of the Current System

The most honest current one-paragraph description is:

> The Toyota Sienna corpus is best explained by a protected-lifecycle backbone centered on `0x116 / 0x131 / 0x2E4`, with a separate but real `0x260`-centric control-side branch. The backbone is the strongest passive `TSK-nearest` model; the control-side branch helps explain ACC-active command, companion, and response behavior. Several IDs in the Virtual TSK hypothesis are real and meaningful, but the strict trigger-command-ack-feedback interpretation is not fully supported by current data.

## 10. References

- [current-findings-summary-v2.md](./current-findings-summary-v2.md)
- [tsk-nearest-ladder-entry-to-anchor.md](./tsk-nearest-ladder-entry-to-anchor.md)
- [final-frame-role-map.md](./final-frame-role-map.md)
- [openpilot-control-side-working-note.md](./openpilot-control-side-working-note.md)
- [session-review-20260509-session3-bridge-tier-summary.md](./session-review-20260509-session3-bridge-tier-summary.md)

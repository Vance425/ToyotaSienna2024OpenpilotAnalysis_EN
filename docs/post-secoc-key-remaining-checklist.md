# Post-SecOC-Key Remaining Checklist

## Purpose

This checklist answers one question:

- after obtaining a `SecOCKey`, what still remains before `2024 Sienna` can be treated as a practical `C3X` implementation target?

## Remaining Work

### 1. Validate The Key Itself

- confirm the key is for the correct ECU / slot / protected path
- confirm it works under the intended ignition/runtime state

### 2. Close Freshness / Synchronization

- determine freshness behavior
- determine resync behavior
- determine failure and recovery behavior

### 3. Close MAC / Packing

- confirm covered bytes
- confirm truncation
- confirm packing order
- confirm `DataId` and framing assumptions

### 4. Confirm Minimum Protected Message Set

- determine what frames must be sent together
- determine timing/sequence assumptions
- determine whether steering acceptance depends on companion/context frames

### 5. Validate ECU Acceptance

- bounded acceptance run
- stable acceptance over time
- fault and recovery behavior

### 6. Integrate Into Repeatable Workflow

- stable startup sequence
- safe fallback sequence
- repeatable logging and diagnostics

## Bottom Line

A usable `SecOCKey` is a major milestone, but it is not the end of the implementation path.


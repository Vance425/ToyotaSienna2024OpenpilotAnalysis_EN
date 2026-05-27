# Implementation Next-Step Plan

## Purpose

This plan is for the current project phase, where lateral operation is treated as working but the secure/auth branch is not yet fully repeatable.

## Recommended Order

### 1. Stabilize The Direct Branch

Focus on:

- dump-only repeatability
- parser repeatability
- clean transcript capture

### 2. Make Key Export Repeatable

Do not treat a one-off success as enough.

Target:

- same workflow
- same target path
- repeatable result

### 3. Close Sync / Freshness

Collect and compare:

- success logs
- near-failure logs
- recovery logs

### 4. Close MAC / Packing

Confirm:

- framing assumptions
- truncation assumptions
- acceptance boundaries

### 5. Identify The Minimum Protected Message Set

Determine the smallest stable set that still preserves steering acceptance.

### 6. Build A Repeatable Bring-Up Procedure

Document:

- startup order
- required runtime state
- required diagnostics
- fault handling

## Logging Strategy At This Stage

Do not collect only generic exploratory CAN logs.

Prioritize:

- successful lateral runs
- long stable runs
- target-switch / lane-change / follow transitions
- runs that produce delayed or partial alarms rather than immediate startup failure


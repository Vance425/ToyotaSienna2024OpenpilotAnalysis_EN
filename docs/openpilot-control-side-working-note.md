# Openpilot Control-Side Working Note

## Purpose

This note captures the current replay-backed control-side interpretation in a compact implementation-facing form.

It is **not** an implementation-ready deployment note.

## Main Control-Side Anchor

The strongest control-side anchor remains:

- `0x260`

This is a control-side statement only.
It does not replace the passive backbone:

- `0x116`
- `0x131`
- `0x2E4`

## Strongest Replay-Backed Branch

The strongest replay-backed branch remains:

- `decode_mode = no_b1_flip`
- `mode = identity`
- `higher slew`

## What The Current Branch Explains Well

The current replay-backed branch already fits multiple sample classes reasonably well:

- `190101` anchor windows
- `171414` partial-ramp windows
- `184921` compact ramp windows
- `20260426` entry-burst pockets
- city active / late-stop / final hold classes

## City Transition / Settle Rule

The strongest current local working rule for city `transition / settle` remains:

- low-band catch-up `5.5x`
- deeper-negative helper `2.5x`
- gated only to the target sub-phase

## What This Is Good For

- replay-backed comparison
- control-side planning
- event interpretation
- narrowing implementation assumptions

## What This Still Does Not Prove

- final normalized mapping closure
- final slew closure
- full secure/auth closure
- final protected message-set acceptance


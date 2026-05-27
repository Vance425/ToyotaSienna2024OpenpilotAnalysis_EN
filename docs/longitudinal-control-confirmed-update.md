# Longitudinal Control Confirmed Update

## Status

At the current project level:

- `2024 Toyota Sienna` longitudinal operation with `C3X` is now treated as working in the field.

This is a meaningful milestone because it moves the longitudinal branch from:

- replay-backed interpretation

to:

- vehicle-confirmed controllability

## What This Confirms

- The earlier `0x260`-centric control-side interpretation was directionally correct.
- `0x260` remains the strongest current longitudinal/control anchor.
- ACC-active accel/decel behavior is still best read as a **multi-ID synchronized cluster**, not as one isolated brake or accel frame.
- The earlier replay-backed branch remains the strongest current implementation-facing interpretation:
  - `no_b1_flip + identity + higher slew`

## What This Does Not Automatically Prove

- That `SecOCKey` export is already repeatable
- That freshness / synchronization is fully closed
- That MAC / packing is fully closed
- That the final minimum protected message set is already fixed
- That the current control mapping is deployment-final

## Practical Meaning

The longitudinal branch should now be read in two layers:

1. **Field-confirmed outcome**
   - longitudinal control can work on `2024 Toyota Sienna`
2. **Still-open implementation closure**
   - repeatability
   - secure/auth stability
   - final message-set acceptance
   - stable fault handling and recovery

## Related References

- [Virtual TSK Spec v2](./VIRTUAL_TSK_SPEC_v2.md)
- [Openpilot Control-Side Working Note](./openpilot-control-side-working-note.md)
- [Current Findings Summary](./current-findings-summary-v2.md)
- [Post-SecOC-Key Remaining Checklist](./post-secoc-key-remaining-checklist.md)

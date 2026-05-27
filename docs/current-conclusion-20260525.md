# Current Conclusion: 2026-05-25

## Bottom Line

The Toyota Sienna project has moved past the question of whether a meaningful protected path exists.

At the current project level:

- `TSK` is treated as confirmed
- `2024 Toyota Sienna` lateral operation with `C3X` is treated as working
- `2024 Toyota Sienna` longitudinal operation with `C3X` is treated as working

## What We Can Say Confidently

- `0x116 / 0x131 / 0x2E4` is the strongest passive lifecycle backbone.
- `0x260` is the strongest control-side anchor.
- Vehicle-confirmed longitudinal controllability now aligns with the earlier `0x260`-centric control-side reading.
- `20260312_190101_000` remains the strongest joined-lifecycle anchor.
- `20260509 Session 3` is now a meaningful bridge-tier route candidate.
- Steering-side SecOC validation is strong enough to treat the steering protected path as real, not hypothetical.

## What We Still Cannot Claim

- That passive bridge-gap closure is complete
- That direct `SecOCKey` export is repeatable
- That freshness / synchronization is fully closed
- That MAC / packing is fully closed
- That the minimum protected message set is fully accepted under a repeatable workflow

## Practical Meaning

The project is now in an implementation-transition phase:

- not blocked on pure passive discovery
- still blocked on secure/auth repeatability and stable implementation mechanics

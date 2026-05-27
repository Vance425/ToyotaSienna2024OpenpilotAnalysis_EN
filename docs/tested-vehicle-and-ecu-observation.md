# Tested Vehicle And ECU Observation

## Tested Vehicle Scope

This public note records the non-sensitive vehicle-side identification details that matter for the current `2024 Toyota Sienna` protected-control research.

## Vehicle Level

- Make: `Toyota`
- Model: `Sienna`
- Model Year: `2024`
- Platform label in the software context:
  - `TOYOTA_SIENNA_4TH_GEN`

## ECU Identification Observation

From the direct-branch diagnostic transcript, the currently relevant EPS-side identification reads as:

- application-side `APPLICATION_SOFTWARE_IDENTIFICATION`:
  - `8965B4514000`
- bootloader-side `APPLICATION_SOFTWARE_IDENTIFICATION` response:
  - `\x02!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!`

## Practical Interpretation

The important point is that the bootloader-side response should **not** be read as a normal human-readable version string.

It is better read as:

- a bootloader-side identification response was reached
- but the returned content appears filler-like or low-information
- so it is useful as a target fingerprint, not as a rich semantic version label

## Why This Matters

This helps pin the tested target more precisely when reading:

- direct-branch transcripts
- extract-keys failure analysis
- profile-specific modification notes

## Related References

- [Extract-Keys Failure Layer Analysis (2024 Sienna)](./extract-keys-failure-layer-analysis-2024-sienna.md)
- [LKAS Context Quick Read 2026-05-08](./lkas-context-quick-read-20260508.md)

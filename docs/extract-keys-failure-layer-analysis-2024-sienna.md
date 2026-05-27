# 2024 Sienna Extract-Keys Failure Layer Analysis

## Main Question

Why did the old `extract_keys` path appear to progress deeply into diagnostics and payload upload, but still fail to produce a usable `SecOCKey` on `2024 Sienna`?

## Main Conclusion

The strongest current reading is:

- the failure does **not** look like an earliest-layer UDS or `SecurityAccess` rejection
- it looks much more like a problem at:
  - dump range
  - memory layout
  - parser assumptions

## What Appeared To Succeed

- target ECU responded
- application-side identification returned:
  - `8965B4514000`
- bootloader-side identification returned:
  - `\x02!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!`
- session switching progressed
- `SecurityAccess` returned success
- payload upload progressed
- dump activity began

## What Still Failed

- extracted structures did not validate as the expected key layout
- parser output collapsed to zero-like results
- checksum validation failed

## Correct Reading

This should **not** be read as proof that the vehicle has no key.

It is better read as:

- old layout assumptions no longer match `2024 Sienna`
- old parser offsets likely no longer describe the real structure
- the bootloader response is reachable, but the returned bootloader identification content is filler-like rather than a normal version string

## Practical Implication

If the direct branch is reopened, the first priorities are:

1. verify the dump range
2. verify the structure layout
3. verify the payload is reading the intended memory region
4. verify the parser model

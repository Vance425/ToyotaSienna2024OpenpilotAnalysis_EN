# Public References Map

## Purpose

This map organizes the most relevant public references around the current project.

The goal is not to claim that public material already solves the `2022 Sienna` problem.

Instead, this page answers:

- what public material is closest to direct `TSK` extraction
- what public material helps with `SecOC` structure
- what public material reflects Toyota / openpilot community reality
- what public material is useful for generic CAN reverse engineering methodology

---

## Quick Summary

Public references fall into four buckets:

1. **Direct TSK / SecOC key extraction**
2. **SecOC structure and protocol reference**
3. **Toyota / openpilot / TSK community context**
4. **General CAN reverse engineering methodology**

The most important limitation is:

- there is no public reference that already reproduces the current project's
  - `0x116 / 0x131 / 0x2E4` protected-lifecycle interpretation
  - `TSK-nearest` ladder
  - bridge-state capture logic

So public references are best used as:

- comparison material
- architecture guidance
- risk framing
- and reality checks

not as a drop-in solution.

---

## 1. Direct TSK / SecOC Key Extraction

These are the closest public references to the final end-goal of actually obtaining a SecOC signing key.

### A. I CAN Hack: Extracting SecOC keys from a 2021 Toyota RAV4 Prime

Link:

- [I CAN Hack: Extracting Secure Onboard Communication (SecOC) keys from a 2021 Toyota RAV4 Prime](https://icanhack.nl/blog/secoc-key-extraction/)

Why it matters:

- closest public write-up to actual Toyota SecOC key extraction
- uses EPS as the target ECU
- shows the path through:
  - firmware extraction
  - bootloader reverse engineering
  - shellcode upload
  - RAM key extraction

How to use it:

- treat it as the strongest public example of a **direct branch**
- use it to understand what a real direct extraction path looks like
- do **not** assume the exact exploit path still applies to the current vehicle

### B. hardwear.io talk: My car, My keys

Link:

- [hardwear.io: My car, My keys: obtaining CAN bus SecOC signing keys](https://hardwear.io/my-car-my-keys-obtaining-can-bus-secoc-signing-keys/)

Why it matters:

- concise public summary of the same research direction
- clearly frames the problem as:
  - ECU security
  - bootloader / update path weakness
  - not just “decode the CAN log”

How to use it:

- good for explaining to collaborators why passive log work and direct extraction are different tasks

### C. Hackaday summary

Link:

- [Hackaday: Extracting SecOC Keys From A 2021 Toyota RAV4 Prime](https://hackaday.com/2024/03/08/extracting-secoc-keys-from-a-2021-toyota-rav4-prime/)

Why it matters:

- less technical than the original write-up
- useful as a short overview for non-specialists

How to use it:

- only as a readable summary
- not as a primary technical source

---

## 2. SecOC Structure And Protocol Reference

These do not give Toyota-specific keys, but they are useful for understanding what protected communication is supposed to look like.

### A. AUTOSAR SecOC specification

Link:

- [AUTOSAR CP SWS Secure Onboard Communication (R24-11)](https://www.autosar.org/fileadmin/standards/R24-11/CP/AUTOSAR_CP_SWS_SecureOnboardCommunication.pdf)

Why it matters:

- canonical structural reference for:
  - secured I-PDUs
  - authenticators
  - freshness values
  - verification behavior
  - security profiles

Most useful sections:

- functional overview
- data covered by authenticator
- freshness value handling
- verification / authentication
- security profiles

How to use it:

- compare the idea of:
  - rolling / freshness-bearing fields
  - auth-heavy tail structure
  - verification context
- against project observations such as:
  - `0x116` protected tail
  - `0x131 / 0x116` lifecycle
  - `0x2E4` protected-family side activity

Important caveat:

- this explains the **standard**
- it does not explain Toyota’s concrete implementation details or its actual `TSK`

### B. SecOC implementation explainer articles

Example:

- [SecOC in AUTOSAR: Secure Vehicle Communication Explained](https://www.altenpolska.pl/en/2025/07/28/secure-onboard-communication-secoc-in-autosar-architecture-and-practical-implementation/)

Why it matters:

- easier than reading full AUTOSAR specs
- useful for onboarding collaborators

How to use it:

- secondary explanation only
- rely on AUTOSAR spec first when precision matters

---

## 3. Toyota / openpilot / TSK Community Context

These sources do not usually contain formal technical proofs, but they are useful for real-world context.

### A. optskug/docs

Link:

- [optskug/docs](https://github.com/optskug/docs)

Why it matters:

- best public community-facing documentation on Toyota/Lexus/Subaru `TSK` / `SecOC`
- contains:
  - vehicle lists
  - extraction/install guidance
  - community history
  - openpilot-related practical notes

How to use it:

- reality-check whether a car line is considered `TSK` / `SecOC`
- compare community expectations against project findings

Important caveat:

- this is community documentation, not a formal reverse engineering proof set

### B. openpilot issue about missing SecOC key on Toyota Sienna

Link:

- [commaai/openpilot issue #34012](https://github.com/commaai/openpilot/issues/34012)

Why it matters:

- directly relevant to `2022 Sienna Hybrid`
- confirms that missing SecOC key behavior is a real community issue on this platform

How to use it:

- as supporting context that the vehicle line is genuinely security-key relevant
- not as evidence for any specific field interpretation

### C. comma / openpilot docs and car support pages

Links:

- [openpilot docs](https://docs.comma.ai/)
- [comma openpilot page](https://comma.ai/openpilot)

Why they matter:

- good for general product/support context
- useful to explain why SecOC matters for steering integration

How to use them:

- context only
- not as deep reverse engineering references

---

## 4. General CAN Reverse Engineering Methodology

These are useful for methods, not Toyota-specific answers.

### A. Online reverse engineering of CAN data

Link:

- [ScienceDirect: Online reverse engineering of CAN data](https://www.sciencedirect.com/science/article/pii/S2542660520300652)

Why it matters:

- strong methodological reference for:
  - signal discovery
  - correlation
  - continuous vs discrete signals
  - reducing search space

How to use it:

- compare against the project’s own:
  - field ranking
  - signal scoring
  - correlation-based local window analysis

### B. CAN reverse engineering surveys

Example:

- [PMC survey with CAN reverse engineering work table](https://pmc.ncbi.nlm.nih.gov/articles/PMC10802965/)

Why it matters:

- helps place the project’s methods into the wider literature
- useful when explaining that:
  - tokenization
  - endianness handling
  - interpretation
  are separate stages

How to use it:

- literature context only
- not for Toyota-specific inference

### C. Practical reverse engineering guides

Example:

- [CSS Electronics CAN reverse engineering overview](https://www.csselectronics.com/pages/can-bus-sniffer-reverse-engineering)

Why it matters:

- accessible explanation for practical tooling and workflow

How to use it:

- onboarding / practical explanation
- not as a substitute for deeper research

---

## What Is Most Similar To The Current Project

### Closest to the project’s end-goal

- [I CAN Hack SecOC extraction](https://icanhack.nl/blog/secoc-key-extraction/)

because it is the clearest public example of actually obtaining a Toyota SecOC-related key.

### Closest to the project’s passive structure work

- [AUTOSAR SecOC specification](https://www.autosar.org/fileadmin/standards/R24-11/CP/AUTOSAR_CP_SWS_SecureOnboardCommunication.pdf)

because it helps explain:

- freshness-like structure
- auth-bearing tail design
- verification context

### Closest to community reality on Toyota TSK cars

- [optskug/docs](https://github.com/optskug/docs)
- [commaai/openpilot issue #34012](https://github.com/commaai/openpilot/issues/34012)

because they show how these problems appear in practice on real Toyota platforms and forks.

---

## What Public Sources Still Do Not Give Us

No public source currently gives us a ready-made answer for:

- the project’s `0x116 / 0x131 / 0x2E4` protected-lifecycle interpretation
- the `TSK-nearest` ladder
- the bridge-state gap between:
  - `171414_000`
  - and `190101_000`
- the regime-first Toyota-specific distinction between:
  - city control behavior
  - seed-heavy protected-lifecycle progression
  - top-tier joined lifecycle anchor behavior

That part is still project-specific and derived from our own samples.

---

## Recommended Reading Order

If someone is joining the project and wants the shortest useful public reading sequence:

1. [I CAN Hack SecOC extraction](https://icanhack.nl/blog/secoc-key-extraction/)
2. [AUTOSAR SecOC specification](https://www.autosar.org/fileadmin/standards/R24-11/CP/AUTOSAR_CP_SWS_SecureOnboardCommunication.pdf)
3. [optskug/docs](https://github.com/optskug/docs)
4. [openpilot issue #34012](https://github.com/commaai/openpilot/issues/34012)
5. [ScienceDirect CAN reverse engineering paper](https://www.sciencedirect.com/science/article/pii/S2542660520300652)

---

## Bottom Line

Public references are useful here, but they divide cleanly into:

- direct extraction references
- protocol structure references
- community context references
- generic reverse engineering method references

They help frame the problem and validate that the project direction is real.

But they do **not** replace the project’s own Toyota-specific passive `TSK-nearest` model.

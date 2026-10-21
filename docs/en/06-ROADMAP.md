# Roadmap and gaps

This document records work that is **not** claimed complete. Its purpose is to prevent Phase 1 from being read as completion of the entire roadmap.

## 1. Current position

| Area | Status | Note |
|---|---|---|
| Five MIT module adoptions | Complete | Optional tree, contracts and tests pass |
| `re-code` pilot | Complete | Contracts and tests pass |
| `web-pentest` merge | Complete | Evidence-led merge |
| `red-ctf` load path | Complete | Discovered and read through `external_dirs` |
| `red-ctf` end-to-end solve | Not yet | Requires a sandbox and explicit scope |
| `red-reverse` Phase 2 | Not yet | 12 additional references |
| Wave 2/3 | Not yet | Core skills that are not yet modularized |
| Branding sweep | Not yet | Locale, docs, desktop |
| Old log archive | Not yet | Internal location `[Redacted 0xnhsec]` |

## 2. Gaps and exit criteria

### 2.1 `red-ctf` end-to-end

**Gap:** load-path proof only proves that the module can be discovered and read.

**Exit criteria:**

- one CTF challenge is run in a sandbox;
- scope and authorization are recorded;
- solve steps are reproducible;
- results and limitations are captured as evidence;
- no capability claim is made beyond the tested challenge.

**Status:** open.

### 2.2 `red-reverse` Phase 2

**Gap:** Phase 1 does not cover the entire reverse-engineering domain.

**Coverage not yet included:**

- macOS and Mach-O;
- JavaScript and web runtimes;
- DSL/VM;
- protocol reverse engineering;
- thick clients;
- browser extensions;
- dynamic analysis and anti-analysis;
- language-specific deep dives.

**Exit criteria:**

- new references are added and routed from `SKILL.md`;
- module contracts and tests are updated;
- discovery and reference reads are verified;
- missing coverage remains explicitly open.

**Status:** open.

### 2.3 Wave 2/3

**Gap:** the six Phase 1 modules do not replace the entire source catalog.

**Exit criteria:**

- core skills that are not yet modularized are mapped;
- every module follows the same authoring contract;
- there is no semantic duplication;
- contract tests and invariants pass;
- the prompt index is re-measured;
- adoption status is updated in the internal manifest and public documents.

**Status:** open.

### 2.4 Branding sweep

**Gap:** legacy branding remains in locale files, documentation, and desktop surfaces.

**Exit criteria:**

- legacy terms do not appear on public surfaces;
- locale and documentation are consistent;
- desktop builds are checked;
- no functional regressions occur.

**Status:** open.

### 2.5 Old log archive

**Gap:** some old runtime logs remain in a temporary internal location `[Redacted 0xnhsec]`.

**Exit criteria:**

- logs still required are moved to the evidence store;
- logs no longer required are deleted according to the retention policy;
- evidence checksums are updated;
- public documents do not reference temporary paths.

**Status:** open.

## 3. Priorities

| Priority | Work | Reason |
|---:|---|---|
| P1 | `red-ctf` end-to-end | Closes the capability gap most likely to be misunderstood |
| P1 | `red-reverse` Phase 2 | Completes the missing domain coverage |
| P2 | Wave 2/3 | Expands coverage without repeating authoring mistakes |
| P2 | Branding sweep | Product and documentation consistency |
| P3 | Old log archive | Housekeeping and retention |

## 4. Non-goals

- Adopting all 128 skills at once.
- Copying `red-ctf` into the MIT tree.
- Activating offensive modules in the default profile.
- Claiming solve capability without end-to-end testing.
- Publishing payloads, raw logs, or artifact checksums.
- Treating public documentation as a distribution package.

## 5. Roadmap update rules

1. Status changes only when new evidence exists.
2. Completed gaps move to the status section with a date.
3. New gaps must have exit criteria.
4. Public documents must not contain unapproved internal target dates.
5. If evidence is withdrawn, the status must return to open.

## 6. One-sentence summary

Phase 1 is sufficient as an opt-in foundation, but not sufficient to claim full coverage, end-to-end CTF capability, or completion of the entire roadmap.

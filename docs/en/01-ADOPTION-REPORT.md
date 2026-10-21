# Adoption report: red-team modules in SNXX

> **Document:** Phase 1 main report
> **Project:** `RTA-SNXX-20261020` — *Red Team Agent — SNXX — 20 October 2026*
> **Date:** 21 October 2026
> **Status:** complete for the Phase 1 adoption scope; functional gaps are tracked in the [roadmap](06-ROADMAP.md)
> **Classification:** sanitized public edition
> **Version:** 1.0

## 1. Executive summary

Phase 1 consolidated security skills from four source repositories into six modules that are easier to select, audit, and operate in SNXX. Five MIT-licensed modules were adopted into the `optional-skills/` tree, the `re-code` pilot and `web-pentest` merge were verified through the same path, and `red-ctf` was separated into a GPL-3.0 package outside the MIT tree.

The main result is not merely a larger skill count. The important changes are a consistent authoring contract, explicit license separation, an opt-in installation path, and reproducible verification evidence. The default profile remains clean: 54 skills enabled and no automatically installed `red-*` modules.

Phase 1 verification shows **1888 passed, 1 skipped** in the skill suite, **90/90** adoption contracts, **12/12** opt-out invariants, **90/90** module tests, and a clean lint run. The single skip is a Windows-only test running on a Linux host.

This report does not claim that all 128 source skills have been adopted. The six Phase 1 modules consolidate 88 skills from `reverse-skill`; the other 40 remain out of scope. `red-reverse` is still at Phase 1, and `red-ctf` has only been proven discoverable and readable, not capable of solving a challenge end-to-end.

## 2. Scope and authorization

### 2.1 In scope

- Official scope and claim boundaries: [00-SCOPE.md](00-SCOPE.md).
- Inventory and classification of skills from four source repositories.
- Domain consolidation into modules selected opt-in.
- Frontmatter, trigger, prerequisite, tool mapping, and reference routing contracts.
- Separation of MIT and GPL-3.0 licensing.
- Verification of contracts, invariants, discovery, `skill_view`, and reference reads.
- Sanitized public documentation.

### 2.2 Out of scope

- Redistributing skill source or operational packages in this repository.
- Testing against a target without a written scope.
- Performance claims or real-target completion claims.
- Publishing raw logs, scanner finding details, or internal artifacts.
- Modules not included in Phase 1.

### 2.3 Publication boundary

This document is the **public edition**. Information not required to understand the architecture decisions and verification results is replaced with `[Redacted 0xnhsec]`. Category details are in the [publication policy](05-PUBLICATION.md).

## 3. Problem and decisions

The four source repositories differ in authoring style, language, license, and depth. Copying everything at once would produce a crowded, overlapping, and hard-to-audit catalog. The decisions were:

| Decision | Reason | Consequence |
|---|---|---|
| Consolidate by domain | Reduce overlap and routing cost | Some source skills are merged into one module |
| Place five MIT modules in the tree | Core modules can be installed through the official tier | Offensive modules remain opt-in |
| Separate `red-ctf` | GPL-3.0 differs from the MIT tree | Needs its own package and `external_dirs` path |
| Use `re-code` as a pilot | Test a single, deep skill | Not every skill needs consolidation |
| Merge `web-pentest` | Avoid duplication with an existing skill | Change is evidence-led, not copy-paste |
| Keep the default profile clean | Reduce accidental activation risk | Operators must explicitly select modules |

The principle is **incremental adoption, not total migration**. Modules that are not mature remain on the roadmap and are not claimed complete.

## 4. Adoption architecture

High-level flow:

```text
Source repositories
    -> inventory and classification
    -> domain modules
    -> authoring contract
    -> policy review
    -> opt-in install in a temporary profile
    -> verification and evidence
    -> sanitized publication
```

Layer details, trust tiers, and license boundaries are explained in [architecture](03-ARCHITECTURE.md). Workflow diagrams are in [workflow](02-WORKFLOW.md) and the raw Mermaid files are in [`diagrams/`](diagrams/).

## 5. Adoption results

### 5.1 Phase 1 catalog

| Module | License | Focus | References | Status |
|---|---|---|---:|---|
| `red-reverse` | MIT | Binary, firmware, and native-code reverse engineering | 12 | Adopted |
| `red-offensive` | MIT | AD/identity, cloud, exploit, evasion, attack chain | 8 | Adopted; explicit opt-in required |
| `red-web` | MIT | Web/API, AppSec, code audit, database, LLM, supply chain | 7 | Adopted; explicit opt-in required |
| `red-forensics` | MIT | DFIR, malware, threat hunting, threat intelligence | 5 | Adopted |
| `red-hardware` | MIT | Mobile, firmware, hardware, OT/ICS, RF, Wi-Fi | 7 | Adopted |
| `re-code` | MIT | Focused reverse engineering and evidence workflow | 15 | Pilot; adopted |
| `web-pentest` | MIT | Existing web pentest, enriched by the merge | 17 + taxonomy cards | Merge; adopted |
| `red-ctf` | GPL-3.0 | CTF/AWD orchestration and domain children | 10 | Separate package; not in the MIT tree |

The six core modules (five MIT modules + `red-ctf`) contain 49 references in total. `re-code` and `web-pentest` are pilot entries following the same contract, not additional modules from `reverse-skill`.

### 5.2 What was adopted into the tree

Five MIT modules and two pilots were added under `optional-skills/security/` in the appropriate categories. These modules:

- have short descriptions that do not collide with the SNXX skill index;
- place triggers in the body rather than relying on fields the runtime does not read;
- declare prerequisites and tool mappings;
- route all references from `SKILL.md`;
- include an opt-out example that names the module itself;
- have contract tests.

### 5.3 `red-ctf` as a separate package

`red-ctf` was not copied into the MIT tree. It is packaged separately with a GPL-3.0 `LICENSE` and tested through `external_dirs`. The proven result is a **load-path proof**: the module is discovered by `skills list`, `SKILL.md` can be read, and the orchestrator reference can be opened.

What is **not** proven is the ability to solve a CTF challenge end-to-end. Load-path proof is not solve proof.

### 5.4 What was not adopted

- All 128 source skills: no.
- All 88 `reverse-skill` skills: not yet; Phase 1 only consolidates the main domains.
- Common/engineering skills outside red-team: not part of Phase 1.
- Modules that still require third-party tool dependencies: prerequisites are recorded, but tools are not installed automatically.

## 6. Verification summary

| Check | Result | Note |
|---|---:|---|
| Skill suite | 1888 passed, 1 skipped | Skip is a Windows-only test on a Linux host |
| Adoption contracts | 90/90 passed | Five red modules, `re-code`, `web-pentest` |
| Opt-out invariants | 12/12 passed | `skills.disabled` examples and pre-adoption prose guard |
| Module tests | 90/90 passed | Module authoring and structure tests |
| Lint | Clean | No new dependencies written to the repository |
| Opt-in install | Allowed | Performed in a temporary profile, not the default |
| Default profile | 54 enabled | No `red-*` |
| Provenance headers | 39 adopted, 0 staging | Source modules synchronized with the adopted tree |
| `red-ctf` in MIT tree | 0 files | Separate GPL package |

The verification model and evidence boundaries are detailed in [verification](04-VERIFICATION.md).

## 7. Evidence -> Finding -> Path

### 7.1 Scope summary

- **Work type:** skill adoption and architecture documentation.
- **Target:** SNXX skill tree and RedWolf modules.
- **Authorization:** changes only to skills, documentation, tests, and supporting packages; the core runtime was not modified.
- **Boundary:** no engagement against an external target.

### 7.2 Evidence

| ID | Source reference | Summary | Integrity |
|---|---|---|---|
| E-01 | Internal inventory, `[Redacted 0xnhsec]` | Four source repositories, 128 unique skills, 129 `SKILL.md` files | Hash `[Redacted 0xnhsec]` |
| E-02 | Internal contract tests, `[Redacted 0xnhsec]` | 90/90 adoption contracts passed | Hash `[Redacted 0xnhsec]` |
| E-03 | Internal skill suite, `[Redacted 0xnhsec]` | 1888 passed, 1 skipped | Hash `[Redacted 0xnhsec]` |
| E-04 | Internal module tests, `[Redacted 0xnhsec]` | 90/90 module tests passed | Hash `[Redacted 0xnhsec]` |
| E-05 | Internal policy and install run, `[Redacted 0xnhsec]` | Opt-in installation allowed in a temporary profile | Hash `[Redacted 0xnhsec]` |
| E-06 | `red-ctf` load path, `[Redacted 0xnhsec]` | `skills list` and `skill_view` succeeded | Hash `[Redacted 0xnhsec]` |
| E-07 | Header and prose audit, `[Redacted 0xnhsec]` | 39 adopted headers, 0 staging, 0 pre-adoption phrases | Hash `[Redacted 0xnhsec]` |

### 7.3 Findings

| ID | Severity | Evidence | Confidence | Location | Status |
|---|---|---|---|---|---|
| F-01 | `n/a_re` | E-01, E-02, E-03 | High | `optional-skills/security/` tree | Closed |
| F-02 | `n/a_re` | E-01, E-05 | High | MIT/GPL license boundary | Closed |
| F-03 | `n/a_re` | E-05 | High | Default profile and opt-in path | Closed |
| F-04 | Medium | E-01, E-06 | High | `red-ctf` and Phase 2 coverage | Open |
| F-05 | `n/a_re` | E-07 | High | Documentation and source modules | Closed |

**F-01 — Phase 1 adoption succeeded.** Five MIT modules, `re-code`, and `web-pentest` are in the correct tree and pass their contracts.

**F-02 — License separation succeeded.** No `red-ctf` files exist in the MIT tree; the GPL package has its own distribution path.

**F-03 — Safe default.** Offensive modules are not active automatically; the default profile remains at 54 skills with no `red-*`.

**F-04 — Functional gaps remain open.** `red-ctf` has not been tested for end-to-end solving; `red-reverse` is still Phase 1; Wave 2/3 is not complete.

**F-05 — Documentation is consistent.** Pre-adoption prose and staging headers were cleaned up, including source-module synchronization.

### 7.4 Path

| ID | Path type | Steps | Evidence |
|---|---|---|---|
| P-01 | `callflow` | Inventory -> classification -> consolidation -> contract -> policy -> install -> verification -> publication | E-01..E-05, E-07 |
| P-02 | `callflow` | GPL package -> `external_dirs` -> `skills list` -> `skill_view` -> reference | E-06 |
| P-03 | `callflow` | Operator selects module -> in-scope task -> evidence -> disable/rollback | E-05 |

There is no `path_type=attack` in this report because the documented work is adoption and verification, not an offensive engagement against a target.

## 8. Timeline

| Date | Event |
|---|---|
| 2026-10-20/21 | Source inventory and initial mapping of 128 skills |
| 2026-10-21 | Consolidation of six modules and contract authoring |
| 2026-10-21 | Cleanup of pre-adoption prose, opt-out examples, manifest, and headers |
| 2026-10-21 | Contract, invariant, and skill-suite verification |
| 2026-10-21 | Opt-in installation in a temporary profile |
| 2026-10-21 | `red-ctf` separation as a GPL package and load-path proof |
| 2026-10-21 | Source-module synchronization and final audit |
| 2026-10-21 | Sanitized documentation publication |

## 9. Risks, claim boundaries, and gaps

### 9.1 Claim boundaries

Allowed claims:

- Seven skill entries are in the `optional-skills/` tree: five MIT modules, `re-code`, and the `web-pentest` merge.
- Adoption contracts, opt-out invariants, skill suite, and module tests pass.
- The official path allows high-risk module installation in a controlled environment.
- The default profile contains no `red-*` modules.
- `red-ctf` is not in the MIT tree and can be loaded through `external_dirs`.
- Public documentation has been sanitized.

Claims that must not be made:

- All 128 skills have been adopted.
- `red-ctf` can already solve a CTF challenge end-to-end.
- `red-reverse` is complete.
- The entire RedWolf roadmap is finished.
- This public documentation is an operational package distribution.

### 9.2 Main risks

| Risk | Impact | Mitigation |
|---|---|---|
| Offensive module activation without scope | Misuse or action beyond authorization | Opt-in, scope gate, disable/rollback |
| License mixing | Distribution and compliance issues | Separate MIT tree and GPL package |
| Overclaiming | Loss of public trust | Explicit claim boundaries and evidence chain |
| Internal data leakage | Operational and privacy risk | `[Redacted 0xnhsec]` redaction and publication review |
| Phase 2 gap treated as complete | Wrong expectations | Roadmap with exit criteria |

## 10. Recommendations

1. Test `red-ctf` against one CTF challenge in a sandbox before claiming solve capability.
2. Continue `red-reverse` Phase 2 with the remaining references.
3. Run Wave 2/3 with the same contracts and tests.
4. Keep the default profile clean and use `skills.disabled` for opt-out.
5. Update public documents only after internal evidence changes and checksums are verified.
6. Do not publish raw logs, payloads, local paths, or artifact checksums.

## 11. References

- [Workflow](02-WORKFLOW.md)
- [Architecture](03-ARCHITECTURE.md)
- [Verification](04-VERIFICATION.md)
- [Publication and redaction](05-PUBLICATION.md)
- [Roadmap](06-ROADMAP.md)
- [Mermaid diagrams](diagrams/)
- This repository's `LICENSE`

## 12. Glossary

| Term | Meaning |
|---|---|
| **Adopted** | Module is in the SNXX tree and has a contract |
| **Opt-in** | Module is inactive until the operator selects it |
| **Official tier** | Trusted distribution path with `builtin` trust |
| **Project tier** | Stricter project path; not used for offensive modules |
| **Load-path proof** | Proof that a module is discovered and readable, not proof of solve capability |
| **Evidence chain** | E -> F -> P chain connecting evidence, findings, and paths |
| **Phase 1** | Initial adoption scope; not the entire roadmap |

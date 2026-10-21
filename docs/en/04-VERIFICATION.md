# Verification and evidence

This document summarizes the Phase 1 verification model and the results that may be published. Raw logs, internal commands, absolute paths, and artifact checksums are kept private and replaced with `[Redacted 0xnhsec]` in this edition.

## 1. Verification model

Verification does not stop at "the file installed successfully". There are five layers of checks:

| Layer | Question | Expected evidence |
|---|---|---|
| Structure | Are `SKILL.md` and its references complete? | Structure and routing inspection |
| Contract | Do frontmatter, triggers, prerequisites, and tool mapping comply? | Per-module contract tests |
| Policy | May the module be installed on the chosen tier? | Verdict and policy decision |
| Runtime | Is the module discovered, read, and its references accessible? | `skills list` and `skill_view` |
| Integrity | Is the evidence consistent and unchanged? | Checksums and re-audit |

## 2. Summary results

| Check | Result | Interpretation |
|---|---:|---|
| Skill suite | 1888 passed, 1 skipped | No failures |
| Adoption contracts | 90/90 passed | Seven contract entries satisfied |
| Opt-out invariants | 12/12 passed | Disable examples and pre-adoption prose guard |
| Module tests | 90/90 passed | Module structure and authoring |
| Lint | Clean | No new dependencies |
| Opt-in install | Allowed | Temporary profile only |
| Default profile | 54 enabled | No `red-*` |
| `red-ctf` in MIT tree | 0 files | License separation preserved |

The single skip in the skill suite is a Windows-only contract test running on a Linux host. The skip is not a module failure.

## 3. Test coverage

### 3.1 Adoption contracts

The contracts cover:

- short descriptions that do not collide with the index;
- body-level triggers;
- prerequisites and tool mapping;
- reference routing from `SKILL.md`;
- an opt-out example that names the module itself;
- license and provenance metadata.

### 3.2 Opt-out invariants

The invariants check two easy-to-regress conditions:

1. The `skills.disabled` example must name the correct module.
2. `SKILL.md` must not contain pre-adoption prose.

These invariants make the text cleanup durable rather than a one-time fix.

### 3.3 Module tests

Module tests check structure, references, and the authoring contract. They complement the main skill suite rather than replacing it.

## 4. Runtime verification

### 4.1 MIT modules

MIT modules are verified through:

1. Installation in a temporary profile.
2. `skills list` to confirm the module appears.
3. `skill_view` to read `SKILL.md`.
4. Reading the main reference.
5. Confirming the default profile is unchanged.

### 4.2 `red-ctf` GPL

`red-ctf` is verified as a separate package through `external_dirs`:

- the module is discovered as external/local;
- `SKILL.md` can be read;
- the orchestrator reference can be read;
- the package does not appear in the `optional-skills/` tree;
- no solve claim is made.

Load-path proof answers "can the module be loaded and read?". It does not answer "can the module solve a challenge?".

## 5. Policy and installation

| Check | Public result |
|---|---|
| Policy review | Complete |
| Scanner finding details | `[Redacted 0xnhsec]` |
| Per-module verdict | Summarized as a risk class, not finding details |
| Official install | Allowed for modules that pass the gate |
| Project-tier install | Not used for offensive modules |
| Default profile | Unchanged |

Offensive modules still require explicit opt-in. A successful install does not mean the module may be activated for normal engagements.

## 6. Evidence integrity

Internal evidence includes:

- suite and contract results;
- module test results;
- prose and header audits;
- installation status in a temporary profile;
- default-profile status;
- `red-ctf` load path;
- checksums for the evidence folders.

For the public edition:

- counts and result summaries may be shown;
- raw logs are not shown;
- absolute paths and hostnames are replaced;
- artifact checksums are replaced with `[Redacted 0xnhsec]`;
- scanner finding details are not shown.

## 7. Evidence boundaries

This verification proves:

- adopted modules are in the correct tree;
- contracts and invariants pass;
- opt-in installation succeeds;
- modules can be discovered and read;
- license boundaries are not violated;
- the default profile remains clean.

This verification does **not** prove:

- all 128 skills have been adopted;
- `red-ctf` can solve a challenge;
- `red-reverse` is complete;
- modules are free from all operational risk;
- performance or result quality on real targets.

## 8. Re-audit

A re-audit follows this order:

1. Check internal evidence checksums.
2. Run the suite and contracts in an isolated environment.
3. Verify the default-profile state.
4. Verify the GPL module load path.
5. Re-check public documents against the redaction rules.
6. Update the [roadmap](06-ROADMAP.md) if status changes.

If any step fails, the "complete" status in public documents must be withdrawn until new evidence is available.

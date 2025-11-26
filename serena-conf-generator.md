# SERENA-GENERATOR.md

## Purpose

This file defines **how a coding LLM must generate `.serena/project.yml`** for this repository.

It is strictly responsible for **Serena project configuration only**.

It MUST NOT generate `AGENTS.md` or describe business logic.

All rules are mandatory.

---

## Output File

The generator MUST produce exactly one file:

* `.serena/project.yml`

Any additional files or edits are INVALID.

---

## Mandatory Generation Order

The LLM MUST follow this order:

1. Resolve repository root directory name (filesystem).
2. Detect language(s) using definitive marker files only.
3. Apply proof-based ignored path rules.
4. Emit `.serena/project.yml` following the exact schema.
5. Run the failure checklist.

---

## Project Name Resolution (Strict)

* `project.name` MUST equal the repository root folder name
* Case, hyphens, prefixes, suffixes MUST be preserved
* Normalization or renaming is FORBIDDEN

Failure = INVALID generation.

---

## Language Detection (Proof-Based Only)

Language detection affects **ignored paths only**.

A language is detected ONLY if a definitive marker file exists at repository root.

### Definitive marker files

* Node / TypeScript / JavaScript

  * `package.json`
  * `tsconfig.json`

* Go

  * `go.mod`

* Java / JVM

  * `pom.xml`
  * `build.gradle`
  * `build.gradle.kts`

* Python

  * `pyproject.toml`
  * `requirements.txt`

* Rust

  * `Cargo.toml`

DO NOT infer language from any other signal.

---

## Pre-YAML Language Proof Gate (MANDATORY)

Before emitting `.serena/project.yml`, the LLM MUST answer:

> "Which definitive marker file proves this language-specific ignored path?"

If no answer exists:

* the language is NOT considered detected
* the ignored path MUST NOT be emitted

Missing ignores are acceptable. Wrong ignores are NOT.

---

## `.serena/project.yml` Schema (STRICT)

### Allowed top-level keys ONLY

* `project`
* `language_server`
* `indexing`
* `permissions`
* `tools`
* `ignored_paths`

Any other key (e.g., `ignore`, `exclude`) is INVALID.

---

## Base Configuration (Always Included)

```yml
project:
  name: <repo-root-name>

language_server:
  enabled: true

indexing:
  enabled: true
  ignore_gitignore: true

permissions:
  read_only: false
```

---

## Ignored Paths Rules

### Base ignored paths (ALWAYS include)

```
.git
build
dist
out
```

### Language-specific ignores (ONLY if proven)

* Java / JVM

  * `target`
  * `.mvn`

* Node / TS / JS

  * `node_modules`
  * `.next`
  * `.turbo`
  * `coverage`

* Go

  * `vendor`
  * `bin`

* Python

  * `__pycache__`
  * `.venv`
  * `.pytest_cache`

* Rust

  * `target`

If NO language is proven, ONLY base ignores are allowed.

---

## Failure Checklist (Mandatory)

Generation is INVALID if ANY are true:

* `project.name` does not match repo root exactly
* Language-specific ignores without definitive marker file
* `ignored_paths` key misspelled or replaced
* Unknown schema keys used
* Assumptions or guesses applied

This file defines correctness, not advice.

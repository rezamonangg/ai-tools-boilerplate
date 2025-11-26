# AGENT-GENERATOR.md

## Purpose

This file defines **how a coding LLM must generate `AGENTS.md`** for this repository.

`AGENTS.md` is the **operating manual for an LLM working on this codebase**. It teaches the LLM:

* what the project does
* what business rules must not be broken
* how the system is structured
* how to work safely and efficiently

This file is **only** responsible for `AGENTS.md`.
It does **NOT** generate Serena configuration.

All rules are mandatory.

---

## Output File

The generator MUST produce exactly one file:

* `AGENTS.md`

Any additional files or changes are INVALID.

---

## Mandatory Generation Order

The LLM MUST follow this order:

1. Resolve repository root directory name.
2. List top-level directories only (no file reads).
3. Identify business-relevant folders via folder semantics.
4. Discover core business logic and invariants using Serena and indexed search.
5. Generate `AGENTS.md` using the exact contract below.
6. Run the failure checklist.

---

## Folder Semantics (Business-Logic Discovery)

The LLM MUST treat **singular and plural forms as equivalent**.

The LLM MUST check for business logic under directories matching the patterns below:

* service / services
* usecase / usecases / use_case / use_cases
* repository / repositories
* controller / controllers / handler / handlers / rest
* consumer / consumers
* producer / producers
* library / libraries / lib / libs
* cmd / command / commands
* internal
* pkg / packages
* helper / helpers
* common / shared
* config / configs
* model / models
* entity / entities
* dao / pojo / dto
* inbound / outbound

Folder names are **signals of responsibility**.
Never assume logic location without checking directory names.

---

## Tool Usage Rules (Strict)

Before reading ANY code, the LLM MUST choose a tool.

Tool priority (cheapest → most expensive):

1. **Serena** (symbol-level exploration)
2. **Indexed semantic search** (vector DB + embeddings)
3. **Raw text search** (grep/find)
4. **Partial file reads** (last resort)

Using a more expensive tool when a cheaper one suffices is a FAILURE.

---

## Partial File Read Limits

Allowed only when symbol and scope are known.

Hard limits per task:

* Max 200 LOC per file
* Max 3 files
* Max ~3000 tokens

Exceeding limits is a FAILURE.

---

## AGENTS.md Output Contract (EXACT)

The generated `AGENTS.md` MUST follow this structure EXACTLY.

```markdown
# AGENTS

## 1. Project Overview
- What this repository is
- What problem it solves
- High-level domain context

## 2. Core Business Logic & Critical Business Rules
- Enumerated business capabilities / use cases as table with fullpath, classname, and method name.
- Critical invariants that MUST NOT be broken
- Ordering, idempotency, consistency, security rules
- Explicit dependency rules ("If X changes, Y must also change")

## 3. Architecture Overview
- High-level architecture
- Major components and responsibilities
- Data flow between components (textual)

## 4. Tech Stack
- Languages
- Frameworks
- Datastores
- Messaging / queues
- Infrastructure dependencies

## 5. Do’s and Don’ts
### Do
- Required safe practices

### Don’t
- Forbidden or dangerous changes

## 6. How to Get Things Done in This Repo
### 6.1 Searching Code
- Serena (symbol-first)
- Indexed semantic search
- Raw search (fallback)

### 6.2 Modifying Code
- Symbol-level edits with Serena
- Approved modification patterns
- Safe fallback behavior

## 7. Available MCPs
- Serena
- Git
- SequentialThinking
```

Unknown information MUST be explicitly marked as `UNKNOWN`. Speculation is forbidden.

---

## Failure Checklist (Mandatory)

Generation is INVALID if ANY are true:

* AGENTS.md structure deviates
* Business rules are vague or missing
* Serena skipped for symbol-level tasks
* Tool usage order violated
* Partial read limits exceeded

This file defines correctness, not advice.

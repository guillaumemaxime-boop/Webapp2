# Implementation Plan: [FEATURE NAME]

**Branch**: `001-webapp2` | **Date**: 2026-05-04 | **Spec**: [./spec.md](./spec.md)
**Input**: Feature specification from `/specs/001-webapp2/spec.md`

## Execution Flow (/plan command scope)
```
1. Load feature spec from Input path
   → If not found: ERROR "No feature spec at {path}"
2. Fill Technical Context (scan for NEEDS CLARIFICATION)
   → Detect Project Type from context (web | mobile | service | library)
   → Set Structure Decision based on project type
3. Fill the Constitution Check section based on the constitution document
4. Evaluate Constitution Check section below
   → If violations exist: document in Complexity Tracking
   → If no justification possible: ERROR "Simplify approach first"
   → Update Progress Tracking: Initial Constitution Check
5. Execute Phase 0 → research.md
   → If NEEDS CLARIFICATION remain: ERROR "Resolve unknowns"
6. Execute Phase 1 → contracts/, data-model.md, quickstart.md
7. Re-evaluate Constitution Check section
   → Update Progress Tracking: Post-Design Constitution Check
8. Plan Phase 2 → describe how tasks.md will be generated (do NOT create it)
9. STOP — ready for /tasks command
```

**IMPORTANT**: The `/plan` command STOPS at step 8. Phases 2 (task generation)
and beyond are executed by other commands.

## Summary
[TO BE FILLED IN — extract the primary requirement from the spec and the
high-level technical approach in 2-3 sentences. No code, no file paths, no
library names yet.]

## Technical Context

| Field | Value |
|-------|-------|
| **Language / Version** | [NEEDS CLARIFICATION] |
| **Primary Dependencies** | [NEEDS CLARIFICATION] |
| **Storage** | [NEEDS CLARIFICATION — DB, files, none] |
| **Testing** | [NEEDS CLARIFICATION — runner, framework] |
| **Target Platform** | [NEEDS CLARIFICATION — web browser, server, mobile, …] |
| **Project Type** | [web / mobile / service / library] |
| **Performance Goals** | [NEEDS CLARIFICATION — p95 latency, throughput] |
| **Constraints** | [NEEDS CLARIFICATION — offline, memory, bundle size] |
| **Scale / Scope** | [NEEDS CLARIFICATION — users, data volume, screens] |

## Constitution Check
*GATE: Must pass before Phase 0. Re-checked after Phase 1.*

- [ ] **Specification-First**: a complete, reviewed `spec.md` exists for this feature.
- [ ] **Plan Before Code**: no implementation has started yet on this branch.
- [ ] **Test-First**: the plan describes failing tests being written before implementation.
- [ ] **Small, Reversible Changes**: tasks are independently shippable; no speculative refactors.
- [ ] **Observability & Traceability**: each FR has a planned test and traces to a task.

If any item above is unchecked, document the deviation in **Complexity Tracking**.

## Project Structure

### Documentation (this feature)
```
specs/001-webapp2/
├── spec.md              # Feature specification (input to /plan)
├── plan.md              # This file
├── research.md          # Phase 0 output
├── data-model.md        # Phase 1 output
├── quickstart.md        # Phase 1 output
├── contracts/           # Phase 1 output (API/contract specs)
└── tasks.md             # Phase 2 output (created by /tasks, NOT by /plan)
```

### Source Code (repository root)
```
[TO BE FILLED IN once Project Type is decided. Pick ONE of the layouts below
and delete the others.]

# Option 1: Single project (default)
src/
└── …
tests/
└── …

# Option 2: Web application (frontend + backend)
backend/
├── src/
└── tests/
frontend/
├── src/
└── tests/

# Option 3: Mobile + API
api/
└── …
mobile/
└── …
```

**Structure Decision**: [TO BE FILLED IN]

## Phase 0: Outline & Research
1. Extract every `NEEDS CLARIFICATION` from Technical Context.
2. For each unknown, generate a research task ("Research X for use case Y").
3. Consolidate findings in `research.md` using the format:
   - **Decision**: [what was chosen]
   - **Rationale**: [why]
   - **Alternatives considered**: [what was rejected and why]

**Output**: `research.md` with no remaining `NEEDS CLARIFICATION`.

## Phase 1: Design & Contracts
*Prerequisite: `research.md` complete*

1. **Extract entities** from the spec → `data-model.md` (fields, relationships,
   validation rules, state transitions).
2. **Generate contracts** from functional requirements → `/contracts/` (one
   schema or interface per endpoint / message).
3. **Generate contract tests** — failing by design — one per contract.
4. **Extract test scenarios** from acceptance scenarios → `quickstart.md`.
5. **Update agent context** (e.g. CLAUDE.md) with the new tech additions only.

**Output**: `data-model.md`, `/contracts/*`, failing contract tests, `quickstart.md`.

## Phase 2: Task Planning Approach
*This section describes what `/tasks` will do — do NOT execute during `/plan`.*

**Task Generation Strategy**:
- Load `.specify/templates/tasks-template.md` as the base.
- Generate tasks from Phase 1 artefacts (contracts, data model, quickstart).
- Each contract → contract-test task [P].
- Each entity → model-creation task [P].
- Each user story → integration-test task.
- Implementation tasks follow the failing tests.

**Ordering Strategy**:
- TDD order: tests precede implementation.
- Dependency order: models → services → UI/handlers.
- Mark `[P]` for tasks that touch independent files and can run in parallel.

**Estimated Output**: 25–30 numbered, ordered tasks in `tasks.md`.

## Phase 3+: Future Implementation
*Beyond the scope of `/plan`*

- **Phase 3**: Task execution (`/tasks` command creates `tasks.md`).
- **Phase 4**: Implementation (execute `tasks.md` following constitutional principles).
- **Phase 5**: Validation (run tests, execute `quickstart.md`, verify performance targets).

## Complexity Tracking
*Fill ONLY when the Constitution Check has violations that must be justified.*

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|--------------------------------------|
| [e.g. 4th project] | [current need] | [why 3 projects are insufficient] |

## Progress Tracking
*Updated during execution.*

**Phase Status**:
- [ ] Phase 0: Research complete (`/plan` command)
- [ ] Phase 1: Design complete (`/plan` command)
- [ ] Phase 2: Task planning complete (`/plan` command — describe approach only)
- [ ] Phase 3: Tasks generated (`/tasks` command)
- [ ] Phase 4: Implementation complete
- [ ] Phase 5: Validation passed

**Gate Status**:
- [ ] Initial Constitution Check: PASS
- [ ] Post-Design Constitution Check: PASS
- [ ] All `NEEDS CLARIFICATION` resolved
- [ ] Complexity deviations documented

---
*Based on Webapp2 Constitution v1.0.0 — see `.specify/memory/constitution.md`*

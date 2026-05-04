# Webapp2 Constitution

<!--
Sync Impact Report
==================
Version change: N/A → 1.0.0 (initial ratification)
Modified principles: N/A (initial creation)
Added sections: Core Principles, Additional Constraints, Development Workflow, Governance
Removed sections: N/A
Templates requiring updates:
  - .specify/templates/plan-template.md ⚠ pending (create after stack is defined)
  - .specify/templates/spec-template.md ⚠ pending (create after stack is defined)
  - .specify/templates/tasks-template.md ⚠ pending (create after stack is defined)
Follow-up TODOs:
  - TODO(RATIFICATION_DATE): set the original adoption date once approved
  - Fill in concrete tooling once the technical stack is chosen
-->

## Core Principles

### I. Specification-First
Every feature MUST start with a written specification (`spec.md`) that captures
the user-facing behaviour and acceptance criteria BEFORE any implementation
plan or code is produced. Specs describe **what** and **why**, never **how**.
Rationale: prevents implementation details from leaking into product decisions
and gives reviewers a stable reference point.

### II. Plan Before Code
No implementation may begin until a `plan.md` derived from the spec has been
reviewed. The plan MUST list the technical context, the constitution check,
and the project structure. Any deviation from the constitution MUST be
documented in the Complexity Tracking section with a justification.

### III. Test-First (NON-NEGOTIABLE)
TDD is mandatory: tests are written, reviewed, and observed to fail BEFORE
the corresponding implementation is written. Red → Green → Refactor.
Rationale: enforces designable interfaces and prevents regression debt from
piling up.

### IV. Small, Reversible Changes
Each task MUST be independently shippable and revertible. Avoid speculative
abstractions, multi-purpose refactors, and "while-I'm-here" cleanups inside a
feature branch. Three similar lines beat a premature abstraction.

### V. Observability & Traceability
User-facing behaviour MUST be traceable: structured logs at boundaries,
explicit error contracts, and no silent failures. Every functional requirement
in `spec.md` MUST be linked (by ID) to at least one task in `tasks.md` and one
test.

## Additional Constraints

- **Stack & tooling**: TBD — to be filled in once the technical stack is
  chosen. Once defined, this section MUST list the language, framework,
  test runner, linter, formatter, and minimum versions.
- **Security**: never commit secrets, tokens, or credentials. Validate all
  external inputs at system boundaries.
- **Performance budgets**: TBD — define p95 latency, bundle size, and memory
  ceilings once the product surface is known.

## Development Workflow

1. Open a feature branch named `NNN-short-slug`.
2. Author `specs/NNN-short-slug/spec.md` and get it reviewed.
3. Author `specs/NNN-short-slug/plan.md` and run the Constitution Check.
4. Generate `specs/NNN-short-slug/tasks.md` from the plan.
5. Implement tasks in order, opening a draft PR early for visibility.
6. PRs MUST link back to the spec, plan, and tasks files.
7. Merge only after tests pass and the spec's acceptance scenarios are
   demonstrably satisfied.

## Governance

This constitution supersedes any other convention in the repository. Any
amendment MUST:

1. Be proposed via a PR that updates this file and bumps the version below
   following semantic versioning:
   - **MAJOR**: backward-incompatible principle removal or redefinition.
   - **MINOR**: new principle or materially expanded guidance.
   - **PATCH**: clarifications, typos, non-semantic refinements.
2. Include a Sync Impact Report at the top of this file.
3. Propagate any required updates to the templates in `.specify/templates/`.

All PRs and reviews MUST verify compliance with these principles. Complexity
that violates a principle MUST be justified in the plan's Complexity Tracking
section or rejected.

**Version**: 1.0.0 | **Ratified**: TODO(RATIFICATION_DATE) | **Last Amended**: 2026-05-04

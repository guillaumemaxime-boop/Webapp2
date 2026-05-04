# Feature Specification: [FEATURE NAME]

**Feature Branch**: `001-webapp2`
**Created**: 2026-05-04
**Status**: Draft
**Input**: User description: "[TO BE FILLED IN — describe in plain language what the webapp should do, for whom, and why it matters]"

## Execution Flow (main)
```
1. Parse user description from Input
   → If empty: ERROR "No feature description provided"
2. Extract key concepts from description
   → Identify: actors, actions, data, constraints
3. For each unclear aspect:
   → Mark with [NEEDS CLARIFICATION: specific question]
4. Fill User Scenarios & Testing section
   → If no clear user flow: ERROR "Cannot determine user scenarios"
5. Generate Functional Requirements
   → Each requirement must be testable
   → Mark ambiguous requirements
6. Identify Key Entities (if data involved)
7. Run Review & Acceptance Checklist
   → If any [NEEDS CLARIFICATION]: WARN "Spec has uncertainties"
   → If implementation details found: ERROR "Remove tech details"
8. Return: SUCCESS (spec ready for planning)
```

---

## ⚡ Quick Guidelines
- ✅ Focus on WHAT users need and WHY
- ❌ Avoid HOW to implement (no tech stack, APIs, code structure)
- 👥 Written for business stakeholders, not developers

### Section Requirements
- **Mandatory sections**: User Scenarios, Requirements, Review Checklist
- **Optional sections**: Key Entities (only if the feature handles data)
- A section that does not apply MUST be removed entirely (do not leave "N/A")

### For AI Generation
When creating this spec from a user prompt:
1. **Mark every ambiguity** with `[NEEDS CLARIFICATION: question]`
2. **Do not invent** acceptance criteria, SLAs, roles, or data shapes
3. **Think like a tester** — every vague requirement must fail the
   "is this testable and unambiguous?" check
4. Common under-specified areas to challenge:
   - User types and permissions
   - Data retention & deletion policies
   - Performance targets and scale
   - Error handling and recovery
   - Integrations with existing systems
   - Security & compliance requirements

---

## User Scenarios & Testing *(mandatory)*

### Primary User Story
[TO BE FILLED IN — one paragraph describing the most important journey through
the feature, in plain language, from the user's perspective.]

### Acceptance Scenarios
1. **Given** [initial state], **When** [user action], **Then** [observable outcome]
2. **Given** [initial state], **When** [user action], **Then** [observable outcome]

### Edge Cases
- What happens when [boundary condition]?
- How does the system behave under [error or degraded condition]?
- What is the expected response to [unauthorised / unexpected input]?

## Requirements *(mandatory)*

### Functional Requirements
- **FR-001**: System MUST [specific, testable capability]
- **FR-002**: System MUST [specific, testable capability]
- **FR-003**: Users MUST be able to [key interaction]
- **FR-004**: System MUST [data behaviour]
- **FR-005**: System MUST [behaviour under failure]

*Examples of vague requirements that MUST be clarified:*
- **FR-006**: System MUST authenticate users via [NEEDS CLARIFICATION: auth method — email/password, SSO, OAuth?]
- **FR-007**: System MUST retain user data for [NEEDS CLARIFICATION: retention period not specified]

### Key Entities *(include only if the feature involves data)*
- **[Entity 1]**: [what it represents, key attributes — no storage details]
- **[Entity 2]**: [what it represents, relationship to Entity 1]

---

## Review & Acceptance Checklist
*GATE: automated checks performed before the spec is considered ready*

### Content Quality
- [ ] No implementation details (languages, frameworks, APIs)
- [ ] Focused on user value and business needs
- [ ] Written for non-technical stakeholders
- [ ] All mandatory sections completed

### Requirement Completeness
- [ ] No `[NEEDS CLARIFICATION]` markers remain
- [ ] Requirements are testable and unambiguous
- [ ] Success criteria are measurable
- [ ] Scope is clearly bounded
- [ ] Dependencies and assumptions are identified

---

## Execution Status
*Updated by main() during processing*

- [ ] User description parsed
- [ ] Key concepts extracted
- [ ] Ambiguities marked
- [ ] User scenarios defined
- [ ] Requirements generated
- [ ] Entities identified
- [ ] Review checklist passed

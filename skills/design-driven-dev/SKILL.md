---
name: design-driven-dev
description: Guide for design-driven development workflow. Use this for nearly ALL work - find or create a design before implementation. Only exceptions: debugging sessions, quick bug fixes (<30 min), or prototype spikes. For everything else: HLD → LLD → EARS specs → Implementation plan → Code with spec annotations.
---

# Design-Driven Development

This skill guides a structured design-driven development workflow. The goal is to get alignment on what you're building *before* writing code, which dramatically reduces rework and misunderstandings.

## Critical Rule: Stop and Iterate

**STOP after completing each phase.** Present the document to the user for review. Incorporate their numbered feedback. Only proceed to the next phase when explicitly approved.

This is the most important part of the workflow. Don't rush through design to get to code.

## Workflow Overview

1. **High-Level Design (HLD)** - Project vision and architecture
2. **Low-Level Design (LLD)** - Component-specific technical design
3. **EARS Specifications** - Requirements with semantic IDs
4. **Implementation Plan** - Phases, checkboxes, Definition of Done

## When to Use This Workflow

**Use for nearly all work.** Before implementing, either find an existing design or create one.

**Skip only for:**
- Debugging sessions (investigating issues)
- Quick bug fixes (<30 minutes)
- Prototype spikes (exploratory code)

**If unsure, use the workflow.** Over-designing is safer than under-designing.

## Phase 1: High-Level Design

Check if a project HLD exists first: `/docs/high-level-design.md`

For new projects or major features, create an HLD covering:
- Problem statement and goals
- Target users and personas
- System architecture overview
- Key design decisions and trade-offs
- Non-goals (what's explicitly out of scope)

**Stop and get user approval before proceeding.**

## Phase 2: Low-Level Design

Create component-specific LLDs in `/docs/llds/` for each major component.

See [lld-templates.md](references/lld-templates.md) for structure guidance.

Key principles:
- **Narrative format** for complex constraint interactions
- **Structured format** for API contracts and interfaces
- Include data models, error handling, edge cases
- Reference the HLD for context

**Stop and get user approval before proceeding.**

## Phase 3: EARS Specifications

Generate requirements using EARS (Easy Approach to Requirements Syntax).

See [ears-syntax.md](references/ears-syntax.md) for full syntax reference.

Key principles:
- **Semantic spec IDs**: `{FEATURE}-{TYPE}-{NNN}` (e.g., `AUTH-UI-001`, `CART-API-003`)
- Create in `/docs/specs/` (e.g., `user-authentication-specs.md`)
- Each requirement is testable and traceable
- Include acceptance criteria

**Stop and get user approval before proceeding.**

## Phase 4: Implementation Plan

Create execution plan in `/docs/planning/` with date suffix.

See [plan-templates.md](references/plan-templates.md) for structure guidance.

Key elements:
- **Phases** with clear deliverables
- **Checkboxes** for tracking progress
- **Spec ID references** tying to EARS requirements
- **Definition of Done** with verification criteria
- **Testing requirements** with spec annotations

**Stop and get user approval before proceeding.**

## Code Annotation Pattern

Annotate code with `@spec` comments linking to EARS IDs:

```typescript
// @spec AUTH-UI-001, AUTH-UI-002, AUTH-UI-003
export function LoginForm({ ... }) {
  // Implementation
}
```

Test files also reference specs:

```typescript
// @spec AUTH-UI-010
it('validates email format before submission', () => {
  expect(validateEmail('invalid')).toBe(false);
});
```

This creates traceability from requirements → code → tests.

## Progress Tracking

During implementation:
- Check off items in the implementation plan as completed
- Update the plan doc with any discovered changes
- Move completed phases to an `/old/` subdirectory when fully done

## Why This Works

| Benefit | Why It Matters |
|---------|----------------|
| **Forced checkpoints** | Catches misunderstandings before you've built the wrong thing |
| **Scannable docs** | One-line requirements easy to search and reference |
| **Traceability** | @spec annotations link code to requirements |
| **Survives session breaks** | Docs persist, context doesn't get lost |
| **Reusable** | Same docs work across multiple sessions |
| **Testable requirements** | EARS format ensures requirements are verifiable |

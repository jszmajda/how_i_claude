# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

Shareable tools, skills, and guides for working with agentic AI coding systems. The current content includes practical guides (based on analysis of 1,352 real development messages) and reusable Claude Code skills, but the repo is not specific to any one tool. There is no build system, test suite, or application code.

## Structure

- **Root markdown files**: Guides and reference material (workflow guide, communication guide, quick reference, meta blog post, data index)
- **`skills/`**: Reusable skill definitions for agentic coding systems
  - **`design-driven-dev/`**: Structured HLD → LLD → EARS → Implementation Plan workflow with intent coherence tracking
  - **`arrow-maintenance/`**: Scaling layer for design-driven-dev — tracks spec-to-code coherence across large projects via `docs/arrows/` index

## Skills Architecture

The two skills form a layered system:

1. **design-driven-dev** is the core workflow — consult for ALL code changes in projects that use it. New features get full 4-phase design (HLD → LLD → EARS specs → Plan). Bug fixes skip doc creation but still verify intent coherence.

2. **arrow-maintenance** overlays on top — adds navigation (`index.yaml`) and tracking (arrow docs) for projects too large to hold in one context window. Arrows map the `HLD → LLDs → EARS → Tests → Code` chain per domain/subsystem.

Both skills use EARS (Easy Approach to Requirements Syntax) for specifications with semantic IDs (`{FEATURE}-{TYPE}-{NNN}`), `@spec` code annotations, and status markers (`[x]` implemented, `[ ]` gap, `[D]` deferred).

## Editing Guidelines

- Guides should remain grounded in the original data analysis — don't add claims without evidence
- Skills follow the SKILL.md frontmatter format (`name`, `description` in YAML front matter)
- The skill `description` field is critical — it determines when Claude auto-invokes the skill. Use specific trigger words, not vague descriptions
- Reference templates live in `references/` subdirectories within each skill

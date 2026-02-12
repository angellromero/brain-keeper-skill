# Brain Keeper Skill

An AI agent skill that maintains Context Brain documentation throughout the development lifecycle. Brain Keeper ensures that code and documentation evolve together, preventing documentation debt before it accumulates.

## What It Does

Brain Keeper is an always-active skill that:

- **Initializes Context Brain** in new projects with proper structure and templates
- **Enforces documentation-with-code** by ensuring artifacts accompany every code change
- **Maintains artifact quality** through grounding, tracking, and gap detection
- **Guides artifact creation** using appropriate templates with right-sized verbosity
- **Implements the Three Laws** (Reciprocity, Creation, Immutability) automatically

## The Three Laws

1. **Reciprocity**: When you consult an artifact and find it outdated, fix it before closing the PR
2. **Creation**: All new code requires new context (1:1 correlation) — no exceptions
3. **Immutability**: ADRs are historical records — supersede them, never edit them

## When to Use

Brain Keeper is **always active during development work**. It automatically:

- Grounds you in Context Brain artifacts before code generation (hard gate)
- Tracks artifact interactions as you work
- Reports Context Brain activity at commit checkpoints
- Detects documentation gaps (Critical 🔴, Moderate 🟡, Minor 🟢)
- Blocks commits when critical gaps exist

## Core Capabilities

### Project Initialization
Bootstraps new projects with complete Context Brain structure including root AGENTS.md, directory structure, and templates.

### Pre-Flight Grounding
Before writing code, Brain Keeper reads relevant artifacts (root AGENTS.md, Domain Guides, Component docs, ADRs) and produces a "Grounded Statement" showing what was consulted.

### Gap Detection
Identifies missing or stale documentation:
- 🔴 **Critical** (blocks commit): New components without docs, undocumented breaking changes
- 🟡 **Moderate** (recommended fix): Stale docs, outdated guides
- 🟢 **Minor** (noted): Sparse coverage, nice-to-haves

### Context Brain Activity Reports
At commit checkpoints, produces traceability reports showing:
- **Referenced**: Artifacts consulted
- **Updated**: Artifacts modified
- **Created**: New artifacts
- **Gaps Identified**: With severity levels
- **Status**: Ready to commit or blocked

### Artifact Creation Guidance
Uses decision frameworks and templates to create:
- **Root AGENTS.md**: Project entry point
- **ADRs**: Architectural decisions
- **Domain Guides**: Pattern documentation
- **Component AGENTS.md**: Component-level documentation

## Verbosity Calibration

Brain Keeper enforces right-sized documentation:
- **Too sparse**: "Handles auth" ❌
- **Right-sized**: "Manages JWT token refresh and session validation. Integrates with AuthProvider context." ✅
- **Too verbose**: [3 paragraphs explaining JWT history] ❌

Every word costs tokens. Write for density, not length.

## Workflow

1. **Check-In**: Ground in Context Brain before coding (required)
2. **Track**: Monitor artifact references, modifications, creations
3. **Report**: Activity Log at checkpoints and mid-task when meaningful
4. **Resolve**: Fix critical gaps before commit

## Usage

This skill can be integrated with AI coding assistants that support custom agent skills. The skill activates automatically during development work and guides the AI agent through Context Brain maintenance workflows.

## References

The skill includes comprehensive templates and guides in the `references/` directory:
- Project initialization procedures
- Artifact templates (AGENTS.md, ADR, Domain Guide, Component docs)
- Gap detection protocols
- Verbosity guidelines

## Philosophy

**Documentation is not a separate task. It is part of "done."**

A feature without documentation is an unfinished feature. Brain Keeper exists to prevent documentation debt before it accumulates, treating documentation as inseparable from code.

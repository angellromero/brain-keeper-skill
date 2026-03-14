# Brain Keeper

An AI agent skill that maintains living documentation alongside code throughout the entire development lifecycle. Brain Keeper ensures that every planning session, implementation, debug pass, refactor, and code review leaves the project's Context Brain accurate and complete — so documentation debt never accumulates and AI agents always have reliable context to work from.

---

## The Problem

- **Documentation drifts from code within days.** Teams write docs at launch, then never touch them again. Within a sprint or two, the docs describe a system that no longer exists.
- **AI agents hallucinate when context is stale.** Coding assistants read your AGENTS.md, Domain Guides, and ADRs to understand your codebase. When those artifacts are wrong, the AI confidently generates code that violates your actual patterns — and you spend time debugging suggestions instead of shipping.
- **"We'll document it later" means never.** Every team says it. Almost none follow through. The result is tribal knowledge locked in the heads of whoever wrote the code, and a codebase that becomes hostile to new contributors and AI tools alike.
- **Onboarding costs scale with documentation debt.** New engineers (and new AI agents) spend weeks reverse-engineering conventions that should have been written down when the decision was made.
- **Undocumented architectural decisions get relitigated.** Without ADRs, the same debates resurface every quarter. Someone proposes the approach that was already rejected — and nobody remembers why.

Catching documentation gaps during development costs a fraction of what it costs to reconstruct context after the fact. Brain Keeper treats documentation as part of "done," not a separate task.

---

## What This Skill Does

Brain Keeper acts as an always-active documentation layer that integrates into every phase of AI-assisted development. It reads existing Context Brain artifacts before work begins, tracks what changes during work, and ensures documentation reflects the new state before work is committed.

### Operating Modes

| Mode | When It Activates | What It Does |
|------|-------------------|--------------|
| **Pre-Flight Grounding** | Start of any task (plan, implement, debug, review) | Reads AGENTS.md and relevant `.agent/` docs, produces a Grounded Statement showing what was consulted |
| **Always-Active Tracking** | During any development work | Silently monitors whether new components, patterns, or decisions need documentation |
| **Commit Checkpoint** | User signals completion (commit, PR, "ship it") | Produces Context Brain Activity report, blocks on critical gaps, reports documentation status |
| **Initialization** | New project or missing Context Brain | Bootstraps full Context Brain structure with templates and root AGENTS.md |
| **Documentation Analysis** | User requests a review of existing docs | Three-level audit (Presence → Structure → Semantic) with health score and prioritized findings |

### The Three Laws

These non-negotiable principles govern all Brain Keeper behavior:

| Law | Principle | In Practice |
|-----|-----------|-------------|
| **Reciprocity** | If you consult an artifact and find it outdated, fix it | The person who discovers drift owns the fix — no tickets for "later" |
| **Creation** | All new code requires new context (1:1 correlation) | New component → AGENTS.md. New pattern → Domain Guide. New decision → ADR |
| **Immutability** | ADRs are historical records — never edit accepted ADRs | When decisions change, create a new ADR that supersedes the old one |

---

## Skill Architecture

```
brain-keeper/
├── SKILL.md                                    # Core skill (~519 lines)
│   ├── Core philosophy & Three Laws
│   ├── Project initialization triggers
│   ├── Context Brain check-in workflow
│   ├── Always-active tracking checklist
│   ├── Commit checkpoint & activity reports
│   ├── Gap detection & severity system
│   ├── Decision framework (which artifact?)
│   ├── Verbosity calibration guidelines
│   └── Documentation analysis mode
│
└── references/                                 # Loaded on demand based on context
    ├── initialization.md                       # Full bootstrapping process for new projects
    ├── gap-detection.md                        # Detailed gap handling protocols & resolution
    ├── template-root-agents.md                 # Root AGENTS.md template
    ├── template-adr.md                         # Architectural Decision Record template
    ├── template-domain-guide.md                # Domain Guide template
    └── template-component-agents.md            # Component AGENTS.md template
```

The skill uses **progressive disclosure** — the SKILL.md is always loaded when triggered, and reference files are loaded only when needed. An initialization request pulls in `initialization.md` + the root template. A commit checkpoint on a new component pulls in `template-component-agents.md`. A gap resolution pulls in `gap-detection.md`. This keeps context usage efficient while providing full coverage.

---

## Coverage

### Artifact Types

| Artifact | Purpose | Template Provided |
|----------|---------|-------------------|
| Root AGENTS.md | Project entry point — structure, conventions, index to everything else | Yes |
| ADR (Architectural Decision Record) | "Why" decisions — technology choices, pattern rationale, trade-offs | Yes |
| Domain Guide | "How" patterns — conventions for a system area (auth, state, data layer) | Yes |
| Component AGENTS.md | Co-located docs — what a component does, its API, usage examples | Yes |

### Development Phases

| Phase | Brain Keeper Involvement |
|-------|--------------------------|
| **Planning** | Reads existing artifacts so plans reflect actual conventions, not assumptions |
| **Implementing** | Tracks new components/patterns/decisions that need documentation |
| **Debugging** | Grounds in documented architecture to locate root causes faster |
| **Refactoring** | Identifies governing ADRs before proposing structural changes |
| **Code Review** | Verifies documented patterns match what was actually built |
| **Committing** | Full activity report, gap detection, blocks on critical issues |

### Gap Detection

| Severity | Gap Type | Behavior |
|----------|----------|----------|
| 🔴 **Critical** | New component without docs, breaking change undocumented, new pattern not captured | Blocks commit — must resolve |
| 🟡 **Moderate** | Stale component docs, outdated Domain Guide, inaccurate examples | Recommended fix |
| 🟢 **Minor** | Sparse area coverage, missing nice-to-haves | Noted, optional |

---

## Output Format

### Grounded Statement (Task Start)

```
## Grounded In

**Root:** AGENTS.md — [key takeaway]
**Domains:** [guides consulted] — [relevant patterns]
**Components:** [AGENTS.md files] — [relevant context]
**ADRs:** [decisions reviewed] — [constraints noted]

Proceeding with task.
```

### Context Brain Activity (Commit Checkpoint)

```
## Context Brain Activity

**Referenced:** [artifacts consulted]
**Updated:** [artifacts modified]
**Created:** [new artifacts]
**Gaps Identified:**
- 🔴 [Critical — blocks commit]
- 🟡 [Moderate — recommended]
- 🟢 [Minor — noted]

**Status:** [Ready to commit | Blocked — see critical gaps]
```

### Documentation Analysis Report (On Request)

```
## Documentation Analysis Report

**Scope:** [What was reviewed]
**Health Score:** [Good | Needs Attention | Critical]

**Findings:**
- 🔴 Critical: [Must fix issues]
- 🟡 Moderate: [Should fix issues]
- 🟢 Minor: [Consider fixing]

**Recommended Actions:**
1. [Priority action]
2. [Next action]
```

---

## Example Usage

### Starting a Feature

**Prompt:**
> Add a new payment processing module to the checkout flow.

**Brain Keeper will:**
- Read root AGENTS.md to understand project structure and conventions
- Identify relevant Domain Guides (e.g., checkout patterns, payment integrations)
- Check for governing ADRs (e.g., payment provider decisions)
- Produce a Grounded Statement before any code is written
- Track that a new component AGENTS.md and possible Domain Guide update will be needed

### Debugging a Bug

**Prompt:**
> The user session is expiring too early. Can you investigate?

**Brain Keeper will:**
- Read AGENTS.md and auth-related Domain Guides before investigating
- Check for ADRs governing session management decisions
- Ground the debugging session in documented architecture so investigation targets the right layer
- Flag if auth documentation is stale or missing during investigation

### Committing Changes

**Prompt:**
> Ready to commit — let's wrap this up.

**Brain Keeper will:**
- Produce a Context Brain Activity report listing all artifacts referenced, updated, and created
- Run gap detection across all changes
- Block if critical gaps exist (e.g., new component without AGENTS.md)
- Report moderate and minor gaps for optional resolution
- Confirm "Ready to commit" or "Blocked — see critical gaps"

### Initializing a New Project

**Prompt:**
> Set up Context Brain for this repo.

**Brain Keeper will:**
- Detect absence of AGENTS.md and `.agent/` directory
- Bootstrap full Context Brain structure using templates
- Create root AGENTS.md as the project entry point
- Set up `.agent/` directory with initial Domain Guides based on existing code
- Provide guidance on maintaining the structure going forward

---

## Limitations

This skill is a documentation maintenance layer, not a replacement for human judgment about what to document. Important caveats:

- **Requires Context Brain structure.** Brain Keeper works with projects that use (or are willing to adopt) the AGENTS.md / `.agent/` documentation pattern. It does not maintain arbitrary documentation formats.
- **Cannot verify documentation accuracy against runtime behavior.** The skill checks for presence and structural correctness of documentation, but cannot run the code to verify that documented behavior matches actual behavior.
- **Relies on honest artifact content.** If existing documentation is wrong, Brain Keeper treats it as ground truth during pre-flight grounding. The Law of Reciprocity mitigates this over time, but initial bootstrapping of a poorly-documented project requires manual review.
- **Cannot assess documentation quality beyond structure.** The skill checks that required sections exist and follow templates, but whether the *content* is genuinely useful to future readers is a human judgment call.
- **Gap detection is based on file changes, not semantic analysis.** If you refactor internal logic without changing the public API, Brain Keeper may not flag that internal documentation needs updating.
- **Template-driven, not prescriptive.** Templates are starting points. The skill guides artifact creation but does not enforce a single rigid format — teams should adapt templates to their conventions.

---

## Installation

Copy the `brain-keeper/` directory to your skills location with the following structure:

```
brain-keeper/
├── SKILL.md
└── references/
    ├── initialization.md
    ├── gap-detection.md
    ├── template-root-agents.md
    ├── template-adr.md
    ├── template-domain-guide.md
    └── template-component-agents.md
```

The skill activates automatically during any development work in a project that has (or should have) a Context Brain. No manual invocation is needed — it triggers on planning, implementing, debugging, refactoring, reviewing, and committing.

---

## Verbosity Philosophy

Every word in a Context Brain artifact costs tokens. Brain Keeper enforces right-sized documentation:

| Too Sparse | Right-Sized | Too Verbose |
|------------|-------------|-------------|
| "Handles auth" | "Manages JWT token refresh and session validation. Integrates with AuthProvider context." | [3 paragraphs explaining JWT history] |
| "See code" | "Props: userId (required), onSuccess callback (optional). Fetches user profile on mount." | [Repeating what TypeScript types already show] |

**Default to lean. Add detail only when its absence causes problems.**

---

Built with the belief that documentation is not a separate task — it is part of "done." A feature without documentation is an unfinished feature, and a codebase without a Context Brain is a codebase running on tribal knowledge and luck.

# Domain Guide Template

Use this template when creating Domain Guides — living documents that explain how to work within a specific area of the codebase.

---

## Template

```markdown
# [Domain Name] Domain Guide

## Overview

[What this domain covers and why it matters. 2-3 sentences that help someone quickly determine if this is the right guide for their task.]

## Foundational Decisions

[Link to relevant ADRs that explain WHY things are done this way]

- See @.agent/adrs/[NNN-decision].md for [brief description of what it covers]
- See @.agent/adrs/[NNN-decision].md for [brief description of what it covers]

## Core Patterns

### Pattern 1: [Pattern Name]

[Explanation of when and why to use this pattern]

```[language]
// Code example demonstrating the pattern
```

### Pattern 2: [Pattern Name]

[Explanation of when and why to use this pattern]

```[language]
// Code example demonstrating the pattern
```

### Pattern 3: [Pattern Name]

[Explanation of when and why to use this pattern]

```[language]
// Code example demonstrating the pattern
```

## Examples in Practice

[Point to real components/files that demonstrate these patterns — these serve as "golden path" references]

- `@/path/to/component/` — [What pattern it demonstrates]
- `@/path/to/component/` — [What pattern it demonstrates]
- `@/path/to/component/` — [What pattern it demonstrates]

## Common Gotchas

### Gotcha 1: [Short Description]

[Explain the mistake and why it's problematic]

**Bad:**
```[language]
// What NOT to do
```

**Good:**
```[language]
// What TO do instead
```

### Gotcha 2: [Short Description]

[Explain the mistake and why it's problematic]

**Bad:**
```[language]
// What NOT to do
```

**Good:**
```[language]
// What TO do instead
```

## Testing

[How to test code in this domain — specific commands, patterns, or approaches]

```bash
# Example test command
```

## Related Documentation

- Domain Guide: @.agent/domains/[related-guide].md — [relationship]
- ADR: @.agent/adrs/[relevant-adr].md — [what it covers]
- How-To: @.agent/guides/[related-guide].md — [what it covers]
```

---

## Naming Convention

`[domain-name].md` using kebab-case

Examples:
- `state-management.md`
- `component-architecture.md`
- `data-fetching.md`
- `authentication-flow.md`
- `checkout-flow.md`

---

## When to Create a Domain Guide

**Create Domain Guide for:**
- Major system areas with established patterns (auth, state, data layer)
- Areas where multiple components follow shared conventions
- Domains where consistency matters across the team
- Topics that require explanation beyond a single ADR

**Do NOT create Domain Guide for:**
- Single technology choices (use ADR)
- Step-by-step procedures (use How-To Guide)
- Individual component documentation (use Component AGENTS.md)

---

## Domain Guide vs ADR

| ADR | Domain Guide |
|-----|--------------|
| "Why did we choose Jotai?" | "How do we use Jotai in this project?" |
| Historical, immutable | Current, living |
| Single decision | Broad area |
| Captures rationale | Captures patterns |

They work together: Domain Guide references ADRs for the "why" while providing the "how."

---

## Maintenance Rules

Domain Guides are LIVING documents. When patterns change:

1. Update the Domain Guide to reflect current reality
2. If the change was a significant decision, create a new ADR documenting why
3. Update any component AGENTS.md files affected by the pattern change
4. Ensure "Examples in Practice" still point to valid, current examples

---

## Quality Checklist

- [ ] Overview clearly explains what this domain covers
- [ ] Foundational Decisions link to relevant ADRs
- [ ] Core Patterns include actual code examples (not pseudocode)
- [ ] Examples in Practice point to real files in the codebase
- [ ] Gotchas show both bad and good patterns
- [ ] Related Documentation links are bidirectional
- [ ] All file paths use @ prefix convention

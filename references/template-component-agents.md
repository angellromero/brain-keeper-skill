# Component AGENTS.md Template

Use this template when creating co-located documentation for individual components. These are "leaf nodes" in the Context Brain hierarchy.

---

## Template

```markdown
# [Component Name]

## Overview

[1-2 sentence description of what this component does]

## Purpose

[Why this component exists and when to use it. What problem does it solve?]

## Location

`[full/path/to/component]`

## Props

| Prop | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| `propName` | `string` | Yes | - | What this prop controls |
| `optionalProp` | `number` | No | `0` | What this prop controls |
| `callback` | `() => void` | No | - | When this callback fires |

## State Management

[How this component manages state — local useState, Jotai atoms, context, etc.]

[If using atoms or shared state, specify which ones:]
- Reads from: `[atomName]` 
- Writes to: `[atomName]`

## Data Fetching

[How this component gets its data — props, API calls, database queries, server component fetching, etc.]

[If it fetches data directly:]
```[language]
// Data fetching pattern used
```

## Example Usage

```[language]
<ComponentName 
  propName="value"
  optionalProp={123}
/>
```

[Include additional examples if the component has multiple usage patterns]

## Testing

Run tests: `[specific test command for this component]`

[Any testing-specific notes — mocking requirements, test utilities, etc.]

## Related Documentation

- Domain Guide: @.agent/domains/[relevant-guide].md
- ADR: @.agent/adrs/[relevant-adr].md
- Similar Component: @/path/to/similar/component/
```

---

## File Location

Component AGENTS.md files are **co-located** with the component they document:

```
ComponentName/
├── AGENTS.md              ← This file
├── ComponentName.tsx
├── ComponentName.test.tsx
├── ComponentName.styles.ts (if applicable)
└── index.ts
```

---

## When to Create Component AGENTS.md

**Every component should have one.** The Law of Creation states: new component → new AGENTS.md.

Prioritize documenting:
- Shared/reusable components
- Complex components with non-obvious logic
- Components that demonstrate important patterns (canonical examples)
- Frequently modified components

---

## The "Leaf Node" Role

Component AGENTS.md files serve as leaf nodes that AI agents navigate to after:

1. Reading root AGENTS.md (project overview)
2. Consulting relevant Domain Guide (patterns for this type of work)
3. Arriving at a similar component's AGENTS.md (concrete example)

This means your component documentation should be **complete enough to serve as a learning example** for AI agents creating similar components.

---

## Props Table Guidelines

- List all public props, even if they seem obvious
- Use exact TypeScript types
- Always specify Required (Yes/No)
- Include default values when applicable
- Description should explain *what it does*, not just restate the name

**Good:**
```
| `isLoading` | `boolean` | No | `false` | Displays skeleton UI while data fetches |
```

**Bad:**
```
| `isLoading` | `boolean` | No | `false` | Loading state |
```

---

## Quality Checklist

- [ ] Overview is 1-2 sentences, not a paragraph
- [ ] Purpose explains when/why to use this component
- [ ] Location path is accurate and complete
- [ ] Props table includes ALL public props
- [ ] State Management explains where state lives
- [ ] Data Fetching explains the data flow
- [ ] Example Usage is copy-pasteable
- [ ] Testing command is specific to this component
- [ ] Related Documentation links to relevant guides and ADRs

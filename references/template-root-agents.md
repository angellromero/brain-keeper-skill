# Root AGENTS.md Template

Use this template when creating the root AGENTS.md file for a project. This is the **entry point** for the entire Context Brain.

---

## Template

```markdown
# [Project Name]

## Overview

[1-2 sentence description of the project and its purpose]

## Tech Stack

| Category | Technology | Version |
|----------|------------|---------|
| Framework | [e.g., Next.js] | [e.g., 14.x] |
| Language | [e.g., TypeScript] | [e.g., 5.x] |
| Styling | [e.g., Tailwind CSS] | [e.g., 3.x] |
| State Management | [e.g., Jotai] | [e.g., 2.x] |
| Database | [e.g., PostgreSQL] | [e.g., 15.x] |
| ORM | [e.g., Prisma] | [e.g., 5.x] |
| Testing | [e.g., Vitest] | [e.g., 1.x] |

## Global Commands

| Command | Description |
|---------|-------------|
| `[package-manager] install` | Install all dependencies |
| `[package-manager] dev` | Start development server |
| `[package-manager] build` | Create production build |
| `[package-manager] test` | Run test suite |
| `[package-manager] lint` | Run linter |
| `[package-manager] typecheck` | Run TypeScript type checking |

## Project Structure

```
[project-root]/
├── apps/
│   └── [app-name]/           # [Brief description]
├── packages/
│   └── [package-name]/       # [Brief description]
├── .agent/                   # Context Brain documentation
│   ├── adrs/                 # Architectural Decision Records
│   ├── domains/              # Domain Guides
│   ├── guides/               # How-To Guides
│   └── templates/            # Code and doc templates
└── [other directories...]
```

## The Context Brain (.agent/)

### Architectural Decision Records

Key decisions documented in `@.agent/adrs/`:

| ADR | Title | Status |
|-----|-------|--------|
| 001 | [Decision title] | Accepted |
| 002 | [Decision title] | Accepted |
| 003 | [Decision title] | Accepted |

### Domain Guides

Implementation patterns in `@.agent/domains/`:

- `[domain-name].md` — [Brief description of what it covers]
- `[domain-name].md` — [Brief description of what it covers]

### How-To Guides

Procedural documentation in `@.agent/guides/`:

- `[guide-name].md` — [What procedure it covers]

## File Conventions

### Naming

- **Components**: PascalCase directories (`ProductCard/`)
- **Utilities**: camelCase files (`formatCurrency.ts`)
- **Types**: PascalCase with suffix (`Product.types.ts`)
- **Constants**: SCREAMING_SNAKE_CASE (`API_BASE_URL`)

### Component Structure

```
ComponentName/
├── AGENTS.md              # Component documentation (required)
├── ComponentName.tsx      # Main component
├── ComponentName.test.tsx # Tests
├── ComponentName.styles.ts # Styles (if applicable)
└── index.ts               # Public exports
```

## Critical Rules

[Non-negotiable rules that apply across the entire project]

1. **[Rule name]**: [Explanation]
2. **[Rule name]**: [Explanation]
3. **[Rule name]**: [Explanation]

## Environment Setup

[Brief notes on environment requirements — Node version, required env vars, etc.]

Required environment variables (see `.env.example`):
- `DATABASE_URL` — [Description]
- `[VAR_NAME]` — [Description]

## Related Documentation

- [Link to external docs if applicable]
- [Link to design system if applicable]
- [Link to API documentation if applicable]
```

---

## File Location

The root AGENTS.md **must** be at the project root:

```
project-root/
├── AGENTS.md              ← This file (entry point)
├── .agent/                ← Context Brain directory
├── apps/
├── packages/
└── ...
```

---

## Purpose

The root AGENTS.md serves three critical functions:

1. **Entry Point**: First file AI agents read to orient themselves
2. **Index**: Map to all other Context Brain documentation
3. **Quick Reference**: Global commands, conventions, and critical rules

---

## What NOT to Include

The root AGENTS.md should be **high-level**. Avoid:

- Detailed implementation patterns (use Domain Guides)
- Historical decision rationale (use ADRs)
- Component-specific documentation (use Component AGENTS.md)
- Step-by-step procedures (use How-To Guides)

If a section grows beyond a few lines, it belongs in a dedicated document.

---

## Maintenance

The root AGENTS.md changes when:

- Tech stack versions are upgraded
- New ADRs or Domain Guides are created (update the index)
- Global commands change
- Project structure changes significantly
- Critical rules are added or modified

Assign an owner responsible for keeping this file accurate.

---

## Quality Checklist

- [ ] Overview clearly describes the project in 1-2 sentences
- [ ] Tech Stack lists all major technologies with versions
- [ ] Global Commands are accurate and tested
- [ ] Project Structure reflects actual directory layout
- [ ] ADR index lists all current ADRs with accurate statuses
- [ ] Domain Guide index lists all current guides
- [ ] File Conventions match actual codebase patterns
- [ ] Critical Rules are genuinely critical (not nice-to-haves)
- [ ] All `@.agent/` paths are correct

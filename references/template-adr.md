# ADR Template

Use this template when creating Architectural Decision Records.

---

## Template

```markdown
# ADR [NUMBER]: [Title in Imperative Form]

**Status:** [Proposed | Accepted | Deprecated | Superseded by ADR-XXX]
**Date:** [YYYY-MM-DD]
**Deciders:** [Who was involved in making this decision]

## Context

[Describe the situation that necessitated the decision. Include:
- What problem are we solving?
- What constraints do we face?
- What requirements must be met?
- What triggered this decision now?]

## Decision

[State the decision clearly and concisely. Use the imperative form: "We will..." rather than "We decided to..."]

## Consequences

**Positive:**
- [Benefit 1]
- [Benefit 2]
- [Benefit 3]

**Negative:**
- [Trade-off 1]
- [Limitation 1]
- [Additional complexity 1]

## Alternatives Considered

[Optional but recommended: What other options did you evaluate?]

**[Alternative 1 Name]:**
- Rejected because: [reason]
- Would have provided: [benefits]

**[Alternative 2 Name]:**
- Rejected because: [reason]
- Would have provided: [benefits]

## References

- [Link to relevant documentation]
- [Link to internal discussions]
- [Link to external resources that informed the decision]
```

---

## Naming Convention

`NNN-short-description.md`

Examples:
- `001-use-nextjs-app-router.md`
- `002-adopt-jotai-for-state-management.md`
- `015-migrate-product-catalog-to-graphql.md`

---

## When to Create an ADR

**Create ADR for:**
- Technology choices (frameworks, databases, libraries)
- Architectural patterns (API architecture, deployment strategy, data flow)
- Irreversible or costly decisions
- Decisions affecting multiple teams or systems
- Resolving technical debates where rationale should be preserved

**Do NOT create ADR for:**
- Routine implementation details (use Domain Guides)
- Temporary decisions or experiments
- Easily reversible choices with minimal migration cost
- Single-component decisions without broader impact

---

## Superseding an ADR

Never modify an accepted ADR. Create a new ADR that supersedes it:

```markdown
# ADR 015: [New Decision Title]

**Status:** Accepted
**Date:** [Date]
**Deciders:** [Team]
**Supersedes:** ADR-008 ([Original Decision Title])

## Context

Since adopting [original decision] (ADR-008), [explain what changed]...
```

Then update ONLY the status line of the original:

```markdown
**Status:** Superseded by ADR-015
```

---

## Quality Checklist

- [ ] Title uses imperative form ("Use X" not "Using X" or "We decided to use X")
- [ ] Context explains the "why now" — what triggered this decision
- [ ] Decision is clear and unambiguous
- [ ] Consequences include both positive AND negative
- [ ] Alternatives section shows other options were considered
- [ ] References link to supporting materials

# Gap Detection Reference

This reference provides detailed guidance on identifying, classifying, and resolving Context Brain coverage gaps. Load when gaps are identified during development.

---

## Gap Severity Levels

### 🔴 Critical Gaps (Blocking)

Critical gaps **must be resolved before commit**. They represent violations of the Three Laws or missing documentation that will cause immediate problems.

| Gap Type | Description | Example |
|----------|-------------|---------|
| **New component without docs** | Component created but no AGENTS.md exists | Created `PaymentFlow/PaymentFlow.tsx` with no AGENTS.md |
| **Breaking change undocumented** | Component behavior or API changed but docs not updated | Changed `onSave` prop to `onSubmit` but AGENTS.md still shows `onSave` |
| **New pattern not captured** | Established a new pattern that others will follow, not documented | Introduced async validation pattern used nowhere else, no Domain Guide coverage |

**Resolution requirement:** Cannot proceed with commit until resolved.

### 🟡 Moderate Gaps (Recommended)

Moderate gaps should be fixed but don't block commit. They represent documentation drift that will cause confusion if left unaddressed.

| Gap Type | Description | Example |
|----------|-------------|---------|
| **Stale component docs** | AGENTS.md exists but is outdated | Props table missing recently added props |
| **Outdated Domain Guide reference** | Domain Guide references deprecated patterns | Guide shows old state management approach |
| **Inaccurate examples** | Code examples no longer work | Example uses removed API |

**Resolution recommendation:** Fix now or create follow-up task.

### 🟢 Minor Gaps (Noted)

Minor gaps are nice-to-haves. They represent areas where documentation could be improved but absence doesn't cause problems.

| Gap Type | Description | Example |
|----------|-------------|---------|
| **Sparse area coverage** | Working in area with minimal docs | `/utils/pricing/` has no documentation but logic is simple |
| **Missing nice-to-haves** | Could add more examples or detail | Component AGENTS.md has one example, could have edge case examples |
| **No Domain Guide for simple area** | Area follows obvious patterns | No Domain Guide for straightforward CRUD operations |

**Resolution:** Optional, address if time permits.

---

## Critical Gap Handling

When critical gaps are detected, follow this protocol:

### Step 1: Report in Activity Log

```
**Gaps Identified:**
- 🔴 PaymentFlow/ created without AGENTS.md — **BLOCKING**
- 🔴 New async validation pattern not in Domain Guide — **BLOCKING**

**Status:** ⛔ Blocked — 2 critical gaps require resolution
```

### Step 2: State Required Actions

```
**Required Actions:**
1. Create PaymentFlow/AGENTS.md
2. Update .agent/domains/forms.md with async validation pattern 
   OR create new Domain Guide for validation patterns

Resolve critical gaps to proceed with commit.
```

### Step 3: Offer Assistance

For each critical gap, offer to help:

- **Missing AGENTS.md:** "Want me to generate PaymentFlow/AGENTS.md?"
- **Missing Domain Guide update:** "Want me to draft the async validation section for forms.md?"
- **Breaking change:** "Want me to update the AGENTS.md to reflect the new API?"

### Step 4: Verify Resolution

After user addresses gaps (or accepts generated docs):

```
**Gaps Resolved:**
- ✓ PaymentFlow/AGENTS.md — created
- ✓ .agent/domains/forms.md — updated with async validation

**Status:** ✅ Ready to commit
```

---

## Moderate Gap Handling

### Report Format

```
**Gaps Identified:**
- 🟡 UserProfile/AGENTS.md lists `onSave` prop but component now uses `onSubmit`
- 🟡 .agent/domains/api-patterns.md references deprecated fetch wrapper

**Recommendation:** Update documentation to reflect current state.
```

### Offer But Don't Block

```
**Status:** Ready to commit (recommended fixes noted)

Want me to fix these documentation gaps before you commit?
```

### If User Declines

Note for future but proceed:

```
Proceeding with commit. Moderate gaps noted for future cleanup.
```

---

## Minor Gap Handling

### Report Format (Concise)

```
**Gaps Noted:**
- 🟢 /utils/pricing/ has no documentation — consider adding if logic grows

**Status:** Ready to commit
```

### No Action Required

Minor gaps don't require resolution or offers. Simply note for awareness.

---

## Gap Detection Triggers

Actively check for gaps when:

| Trigger | What to Check |
|---------|---------------|
| **Creating new component** | Does AGENTS.md exist for it? |
| **Modifying component** | Is AGENTS.md still accurate? |
| **Establishing new pattern** | Is it documented in a Domain Guide? |
| **Changing component API** | Are props/behavior documented correctly? |
| **Reading stale documentation** | Law of Reciprocity — flag and fix |
| **Working in undocumented area** | Note sparse coverage |

---

## Example: Full Activity Log with Gaps

```
## Context Brain Activity

**Referenced:**
- AGENTS.md — project conventions, component structure
- .agent/domains/component-architecture.md — composition patterns
- .agent/domains/forms.md — form handling patterns

**Updated:**
- .agent/domains/forms.md — added async validation section

**Created:**
- PaymentFlow/AGENTS.md — new component documentation
- PaymentFlow/PaymentFlow.tsx — new component

**Gaps Identified:**
- 🟡 UserProfile/AGENTS.md — `onSave` should be `onSubmit` (modified but not updated)
- 🟢 /utils/validation/ — no documentation exists

**Status:** Ready to commit (1 recommended fix)

Want me to update UserProfile/AGENTS.md before you commit?
```

---

## Gap Patterns to Watch For

### Pattern: Orphaned Components

**Signal:** Component directory with code but no AGENTS.md
**Severity:** 🔴 Critical if new, 🟡 Moderate if existing
**Action:** Create AGENTS.md

### Pattern: Documentation Drift

**Signal:** AGENTS.md content doesn't match code reality
**Severity:** 🔴 Critical if breaking change, 🟡 Moderate otherwise
**Action:** Update AGENTS.md

### Pattern: Undocumented Patterns

**Signal:** Code follows a pattern not described in any Domain Guide
**Severity:** 🔴 Critical if new pattern, 🟢 Minor if well-established elsewhere
**Action:** Update or create Domain Guide

### Pattern: Stale References

**Signal:** Documentation links to files that don't exist or have moved
**Severity:** 🟡 Moderate
**Action:** Fix references

### Pattern: Modified ADR

**Signal:** Accepted ADR content was changed (not just status)
**Severity:** 🔴 Critical — violates Law of Immutability
**Action:** Revert changes, create superseding ADR if decision changed

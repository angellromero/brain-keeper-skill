# Context Brain Initialization

This reference covers bootstrapping Context Brain in new or existing projects. Load this when initialization is needed.

---

## Detection

When starting work in any project, check for Context Brain presence:

1. Does `AGENTS.md` exist at project root?
2. Does `.agent/` directory exist?

**If neither exists → This project needs initialization.**

---

## Initialization Triggers

Activate initialization when:

- User explicitly requests: "set up Context Brain," "initialize documentation," "create AGENTS.md"
- Agent detects no Context Brain and user is about to create significant code
- User asks "where should I document this?" in a project without Context Brain
- New project is being created from scratch

---

## Initialization Process

### Step 1: Scaffold the Structure

Create the full Context Brain directory structure:

```
project-root/
├── AGENTS.md              ← Create this (populated)
└── .agent/
    ├── adrs/              ← Create empty directory
    ├── domains/           ← Create empty directory
    ├── guides/            ← Create empty directory
    └── templates/         ← Create empty directory
```

### Step 2: Gather Information (Inferential + Interactive)

**First, scan the project for discoverable information:**

| Source | What to Extract |
|--------|-----------------|
| `package.json` | Project name, dependencies, scripts |
| `tsconfig.json` | TypeScript configuration |
| `requirements.txt` / `pyproject.toml` | Python dependencies |
| `Cargo.toml` | Rust configuration |
| Directory structure | App organization, monorepo detection |
| Existing README | Project description, setup instructions |

**Then, ask the user for what couldn't be inferred:**

- "What's the primary purpose of this project?"
- "Are there critical rules the team follows?"
- "Any environment setup requirements I should document?"

**Do not ask for information that's already discoverable.** Respect the user's time.

### Step 3: Generate Root AGENTS.md

Using the gathered information, populate the template from `references/template-root-agents.md`.

Apply verbosity calibration:
- Tech Stack: List what's actually used, not aspirational
- Commands: Only include commands that exist and work
- Project Structure: Reflect actual layout, not ideal state
- Critical Rules: Only genuinely critical items (3-5 max)

### Step 4: Offer Audit (For Existing Projects)

If the project already has code but no Context Brain:

```
## Initialization Complete

I've created the Context Brain structure. Since this project has existing code, 
would you like me to:

1. **Audit for documentation gaps** — Identify components that need AGENTS.md files
2. **Recommend initial Domain Guides** — Based on patterns I observe in the code
3. **Identify potential ADRs** — Decisions that appear to have been made but aren't documented

Which would be helpful?
```

---

## Initialization Output

After initialization, report what was created:

```
## Context Brain Initialized

**Created:**
- ✓ AGENTS.md (root entry point)
- ✓ .agent/adrs/ (ready for ADRs)
- ✓ .agent/domains/ (ready for Domain Guides)
- ✓ .agent/guides/ (ready for How-To Guides)
- ✓ .agent/templates/ (ready for templates)

**Next Steps:**
1. Review AGENTS.md and refine any inferred information
2. Create your first ADR when you make an architectural decision
3. Create Domain Guides as patterns emerge
4. Add AGENTS.md to components as you build them

The Context Brain is ready. I'll help maintain it from here.
```

---

## Post-Initialization

Once initialized, the main Brain Keeper skill takes over for ongoing maintenance. The Three Laws and always-active behaviors apply from this point forward.

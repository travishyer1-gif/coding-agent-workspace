# Coding Agent Workspace

**Purpose:** Structured environment for building real products with AI coding agents (Claude Code, Codex, Cursor, etc.)

**Framework:** AIEDGE "Build Any App: The Technical Co-Founder" by Miles Deutscher

---

## Directory Structure

```
coding-agent/
├── SOUL.md                 # Core framework - read this first
├── README.md               # This file
├── projects/               # Active and completed projects
│   └── <project-name>/     # Each project gets its own folder
│       ├── PROJECT.md      # Project brief and status
│       ├── src/            # Source code
│       ├── docs/           # Documentation
│       └── README.md       # Project-specific instructions
├── templates/              # Reusable templates
│   └── PROJECT_TEMPLATE.md # Template for new projects
└── docs/                   # Reference materials
    └── wisp-context.md     # WISP domain knowledge
```

---

## Getting Started

### 1. Read SOUL.md
This is the framework that defines how your coding agent should work with you.

### 2. Create a New Project
```bash
cd ~/clawd/coding-agent/projects
mkdir my-project-name
cp ../templates/PROJECT_TEMPLATE.md my-project-name/PROJECT.md
```

### 3. Fill Out PROJECT.md
Define what you're building, why, and how serious you are about it.

### 4. Start Your Coding Agent
Open your preferred coding environment (Claude Code, Cursor, etc.) and:
- Load SOUL.md as context
- Load your PROJECT.md
- Start building

---

## WISP Projects

For projects related to the WISP business:

### Domain Context Available
- Network infrastructure data (`~/clawd/data/work/`)
- Customer database (`customer-lookup.db`)
- UISP API integration
- VISP billing system access
- Existing tools and scripts (`~/clawd/scripts/`)

### Common Project Types
- Customer portal development
- Network monitoring dashboards
- Automated reporting tools
- Integration improvements
- Internal admin tools

---

## Workflow

1. **Discovery** - Define what you actually need
2. **Planning** - Outline version 1 scope
3. **Building** - Iterative development with check-ins
4. **Polish** - Professional finish
5. **Handoff** - Deploy, document, and plan v2

---

## Access from Work PC

This directory is located at: `~/clawd/coding-agent/`

**To access from your work PC:**
1. Ensure you can reach this Mac (Tailscale: 100.92.17.69)
2. Use VS Code Remote SSH or similar
3. Or sync via Git if you've pushed this to a repo

---

## Tips

- **Keep projects isolated** - Each project gets its own folder
- **Version control** - Use git for each project
- **Document as you go** - Future-you will thank you
- **Start small** - MVP first, features later
- **Real products** - Not prototypes, shipping code

---

*Created: 2026-02-06*  
*Last Updated: 2026-02-06*

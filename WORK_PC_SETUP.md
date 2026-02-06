# Work PC Setup Guide

**Location on Mac mini:** `~/clawd/coding-agent/`  
**Mac mini Tailscale IP:** `100.92.17.69`

---

## Option 1: VS Code Remote SSH (Recommended)

### Setup
1. Install VS Code on your work PC
2. Install "Remote - SSH" extension
3. Connect to Mac mini:
   ```
   ssh travis@100.92.17.69
   ```
4. Open folder: `/Users/frobertomaya/clawd/coding-agent`

### Benefits
- Full IDE experience
- Terminal access
- Git integration
- Extension support

---

## Option 2: Direct SSH + Local Editor

### Access Files
```bash
# SSH into Mac mini
ssh travis@100.92.17.69

# Navigate to coding agent
cd ~/clawd/coding-agent

# List projects
ls -la projects/

# Edit files with nano/vim
nano projects/my-project/PROJECT.md
```

### Sync to Work PC
```bash
# From work PC, pull files
scp -r travis@100.92.17.69:~/clawd/coding-agent/projects/my-project ./

# Push changes back
scp -r ./my-project travis@100.92.17.69:~/clawd/coding-agent/projects/
```

---

## Option 3: Git Repository

### Setup
```bash
# On Mac mini
cd ~/clawd/coding-agent
git init
git add .
git commit -m "Initial coding agent workspace"

# Push to GitHub/GitLab (optional)
git remote add origin <your-repo-url>
git push -u origin main
```

### From Work PC
```bash
# Clone the repo
git clone <your-repo-url>
cd coding-agent

# Work on projects
# ... make changes ...

# Push when done
git add .
git commit -m "Project updates"
git push
```

### Benefits
- Version control
- Work from anywhere
- Collaboration ready
- Backup built-in

---

## Quick Start Workflow

### 1. Start a New Project
```bash
# SSH into Mac mini
ssh travis@100.92.17.69
cd ~/clawd/coding-agent

# Create project
mkdir projects/my-wisp-dashboard
cp templates/PROJECT_TEMPLATE.md projects/my-wisp-dashboard/PROJECT.md

# Edit project brief
nano projects/my-wisp-dashboard/PROJECT.md
```

### 2. Start Coding Agent
- Open Claude, Cursor, or your preferred coding AI
- Load `SOUL.md` as context
- Load `projects/my-wisp-dashboard/PROJECT.md`
- Load `docs/wisp-context.md` (if WISP-related)
- Start building

### 3. Iterate
- Agent builds in stages
- Review and test as you go
- Make decisions at checkpoints
- Keep PROJECT.md updated with status

---

## File Access Cheat Sheet

### Core Files
```
~/clawd/coding-agent/
├── SOUL.md              ← Read this first (agent framework)
├── README.md            ← Overview and workflow
├── WORK_PC_SETUP.md     ← This file
```

### Templates
```
templates/
└── PROJECT_TEMPLATE.md  ← Copy for each new project
```

### WISP Context (for work projects)
```
docs/
└── wisp-context.md      ← Domain knowledge for WISP tools
```

### Your Projects
```
projects/
└── <project-name>/
    ├── PROJECT.md       ← Project brief and status
    ├── src/             ← Your code
    ├── docs/            ← Documentation
    └── README.md        ← Usage instructions
```

---

## Tips

### For WISP Projects
- Load `docs/wisp-context.md` into your agent's context
- Reference existing tools in `~/clawd/scripts/`
- Access live data via APIs and databases
- Follow security guidelines (credentials in `~/.secrets/`)

### For General Projects
- Start with discovery phase (don't skip this!)
- Keep scope small for v1
- Test as you go
- Document for future-you

### Working Remotely
- Tailscale keeps connection stable
- VS Code Remote SSH is seamless
- Git gives you offline capability
- Keep backups of important work

---

## Troubleshooting

### Can't Connect via SSH
```bash
# Verify Mac mini is reachable
ping 100.92.17.69

# Check Tailscale status
tailscale status
```

### File Permissions
```bash
# On Mac mini, ensure you own the directory
sudo chown -R travis:staff ~/clawd/coding-agent
chmod -R 755 ~/clawd/coding-agent
```

### Git Conflicts
```bash
# If you're working from multiple locations
git fetch origin
git merge origin/main
# Resolve conflicts, then push
```

---

*Created: 2026-02-06*

# Build Your AI Agent: Claude Code Setup Guide

A practical guide to setting up Claude Code as your personal AI operating system. By the end of this, you'll have a persistent "brain" that Claude can read and write to, auto-synced to GitHub, with a CLAUDE.md that teaches it who you are and how you work.

---

## What You're Building

```
~/brain/                    # Your private GitHub repo (source of truth)
  CLAUDE.md                 # Who you are, how Claude should work with you
  todos.md                  # Running task list Claude can read and update
  memory/                   # Claude's self-improving notes
    MEMORY.md               # Index file (auto-loaded every session)
    tool-lessons.md          # What went wrong, how to fix it
    preferences.md           # Your feedback on Claude's output
  work/                     # Your work context (customers, projects, notes)
  skills/                   # Reusable workflows Claude can execute
  commands/                 # Quick-fire templates
  scripts/
    auto-sync.sh            # Cron job: commits and pushes changes every 10 min
    setup-claude.sh          # One-time script to wire Claude Code to your brain
  .github/workflows/        # Recurring automations (health reports, digests, etc.)
```

The key insight: Claude Code reads `~/CLAUDE.md` and `~/.claude/` on every session start. If you symlink those to a Git repo, your AI agent has persistent memory across sessions and machines.

---

## Step 1: Get Claude Code Running

### Install Claude Code
```bash
# Install via npm (requires Node.js 18+)
npm install -g @anthropic-ai/claude-code

# Or via Homebrew
brew install claude-code
```

### Subscribe
You need a Claude subscription with Claude Code access. Options:
- **Claude Pro** ($20/mo) - limited usage
- **Claude Max 5x** ($100/mo) - recommended, plenty of headroom
- **Claude Max 20x** ($200/mo) - heavy usage

### First Run
```bash
# Launch from your home directory
cd ~
claude

# It will walk you through authentication
```

---

## Step 2: Create Your Brain Repo

### Initialize the repo
```bash
mkdir ~/brain && cd ~/brain
git init
```

### Create the directory structure
```bash
mkdir -p memory work skills commands scripts notes reference .github/workflows
```

### Create your CLAUDE.md
This is the most important file. It tells Claude who you are and how to work with you. Drop this at `~/brain/CLAUDE.md` and customize it:

```markdown
# [Your Name]

## Communication
- [Your preferred tone: concise, detailed, casual, formal]
- [Any writing rules: no jargon, no emojis, etc.]
- [Push back when warranted? Or always agree?]

## Work
- [Your role, company, team]
- [What you're working on right now]
- [Work email vs personal email]

## File System
- **Brain is source of truth.** Write to `~/brain/` first.
- Todos: `~/brain/todos.md`
- Memory: `~/brain/memory/`
- Work context: `~/brain/work/`
- Save generated files to `~/Downloads`

## Session Rules
- Read relevant context files before starting work on a topic
- Update todos.md when new tasks come up
- Update memory files when you learn something new about tools or my preferences
- Ask on ambiguous requests. Act on clear tasks.
```

### Create the memory index
Create `~/brain/memory/MEMORY.md`:
```markdown
# Claude Memory

## Key Facts
- [Will be populated as Claude learns about you]

## Tool Lessons
- See tool-lessons.md for tool-specific notes

## Preferences
- See preferences.md for output/format feedback
```

Create the companion files:
```bash
echo "# Tool Lessons\n\nLog tool failures and correct approaches here." > ~/brain/memory/tool-lessons.md
echo "# Preferences\n\nLog feedback on format, tone, and approach here." > ~/brain/memory/preferences.md
echo "# Debugging\n\nLog recurring issues and solutions here." > ~/brain/memory/debugging.md
```

### Create your todos file
```bash
echo "# Todos\n\nClaude can read and update this file across sessions." > ~/brain/todos.md
```

---

## Step 3: Wire Claude Code to Your Brain

### Symlink CLAUDE.md to your home directory
Claude Code looks for `~/CLAUDE.md` on every session start:
```bash
ln -sf ~/brain/CLAUDE.md ~/CLAUDE.md
```

### Set up Claude's memory directory
Claude Code auto-loads memory from a specific path. Copy your brain's memory there:
```bash
MEMORY_DST="$HOME/.claude/projects/-Users-$(whoami)/memory"
mkdir -p "$MEMORY_DST"
cp ~/brain/memory/MEMORY.md "$MEMORY_DST/"
cp ~/brain/memory/tool-lessons.md "$MEMORY_DST/"
cp ~/brain/memory/preferences.md "$MEMORY_DST/"
cp ~/brain/memory/debugging.md "$MEMORY_DST/"
```

### (Optional) Symlink skills and commands
If you build reusable skills later:
```bash
# Back up existing directories if they exist
[ -d ~/.claude/skills ] && mv ~/.claude/skills ~/.claude/skills.bak
[ -d ~/.claude/commands ] && mv ~/.claude/commands ~/.claude/commands.bak

ln -sfn ~/brain/skills ~/.claude/skills
ln -sfn ~/brain/commands ~/.claude/commands
```

### Automate this with a setup script
Save this as `~/brain/scripts/setup-claude.sh` so you can re-run it on any machine:

```bash
#!/bin/bash
set -e

BRAIN_DIR="$HOME/brain"
CLAUDE_DIR="$HOME/.claude"
MEMORY_SRC="$BRAIN_DIR/memory"
MEMORY_DST="$CLAUDE_DIR/projects/-Users-$(whoami)/memory"

echo "Wiring Claude Code to Brain..."

# Symlink CLAUDE.md
ln -sf "$BRAIN_DIR/CLAUDE.md" "$HOME/CLAUDE.md"
echo "Linked ~/CLAUDE.md -> ~/brain/CLAUDE.md"

# Symlink skills
if [ -d "$CLAUDE_DIR/skills" ] && [ ! -L "$CLAUDE_DIR/skills" ]; then
    mv "$CLAUDE_DIR/skills" "$CLAUDE_DIR/skills.bak"
fi
ln -sfn "$BRAIN_DIR/skills" "$CLAUDE_DIR/skills"
echo "Linked ~/.claude/skills/ -> ~/brain/skills/"

# Symlink commands
if [ -d "$CLAUDE_DIR/commands" ] && [ ! -L "$CLAUDE_DIR/commands" ]; then
    mv "$CLAUDE_DIR/commands" "$CLAUDE_DIR/commands.bak"
fi
ln -sfn "$BRAIN_DIR/commands" "$CLAUDE_DIR/commands"
echo "Linked ~/.claude/commands/ -> ~/brain/commands/"

# Copy memory files
mkdir -p "$MEMORY_DST"
for f in MEMORY.md tool-lessons.md preferences.md debugging.md; do
    [ -f "$MEMORY_SRC/$f" ] && cp "$MEMORY_SRC/$f" "$MEMORY_DST/$f"
done
echo "Copied memory files"

echo "Done. Claude Code is now using Brain as source of truth."
```

---

## Step 4: Auto-Sync to GitHub

This is what keeps your brain backed up and accessible from any machine. A cron job checks for changes every 10 minutes, commits them, and pushes to GitHub.

### Push your brain to GitHub
```bash
cd ~/brain

# Create a private repo on GitHub first (via github.com or gh CLI)
gh repo create Brain --private --source=. --remote=origin

# Or if you already created it:
git remote add origin git@github.com:YOUR_USERNAME/Brain.git

# Initial commit
git add -A
git commit -m "initial brain setup"
git push -u origin main
```

### Create the auto-sync script
Save as `~/brain/scripts/auto-sync.sh`:

```bash
#!/bin/bash
# Auto-sync ~/brain to GitHub every 10 minutes via cron

cd ~/brain || exit 1

# Skip if rebase in progress
if [[ -d .git/rebase-merge || -d .git/rebase-apply ]]; then
    echo "$(date '+%Y-%m-%d %H:%M') - Rebase in progress, skipping"
    exit 0
fi

# Stash local changes, pull remote, restore, commit, push
STASHED=false
if [[ -n $(git status --porcelain) ]]; then
    git stash -q
    STASHED=true
fi

git fetch origin main -q
if ! git rebase origin/main -q 2>/dev/null; then
    git rebase --abort 2>/dev/null
    if $STASHED; then git stash pop -q 2>/dev/null; fi
    echo "$(date '+%Y-%m-%d %H:%M') - Rebase conflict, needs manual merge"
    exit 1
fi

if $STASHED; then
    git stash pop -q 2>/dev/null || {
        echo "$(date '+%Y-%m-%d %H:%M') - Stash conflict, needs manual merge"
        exit 1
    }
fi

if [[ -n $(git status --porcelain) ]]; then
    git add -A
    git commit -q -m "auto-sync $(date '+%Y-%m-%d %H:%M')"
fi

if [[ -n $(git log origin/main..HEAD --oneline) ]]; then
    git push origin main -q
fi
```

### Install the cron job
```bash
chmod +x ~/brain/scripts/auto-sync.sh

# Add to crontab (runs every 10 minutes)
(crontab -l 2>/dev/null || true; echo "*/10 * * * * $HOME/brain/scripts/auto-sync.sh >> $HOME/brain/scripts/sync.log 2>&1") | crontab -

# Verify
crontab -l
```

### Add a .gitignore
Create `~/brain/.gitignore`:
```
.DS_Store
*.tmp
*~
```

---

## Step 5: Add MCP Servers (Optional but Powerful)

MCP (Model Context Protocol) servers give Claude access to external tools: your calendar, email, documents, search, etc.

### What MCPs are
Think of them as plugins. Claude Code can connect to MCP servers that expose tools like "search my email" or "look up a meeting." You configure them in `~/.claude/settings.json`.

### Example: Adding a search MCP
```json
// ~/.claude/settings.json
{
  "mcpServers": {
    "my-search": {
      "command": "npx",
      "args": ["-y", "@anthropic-ai/mcp-server-web-search"]
    }
  }
}
```

### Glean MCP (for Glean employees)
If you have access to Glean's MCP server, it gives Claude access to your company's entire knowledge graph: Slack, email, docs, meeting transcripts, Salesforce, etc. This is where the real magic happens for work context.

### Other useful MCPs
- **Google Calendar** - read/create events
- **Gmail** - search and draft emails
- **GitHub** - interact with repos, PRs, issues
- **File system** - read/write files beyond the working directory

Check [modelcontextprotocol.io](https://modelcontextprotocol.io) for the full directory.

---

## Step 6: Build Your First Skill

Skills are markdown files that teach Claude how to do a specific task. They live in `~/brain/skills/` and get auto-loaded via the symlink.

### Example: Meeting Prep Skill
Create `~/brain/skills/meeting-prep/SKILL.md`:

```markdown
# Meeting Prep

Prepare a briefing for an upcoming meeting.

## Trigger
When the user says "prep me for [meeting]" or "brief me on [account]"

## Steps
1. Check local files at ~/brain/work/ for any existing context
2. Search for recent communications and documents related to the topic
3. Look up the meeting on the calendar for attendees and agenda
4. Synthesize into a brief with:
   - Key context and background
   - Open action items
   - Suggested talking points
   - Any risks or things to watch for

## Output Format
Concise bullet points. No fluff. Lead with the most important thing.
```

### Example: Quick Log Skill
Create `~/brain/skills/log/SKILL.md`:

```markdown
# Quick Log

Capture a quick activity note.

## Trigger
/log [topic] [what happened]

## Steps
1. Parse the topic and content from the user's message
2. Append a dated entry to the relevant file in ~/brain/work/ or ~/brain/notes/
3. If new action items were mentioned, add them to ~/brain/todos.md

## Format
## YYYY-MM-DD
- [bullet points of what happened]
```

---

## Step 7: Rules Files (Teaching Claude Your Preferences)

Rules files live in `~/.claude/rules/` and get loaded on every session. Use them for behavioral instructions that should always apply.

### Example: `~/.claude/rules/work-context.md`
```markdown
# Work Context

## My Role
- [Your role and what you do day-to-day]
- [Key projects or accounts you manage]

## How I Work
- I prefer [concise/detailed] responses
- Always [read context files before starting / just dive in]
- When I say "remember this," add it to ~/brain/notes/ or ~/brain/todos.md
- When I mention a task I need to do, add it to ~/brain/todos.md
```

### Example: `~/.claude/rules/session-rules.md`
```markdown
# Session Rules

- Read relevant context files before starting work on a topic
- After finishing substantive work, update the relevant log file in ~/brain/
- Parallelize independent lookups when possible (use subagents)
- Ask before pushing to GitHub
```

---

## How It All Fits Together

```
You open a terminal and type: claude

Claude Code starts up and automatically reads:
  1. ~/CLAUDE.md              -> knows who you are
  2. ~/.claude/rules/*.md     -> knows your preferences and rules
  3. ~/.claude/.../MEMORY.md  -> remembers past sessions

You say: "prep me for my meeting with Acme Corp"

Claude:
  - Reads ~/brain/work/customers/acme-corp/ for local context
  - Uses MCP tools to search recent emails, docs, transcripts
  - Synthesizes a brief with talking points

After the meeting, you say: "log that we discussed X, Y, Z. Action item: send proposal by Friday"

Claude:
  - Appends a dated entry to ~/brain/work/customers/acme-corp/log.md
  - Adds "Send Acme proposal by Friday" to ~/brain/todos.md

10 minutes later, auto-sync commits and pushes to GitHub.

Next session (maybe on a different machine), Claude picks up right where you left off.
```

---

## Quick Reference

| What | Where |
|------|-------|
| Master config | `~/brain/CLAUDE.md` (symlinked to `~/CLAUDE.md`) |
| Behavioral rules | `~/.claude/rules/*.md` |
| Memory (auto-loaded) | `~/.claude/projects/-Users-YOU/memory/MEMORY.md` |
| Memory (canonical) | `~/brain/memory/` |
| Todos | `~/brain/todos.md` |
| Skills | `~/brain/skills/` (symlinked to `~/.claude/skills/`) |
| Commands | `~/brain/commands/` (symlinked to `~/.claude/commands/`) |
| Auto-sync | `~/brain/scripts/auto-sync.sh` (cron, every 10 min) |
| Setup script | `~/brain/scripts/setup-claude.sh` (run once per machine) |
| GitHub Actions | `~/brain/.github/workflows/` |

## Useful Commands

```bash
# Start a new session
claude

# Continue your last session
claude --continue

# Rename your current session (makes it easier to find later)
# Inside Claude Code, type:
/rename meeting-prep-acme

# Check auto-sync logs
tail -20 ~/brain/scripts/sync.log
```

## Tips

1. **Start small.** Get CLAUDE.md and the brain repo working first. Add skills and MCPs as you find patterns worth automating.

2. **Let Claude update its own memory.** When something goes wrong with a tool or you correct Claude's output, it should log that in memory files so it doesn't repeat the mistake.

3. **Use markdown for everything.** Claude reads and writes markdown natively. It's version-controlled, diffable, and human-readable.

4. **Parallelize.** If you need Claude to do 5 independent lookups, it can spin up subagents to do them all at once instead of sequentially.

5. **Build skills for repetitive work.** If you do the same type of task more than twice, write a skill for it. Future you will thank you.

6. **Your CLAUDE.md is a living document.** Update it as your role, projects, and preferences change. The more accurate it is, the better Claude performs.

---

*Built by Harry Toig. Questions? Reach out.*

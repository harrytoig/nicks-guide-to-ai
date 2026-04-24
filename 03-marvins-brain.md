# Marvin's Brain

> *"I've got this terrible pain in all the diodes down my left side."*
> - Marvin, the Paranoid Android

Marvin had a brain the size of a planet and spent most of it sulking. You can have that, too, running quietly in a terminal window on your laptop, and we can make yours more useful than his.

This is my Claude Code setup. Steal any of it. All of it.

---

## What is Claude Code?

A command-line tool from Anthropic. You type plain English, it writes code, edits files, runs commands, and hands back results. It is better than ChatGPT for anything involving your actual filesystem: writing docs, editing code, automating workflows, building projects from zero.

It is the single biggest productivity unlock I've found in the last two years. I use it for customer work, my finances, health tracking, side projects, writing this guide, and most meaningful typing I do at a computer. Pay the $20 a month for Claude and use the hell out of it.

---

## Install

```bash
npm install -g @anthropic-ai/claude-code
```

You need Node.js. If you don't have it, `brew install node`. If you don't have Homebrew, install that first (the internet will tell you how).

Then `cd` to a folder and type `claude`. That's it.

---

## The 6 Things Worth Configuring

You can ignore all of this for your first week. Just start using Claude Code on real tasks. When it gets frustrating in the same way twice, come back here.

### 1. CLAUDE.md

A `CLAUDE.md` file in the root of any project gets read every session. Use it to tell Claude who you are, how you want to be talked to, what tools to prefer, what to avoid.

Put one at the top of your home directory (`~/CLAUDE.md`) so Claude knows who you are across every project.

Starter template, adapted from mine:

```markdown
# [Your Name]

## Communication
- Concise. No fluff.
- No em dashes.
- Dry honesty preferred over corporate language.

## Work
- [Your role, your company, your manager]
- [What you're working on right now]

## File System
- [Where your notes live]
- [Where generated files should go, e.g. ~/Downloads]

## Session Rules
- Ask on ambiguous requests. Act on clear tasks.
- Always confirm before pushing to GitHub.
```

### 2. Rules Files

For longer preferences, split them into `~/.claude/rules/*.md`, one file per topic. Mine are: `personal-context.md`, `tool-routing.md`, `parallel-execution.md`, `memory-and-persistence.md`, `reminders.md`. They auto-load into every session.

This keeps `CLAUDE.md` short without losing detail.

### 3. Slash Commands

A slash command is a reusable prompt you invoke with `/name`. Create one by dropping a markdown file into `~/.claude/commands/` (or wherever yours live). Example:

```markdown
---
name: morning
description: Daily morning startup
---
Pull my calendar for today. Check my inbox for anything urgent. Summarize overnight news from my top 3 AI sources. Draft a top-of-day plan with three priorities.
```

Now typing `/morning` runs that every time. Good commands to build:

- `/morning`: daily startup
- `/evening`: end-of-day shutdown routine
- `/standup`: what did I do yesterday, what am I doing today
- `/brief [customer]`: pre-meeting briefing
- `/log`: dump today's work to a dated log file

If you use the same prompt three times, make it a command.

### 4. Skills

Skills are commands' more structured cousin. They can be multi-step, can spawn sub-agents, and can ship with their own domain knowledge. Use skills for complex repeatable workflows. If a command gets longer than 30 lines or needs sub-steps, promote it to a skill.

### 5. MCPs (Model Context Protocols)

MCPs are plug-in tool servers that let Claude talk to external services. Install a few early:

- **Google Calendar / Gmail MCP**: personal calendar and email access.
- **Granola MCP**: meeting transcripts, if you use Granola.
- **Plaid MCP**: personal finance automation.
- **Glean MCP**: work knowledge if your company has Glean.
- **Computer Use MCP**: let Claude control your desktop. Use sparingly. Amazing when it works.

MCPs install via Claude Desktop config or CLI flags. This is where the rabbit hole begins.

### 6. Memory

Claude Code writes auto-memory notes to `~/.claude/projects/[project]/memory/` across sessions. It remembers your preferences, your corrections, tool mistakes, and so on. You can also prompt it directly: "remember that I prefer X over Y."

The pattern I use:

- `MEMORY.md` is the index (keep it under 200 lines).
- Topic files for `tool-lessons.md`, `preferences.md`, `debugging.md`.
- Claude updates them automatically when corrected or when something goes sideways.

---

## Things to Try in Your First Week

- Ask Claude to read your entire downloads folder and categorize what's in it.
- Have it summarize your last 30 days of journal entries and tell you what you're obsessing over.
- Let it build a one-page website from a rough description and deploy it to Vercel.
- Write a slash command that runs your morning routine: calendar check, top-of-feed news, day plan.
- Point it at an annoying manual process you do weekly and have it write the bash script.

Use Claude Code as your primary interface for a week. You won't want to go back.

---

## Where to Go Deeper

- **Anthropic's Claude Code docs:** https://docs.claude.com/en/docs/claude-code/overview
- **Boris Cherny on Lenny's Podcast**. Head of Claude Code on the product philosophy. See [Ear to the Ground](./04-ear-to-the-ground.md).
- **Anthropic's "Code w/ Claude" YouTube series**: the applied team walks through real workflows.

---

## One Warning

Claude Code can do destructive things. Don't give it unsupervised access to production databases. Don't let it `rm -rf` blindly. Always confirm before a `git push`. Keep your towel nearby.

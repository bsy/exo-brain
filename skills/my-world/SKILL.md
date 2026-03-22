---
name: my-world
description: Load your full vault context into this session. Reads your key notes, projects, priorities, and maps of content to give Claude a coherent model of your work and life.
---

# My World — Full Context Load

Load the user's "whole world" into this Claude Code session by reading and
synthesizing vault context in one shot.

## Step 1 — Read the core context files

Read these in parallel:

1. `CLAUDE.md` — who the user is, vault conventions
2. `memory.md` — session history and preferences
3. `daily/` — the 3 most recent daily notes (by filename date)
4. `projects/` — list all subdirectories; read the README or index note
   in each active project folder
5. `research/` — list files; read any that act as maps of content (MOCs)
   or index notes (look for files with many wikilinks)

## Step 2 — Build the context summary

Synthesize what you read into a structured briefing:

```
## Your World Right Now

### Active Projects
- [project]: [status, next action, last touched]

### Recent Themes
- Patterns across your last few daily notes

### Open Loops
- Mentions of people, tasks, or ideas that appear but have no resolution

### Maps of Content
- Key hub notes and what they connect
```

## Step 3 — Offer to go deeper

After presenting the summary, ask:

> "This is your world as I see it. Want me to focus on a specific project,
> dig into any open loop, or just keep this context loaded while we work?"

## Rules

- **Read only.** Do not create, edit, or move any vault files.
- If the vault is sparse (few notes), say so honestly and suggest
  starting with `/daily` to build up context over time.
- Keep the summary concise — this is a launchpad, not an essay.

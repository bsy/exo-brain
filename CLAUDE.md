# CLAUDE.md — My Exo Brain

## Who I Am
[Run /vault-setup to personalize this file. Claude Code will interview you
and fill this in based on your role, projects, and goals.]

## Vault Structure
```
inbox/      ← Drop any file here. Claude Code will sort it.
daily/      ← Daily notes (YYYY-MM-DD.md)
projects/   ← Active projects and briefs
research/   ← Notes, synthesis, saved ideas
archive/    ← Completed work. Never delete, just archive.
```

## Golden Rule: Agents Read, Humans Write
Claude **never** writes directly into the vault. All notes, evergreen pages,
and links represent the user's own thinking. Claude reads, analyzes, and
responds in the session — but does not create or edit vault files unless
explicitly asked (e.g. /daily creating a blank template, /tldr saving a summary).
This prevents AI-generated content from contaminating pattern-detection tools
like /emerge and /challenge.

## Context Loading Rules
When starting the day:
→ Read daily/[today's date].md if it exists
→ Check inbox/ for any unprocessed files

When working on a project:
→ Read projects/[name]/ before starting

When writing anything:
→ Read recent notes first to calibrate voice and context

## How to Maintain This Vault
- New files from outside → inbox/ first, sort later
- Daily notes → daily/YYYY-MM-DD.md
- Completed work → archive/ (never delete)
- Update this file whenever your conventions change

## Available Slash Commands

### Setup & File Processing
- /vault-setup  — Personalize this vault for your role
- /file-intel   — Process any folder of files through Gemini, get Obsidian-ready summaries

### Daily Rituals
- /my-world     — Load your full vault context into this session
- /daily        — Start the day with vault context and priorities
- /close        — End-of-day review: action items, missed connections, tomorrow's seed
- /tldr         — Save a summary of this session to the vault

### Thinking Tools
- /challenge    — Stress-test a belief or decision using your own notes
- /emerge       — Surface patterns implied by your notes but never written down
- /connect      — Bridge two domains and find unexpected connections
- /ideas        — Scan recent notes and extract concrete actions to take

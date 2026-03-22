<div align="center">

<img src="banner.svg" alt="Exo Brain" width="800"/>

**Your AI already knows everything. It just can't remember any of it.**

![macOS](https://img.shields.io/badge/macOS-✓-8A2BE2?style=flat-square) ![Windows](https://img.shields.io/badge/Windows-✓-8A2BE2?style=flat-square) ![Free](https://img.shields.io/badge/cost-free-8A2BE2?style=flat-square) ![One command](https://img.shields.io/badge/setup-one_command-8A2BE2?style=flat-square)

[Obsidian](https://obsidian.md) + [Claude Code](https://claude.ai/code) · Local · Private · One command

```
  Your files (PDFs, docs, notes)
          │
          ▼
  ┌───────────────────┐
  │   Obsidian vault  │  ← plain .md files on your computer
  │  inbox/  daily/   │
  │  projects/  ...   │
  └────────┬──────────┘
           │  Claude Code reads this folder
           ▼
  ┌───────────────────┐
  │   Claude Code     │  ← knows your projects, voice, context
  │   /vault-setup    │     before you type a single word
  │   /daily  /tldr   │
  └───────────────────┘
           │
           ▼
    AI that compounds.
    Session 1: knows your folders.
    Session 20: knows your work better
    than you consciously remember.
```

</div>

---

## Quick Start

### macOS

**One-liner** (paste into Terminal, hit Enter):

```bash
curl -fsSL https://raw.githubusercontent.com/bsy/exo-brain/main/setup.sh -o setup.sh && bash setup.sh
```

**Or clone it:**

```bash
git clone https://github.com/bsy/exo-brain.git
cd exo-brain
./setup.sh
```

> No git? Run `xcode-select --install` first.

---

### Windows

> **Need git?** Open **PowerShell** and run `git --version`. If nothing comes back, grab it from [git-scm.com](https://git-scm.com/download/win), accept all defaults, reopen PowerShell.

**One-liner:**

```powershell
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/bsy/exo-brain/main/setup.ps1" -OutFile setup.ps1; powershell -ExecutionPolicy Bypass -File setup.ps1
```

**Or clone it:**

```powershell
git clone https://github.com/bsy/exo-brain.git
cd exo-brain
powershell -ExecutionPolicy Bypass -File setup.ps1
```

> **"Running scripts is disabled"?** That's Windows being Windows. The `-ExecutionPolicy Bypass` flag handles it for this one run.
>
> **Python not found?** Grab it from [python.org/downloads](https://python.org/downloads). Tick **"Add Python to PATH"** on the first screen. Reopen PowerShell. Re-run.

---

The script does the rest. Obsidian, Claude Code, vault structure, optional file import — all of it.

---

## Why This Exists

We've all been here. You pick a note-taking app, spend a weekend organizing it, use it religiously for nine days, then never open it again. The notes rot. The system dies.

The tool was never the problem. **Maintenance was the problem.** You had to remember to feed the system, and you didn't, because you're busy doing actual work.

Exo Brain flips this. Wire [Obsidian](https://obsidian.md) to [Claude Code](https://claude.ai/code) and the system feeds itself:

- Claude **reads your vault** before every session — it already knows your projects, your context, your voice
- Claude **writes back to your vault** after working — summaries, decisions, and context get captured without you lifting a finger
- Existing files (PDFs, docs, slides) get **synthesized into clean notes** via Gemini 3 Flash
- Everything stays **on your machine** — plain markdown files, no cloud lock-in, no SaaS dependency

The result: an AI with long-term memory that gets sharper every time you use it. Not because of some magic retrieval system. Because it reads a folder of markdown files. The simplest thing that could possibly work.

---

## Already Have an Obsidian Vault?

Good. The script respects what's already there.

Point it at your existing vault and it'll add the missing pieces — 4 slash commands, a `CLAUDE.md` template, helper scripts — without touching a single existing note, plugin, or theme. It backs up your `CLAUDE.md` if you have one, shows you exactly what it plans to do, and asks before changing anything.

```
# macOS
./setup.sh
# When prompted: enter your vault path, e.g. ~/Documents/MyVault

# Windows
powershell -ExecutionPolicy Bypass -File setup.ps1
# When prompted: enter your vault path, e.g. C:\Users\You\MyVault
```

Then run `/vault-setup` in Claude Code. It interviews you and generates a personalized `CLAUDE.md` fitted to your structure.

> **Want to undo?** Delete `.claude/skills/`, `scripts/`, `CLAUDE.md`, and `memory.md` from your vault. Done. Your notes are untouched.
>
> **Safe to re-run.** Detects existing vaults, creates timestamped backups, only adds what's missing.

---

## What Gets Installed

| Component | What | Why |
|-----------|------|-----|
| **Obsidian** | Local markdown editor | Your notes are plain files on disk. No vendor, no subscription, yours forever. |
| **Claude Code** | AI terminal agent | Reads and writes directly in your vault. No copy-paste, no tab-switching. |
| **Python packages** | File processing libs | Gemini 3 Flash uses these to read PDFs, docs, and slides. |
| **Vault skills** | 4 slash commands | `/vault-setup` `/daily` `/tldr` `/file-intel` |
| **Obsidian Skills** *(opt-in)* | [Kepano's](https://github.com/kepano) official skills | Claude navigates your vault via the Obsidian CLI |

> **Nothing leaves your machine.** The vault is a local folder. Claude reads it locally. The only network call is optional Gemini file processing.

---

## Setup Walkthrough

```
Step 1 — Dependencies          Homebrew (Mac) or winget (Windows)
Step 2 — Obsidian              Free, local note-taking app
Step 3 — Claude Code           Anthropic's AI terminal
Step 4 — Python packages       For Gemini file processing
Step 5 — Vault creation        Folder structure + skills (local + global)
Step 6 — File import           Optional — Gemini synthesizes your existing docs
Step 7 — Obsidian Skills       Optional — Kepano's official Claude skills
```

---

## After Setup

**1. Turn on the Obsidian CLI**
```
Obsidian → Settings → General → Enable Command Line Interface
```

**2. Launch Claude Code**
```bash
cd ~/exo-brain && claude
```

**3. Personalize your vault**
```
/vault-setup
```

Claude interviews you — role, projects, goals — then builds a `CLAUDE.md` and slash commands tailored to how you actually work. A founder gets different folders than a developer. A consultant gets different commands than a student.

---

## Slash Commands

Four ship out of the box. More accumulate as you use the system.

| Command | Does |
|---------|------|
| `/vault-setup` | Interviews you, generates your personalized vault structure + CLAUDE.md + custom commands |
| `/daily` | Morning kickoff — reads or creates today's note, surfaces priorities, asks what's on deck |
| `/tldr` | End-of-session — captures decisions, takeaways, next actions into the right vault folder |
| `/file-intel` | Aim it at any folder — Gemini reads every file, generates Obsidian-ready summaries |

> Skills install both locally and globally (`~/.claude/skills/`), so they work from any directory.

---

## Importing Existing Files

Years of PDFs and Word docs gathering dust? Feed them in:

```bash
python3 scripts/process_docs_to_obsidian.py ~/your-files ~/exo-brain/inbox
```

Gemini 3 Flash reads each file, strips the noise (boilerplate, headers, filler), and outputs a compressed markdown note (300-600 words). Then tell Claude: *"Sort everything in inbox/ into the right folders."* It reads your CLAUDE.md and routes each note where it belongs.

**Formats:** `.pdf` `.docx` `.pptx` `.txt` `.md`

> **Spreadsheets and code too?** Use the broader script:
> ```bash
> python3 scripts/process_files_with_gemini.py ~/your-files
> ```
> Handles `.xlsx` `.csv` `.json` `.xml` `.py` `.js` `.html` and more. Outputs per-file summaries plus a `MASTER_SUMMARY.md`.

---

## Vault Structure

```
~/exo-brain/
├── CLAUDE.md        ← The system prompt for your life. Read every session.
├── memory.md        ← Running log. Claude updates this after each conversation.
├── inbox/           ← Drop zone. Everything lands here first.
├── daily/           ← Daily notes (YYYY-MM-DD.md).
├── projects/        ← Active work. Claude loads the relevant one before helping.
├── research/        ← Synthesized knowledge, sources, ideas.
└── archive/         ← Done work. Never delete — just move it here.
```

**How it compounds:**
- **Session 1:** Claude knows your folder layout
- **Session 5:** Claude knows your projects, your preferences, your voice
- **Session 20:** Claude has better recall of your work than you do

---

## Requirements

| Tool | Platform | Get it |
|------|----------|--------|
| Obsidian | macOS / Windows / Linux | `brew install --cask obsidian` or `winget install Obsidian.Obsidian` |
| Claude Code | macOS / Linux | `curl -fsSL https://claude.ai/install.sh \| sh` |
| Claude Code | Windows | `winget install Anthropic.ClaudeCode` |
| Python 3.8+ | All | [python.org](https://python.org) |
| Google API key | All | [aistudio.google.com/apikey](https://aistudio.google.com/apikey) — free tier works |
| Claude account | All | [claude.ai](https://claude.ai) — Pro recommended for daily use |

---

## Repo Structure

```
exo-brain/
├── setup.sh                              macOS/Linux setup
├── setup.ps1                             Windows setup
├── CLAUDE.md                             Vault system file
├── memory.md                             Session memory
├── requirements.txt                      Python deps
├── .env.example                          API key template
├── .gitignore
├── scripts/
│   ├── process_docs_to_obsidian.py      File → Obsidian note converter
│   └── process_files_with_gemini.py     Batch file analyzer
├── skills/
│   ├── vault-setup/SKILL.md             Vault configurator
│   ├── daily/SKILL.md                   Daily standup
│   ├── tldr/SKILL.md                    Session summary
│   └── file-intel/SKILL.md             Folder processor
└── vault-template/
    ├── inbox/   daily/   projects/
    └── research/   archive/
```

---

## Manual Setup

<details>
<summary>Want to install each piece yourself? Expand for step-by-step on both platforms.</summary>

---

### macOS

**1. Homebrew** (skip if installed)
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**2. Obsidian**
```bash
brew install --cask obsidian
```

**3. Claude Code**
```bash
curl -fsSL https://claude.ai/install.sh | sh
```

**4. Python deps**
```bash
python3 -m venv ~/.exo-brain-venv
~/.exo-brain-venv/bin/pip install -r exo-brain/requirements.txt
```

**5. Vault setup**
```bash
git clone https://github.com/bsy/exo-brain.git
mkdir -p ~/exo-brain/{inbox,daily,projects,research,archive,.claude/skills/vault-setup,.claude/skills/daily,.claude/skills/tldr,.claude/skills/file-intel,scripts}
cp exo-brain/CLAUDE.md exo-brain/memory.md ~/exo-brain/
cp exo-brain/skills/vault-setup/SKILL.md ~/exo-brain/.claude/skills/vault-setup/
cp exo-brain/skills/daily/SKILL.md ~/exo-brain/.claude/skills/daily/
cp exo-brain/skills/tldr/SKILL.md ~/exo-brain/.claude/skills/tldr/
cp exo-brain/skills/file-intel/SKILL.md ~/exo-brain/.claude/skills/file-intel/
cp exo-brain/scripts/* ~/exo-brain/scripts/
cp exo-brain/.env.example ~/exo-brain/.env
# Global skills (work from any folder):
mkdir -p ~/.claude/skills/{vault-setup,daily,tldr,file-intel}
cp exo-brain/skills/vault-setup/SKILL.md ~/.claude/skills/vault-setup/
cp exo-brain/skills/daily/SKILL.md ~/.claude/skills/daily/
cp exo-brain/skills/tldr/SKILL.md ~/.claude/skills/tldr/
cp exo-brain/skills/file-intel/SKILL.md ~/.claude/skills/file-intel/
```

**6. API key** — Edit `~/exo-brain/.env`, paste your key from [aistudio.google.com/apikey](https://aistudio.google.com/apikey).

**7. Kepano's Obsidian Skills** *(optional)*
```bash
git clone --depth=1 https://github.com/kepano/obsidian-skills.git /tmp/obs-skills
for d in /tmp/obs-skills/skills/*/; do
  name=$(basename "$d")
  mkdir -p ~/exo-brain/.claude/skills/$name
  cp "$d/SKILL.md" ~/exo-brain/.claude/skills/$name/
done
rm -rf /tmp/obs-skills
```

**8. Go**
```bash
cd ~/exo-brain && claude
```

---

### Windows

Open **PowerShell** for everything below.

**1. Obsidian**
```powershell
winget install Obsidian.Obsidian
```

**2. Claude Code**
```powershell
winget install Anthropic.ClaudeCode
```
Close and reopen PowerShell.

**3. Python** — Download from [python.org/downloads](https://python.org/downloads). Tick **"Add Python to PATH"**.

**4. Vault setup**
```powershell
git clone https://github.com/bsy/exo-brain.git
$vault = "$env:USERPROFILE\exo-brain"
New-Item -ItemType Directory -Force -Path "$vault\inbox","$vault\daily","$vault\projects","$vault\research","$vault\archive","$vault\scripts","$vault\.claude\skills\vault-setup","$vault\.claude\skills\daily","$vault\.claude\skills\tldr","$vault\.claude\skills\file-intel" | Out-Null
Copy-Item "exo-brain\CLAUDE.md","exo-brain\memory.md" $vault
Copy-Item "exo-brain\skills\vault-setup\SKILL.md" "$vault\.claude\skills\vault-setup\"
Copy-Item "exo-brain\skills\daily\SKILL.md" "$vault\.claude\skills\daily\"
Copy-Item "exo-brain\skills\tldr\SKILL.md" "$vault\.claude\skills\tldr\"
Copy-Item "exo-brain\skills\file-intel\SKILL.md" "$vault\.claude\skills\file-intel\"
Copy-Item "exo-brain\scripts\*" "$vault\scripts\"
Copy-Item "exo-brain\.env.example" "$vault\.env"
# Global skills:
$global = "$env:USERPROFILE\.claude\skills"
New-Item -ItemType Directory -Force -Path "$global\vault-setup","$global\daily","$global\tldr","$global\file-intel" | Out-Null
Copy-Item "exo-brain\skills\vault-setup\SKILL.md" "$global\vault-setup\"
Copy-Item "exo-brain\skills\daily\SKILL.md" "$global\daily\"
Copy-Item "exo-brain\skills\tldr\SKILL.md" "$global\tldr\"
Copy-Item "exo-brain\skills\file-intel\SKILL.md" "$global\file-intel\"
```

**5. Python deps**
```powershell
pip install -r exo-brain\requirements.txt
```

**6. API key** — Edit `%USERPROFILE%\exo-brain\.env`, paste your key from [aistudio.google.com/apikey](https://aistudio.google.com/apikey).

**7. Kepano's Obsidian Skills** *(optional)*
```powershell
$tmp = "$env:TEMP\obs-skills"
git clone --depth=1 https://github.com/kepano/obsidian-skills.git $tmp
Get-ChildItem "$tmp\skills" -Directory | ForEach-Object {
    $dest = "$env:USERPROFILE\exo-brain\.claude\skills\$($_.Name)"
    New-Item -ItemType Directory -Force -Path $dest | Out-Null
    Copy-Item "$($_.FullName)\SKILL.md" "$dest\" -Force
}
Remove-Item $tmp -Recurse -Force
```

**8. Go**
```powershell
cd "$env:USERPROFILE\exo-brain"
claude
```

</details>

---

## Important: Cloud Sync Users

If you use **Obsidian Sync**, **iCloud**, **OneDrive**, or **Dropbox**, exclude these from sync:

| Exclude | Reason |
|---------|--------|
| `.claude/` | Claude's internal state. Syncing it creates a recursive loop — Claude reads its own logs as vault content, file count explodes, context gets corrupted. |
| `scripts/` | Python scripts. No reason to sync. |
| `.env` | Your API key. Never sync credentials. |

```
Obsidian → Settings → Sync → Excluded folders → Add: .claude, scripts
```

> **This is not hypothetical.** Syncing `.claude/` has bricked vaults for months. Keep your Obsidian vault and Claude config folders completely separate.

### Vault vs Global Config

| Path | What | Obsidian sees it? |
|------|------|-------------------|
| `~/exo-brain/` | Your vault | Yes |
| `~/.claude/` | Claude Code's global config | **No** — never point Obsidian or sync here |

---

## Windows Troubleshooting

<details>
<summary><strong>Parsing errors ("Unexpected token '}'")</strong></summary>

Old issue with PowerShell 7+ syntax on Windows' default PowerShell 5.1. Fixed in the current version. Re-download and re-run — it's safe, skips completed steps.

```powershell
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/bsy/exo-brain/main/setup.ps1" -OutFile setup.ps1
powershell -ExecutionPolicy Bypass -File setup.ps1
```

</details>

<details>
<summary><strong>Python not found / pip not found</strong></summary>

Windows sometimes reports Python as "installed" when only the launcher (`py.exe`) exists.

1. Download from [python.org/downloads](https://python.org/downloads)
2. **Tick "Add Python to PATH"** on the first installer screen
3. Close and reopen PowerShell
4. Re-run the setup script

> WSL Python doesn't count. You need native Windows Python.

</details>

<details>
<summary><strong>'claude' not recognized</strong></summary>

Close PowerShell, open a new window. PATH updates only apply to new sessions.

</details>

<details>
<summary><strong>Script in wrong folder</strong></summary>

The one-liner downloads to wherever PowerShell is sitting. If files are missing:

```powershell
git clone https://github.com/bsy/exo-brain.git
cd exo-brain
powershell -ExecutionPolicy Bypass -File setup.ps1
```

</details>

---

## FAQ

**Is my data private?**
Yes. Everything is local markdown files. Claude Code reads them in your folder. The only network call is optional Gemini file processing, and you can skip that entirely.

**Free or paid Claude?**
Free works for light use. Claude Pro ($20/mo) is worth it if you're using this daily.

**Works with an existing vault?**
Yes. See [above](#already-have-an-obsidian-vault). Detects existing content, backs up your CLAUDE.md, only adds what's missing.

**Do I need the Gemini file processing?**
No. The core system — Obsidian + Claude Code + CLAUDE.md + slash commands — works without any API key.

**Cloud sync safe?**
Yes, if you exclude `.claude/`, `scripts/`, and `.env`. See [Important: Cloud Sync Users](#important-cloud-sync-users).

**WSL compatible?**
Yes. Set up the vault on Windows, access it from WSL at `/mnt/c/Users/YOU/exo-brain`. Obsidian and Claude Code share the same files.

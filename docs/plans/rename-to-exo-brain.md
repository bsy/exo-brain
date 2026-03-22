# Plan: Rename Second Brain to Exo Brain

**Complexity**: Shallow
**Risk**: Low — text replacements in a small repo, no runtime dependencies to break

## Context

Clone https://github.com/earlyaidopters/second-brain into `/Users/ben/code/second-brain`, initialize as a fresh git repo (not a fork), and rename all references from "second brain" to "exo brain" across all variants.

## Replacement Map

| Original | Replacement |
|----------|-------------|
| `second-brain` | `exo-brain` |
| `Second Brain` | `Exo Brain` |
| `second brain` | `exo brain` |
| `SECOND BRAIN` | `EXO BRAIN` |
| `SECOND_BRAIN` | `EXO_BRAIN` |
| `SecondBrain` | `ExoBrain` |
| `.second-brain-venv` | `.exo-brain-venv` |

## Steps

### 1. Clone and initialize
- Copy all files from the cloned repo (`/tmp/second-brain-source`) into `/Users/ben/code/second-brain/`
- Initialize a fresh git repo
- Remove `.git` from clone (we don't want upstream history)

### 2. Rename file contents (all files)
Apply the replacement map to every file. Order: longest match first to avoid partial replacements.

Files with known occurrences:
- `setup.sh` (~25+ occurrences)
- `setup.ps1` (~25+ occurrences)
- `README.md` (~15+ occurrences)
- `CLAUDE.md` (1 occurrence)
- `banner.svg` (2 occurrences)
- `skills/vault-setup/SKILL.md` (1 occurrence)
- `scripts/process_docs_to_obsidian.py` (1 occurrence)
- `.env.example` (check)

### 3. Update banner.svg branding
Replace "SECOND BRAIN" text with "EXO BRAIN" in the SVG.

### 4. Remove upstream attribution references
- Remove earlyaidopters GitHub URLs
- Remove Mark Kashef / Prompt Advisers attribution (make it Ben's own)

### 5. Initialize git repo and make initial commit

## Verification
- `grep -ri "second.brain"` across all files should return 0 results
- All scripts should have consistent `exo-brain` naming

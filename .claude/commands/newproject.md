# New Project Setup

Creates a standard project folder structure for UIB research projects.

## Usage

```
/newproject <project-name>
```

## What It Does

1. Creates the folder structure below inside the current directory
2. Copies `CLAUDE.md` from `C:\Users\UIB\uib-research-tools-amo\templates\CLAUDE.md`
3. Generates a `README.md` with the project name, date, and blank sections
4. Creates a first progress log entry in `progress_logs/`

## Folder Structure Created

```
<project-name>/
├── CLAUDE.md
├── README.md
├── code/
│   ├── stata/
│   └── python/
├── data/
│   ├── raw/
│   └── clean/
├── output/
│   ├── tables/
│   ├── figures/
│   └── logs/
├── documents/
├── decks/
├── notes/
└── progress_logs/
```

## Instructions for Claude

When the user runs `/newproject <name>`:

1. Create all folders listed above under `<name>/`
2. Copy the contents of `C:\Users\UIB\uib-research-tools-amo\templates\CLAUDE.md` into `<name>/CLAUDE.md`
3. Create `<name>/README.md` with this template:

```markdown
# <name>

**Started:** <YYYY-MM-DD>
**Director:** Alfredo Martínez — Cátedra de Empresa Familiar, UIB

## Research Question


## Status


## Key Files


## Data Sources


## Notes

```

4. Create `<name>/progress_logs/<YYYY-MM-DD>_project-start.md` with:

```markdown
# Session Log — <YYYY-MM-DD>

## Project started: <name>

### Setup
- Folder structure created via /newproject
- CLAUDE.md copied from uib-research-tools-amo template

### Research question
[To be defined]

### Next steps
- [ ] Define research question
- [ ] Identify data sources
- [ ] Draft estimation strategy

```

5. Confirm to the user what was created and remind them to fill in the README research question.

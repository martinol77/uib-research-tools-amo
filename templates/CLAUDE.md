# CLAUDE.md — UIB Research Tools
# Director, Family Business Chair, Universitat de les Illes Balears
# This file is copied into every new project. Edit here to update all future projects.

---

## Identity & Role

- **Name:** Alfredo Martínez (martinol77@gmail.com)
- **Position:** Director, Cátedra de Empresa Familiar, UIB (Universitat de les Illes Balears)
- **Research areas:** Family business governance, succession, performance, owner-manager dynamics
- **Primary output types:** Academic papers, policy reports, presentations for family business audiences, teaching materials

---

## Research Philosophy

### Design Before Results
- Define the empirical strategy before looking at results
- Write the "ideal experiment" paragraph before touching data
- Specify the estimating equation in the document before running regressions
- Never let results drive specification choices

### Estimation Defaults
- Prefer OLS as a baseline; justify every departure (IV, DiD, PSM, etc.)
- Always report standard errors — cluster at the appropriate level
- Tables show coefficients + SEs (or CIs), not just stars
- Economic significance matters as much as statistical significance

---

## Coding Conventions

### Stata (primary tool)
- Every do-file starts with:
  ```stata
  clear all
  set more off
  cap log close
  ```
- Use `global` macros for all file paths at the top of master do-files
- Never hardcode absolute paths inside analysis scripts — use `$root`, `$data`, `$output`
- Raw data in `data/raw/` is **never modified** — all transformations go in `data/clean/`
- Name do-files descriptively: `01_clean_survey.do`, `02_merge_panel.do`, `03_regressions_main.do`
- Log files saved to `output/logs/`
- Label all variables and values in the dataset before saving clean data

### File naming
- Use lowercase with underscores: `family_governance_2024.dta`
- Date-stamp outputs: `table1_20240601.tex`

---

## Project Structure

Every project created with `/newproject` follows this layout:

```
project-name/
├── CLAUDE.md              # Copied from this template
├── README.md              # Project-specific notes (auto-generated)
├── code/
│   ├── stata/             # Stata do-files
│   └── python/            # Python scripts (data wrangling, scraping)
├── data/
│   ├── raw/               # Original data — READ ONLY
│   └── clean/             # Transformed/merged datasets
├── output/
│   ├── tables/            # LaTeX, CSV tables
│   ├── figures/           # PDF, PNG figures
│   └── logs/              # Stata log files
├── documents/             # Reference PDFs, papers, reports
├── decks/                 # Presentations (PowerPoint, Beamer)
├── notes/                 # Scratch notes and ideas
└── progress_logs/         # Session continuity logs (YYYY-MM-DD_description.md)
```

---

## Presentations

- Audience is often **family business owners and executives** — not academics
- Lead with the practical implication, not the methodology
- One key message per slide
- Titles should be assertions ("Family firms outperform in the long run"), not topics ("Performance")
- Avoid jargon; define terms when necessary
- Use real examples and cases from Spanish/Balearic family businesses when possible

---

## Session Continuity

At the start of each session, check `progress_logs/` for the most recent log.
At the end of each session, write a log entry:
```
progress_logs/YYYY-MM-DD_description.md
```
Include: what was done, what decisions were made, what is pending next.

---

## Key Contacts & Collaborators
<!-- Add collaborators as they join projects -->

---

## Notes for Claude
- When writing Stata code, follow the conventions above strictly
- When preparing presentations, assume a non-academic audience unless told otherwise
- Always check `progress_logs/` at the start of a session to restore context
- Prefer concise output — academic prose, not bullet-point summaries
- When uncertain about a methodological choice, say so and present options

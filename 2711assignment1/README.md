# Assignment 1 — Configure a Multi-Level Claude Code Setup

**Track:** Claude Code · Folder Structure  **Level:** Intermediate

## Goal

Create four `CLAUDE.md` files — personal, team-wide, API-specific and frontend-specific — each containing only the rules that belong at its scope, with no rule duplicated across files.

## Scenario

A Node.js monorepo with two services, `api/` and `frontend/`. The project's working rules are encoded at the correct level so every developer, and every future Claude Code session, gets consistent behaviour automatically.

## Submission Structure

```
2711assignment1/
├── README.md
├── CLAUDE.md                 # Team-wide        → ./CLAUDE.md
├── api/
│   └── CLAUDE.md             # API service      → api/CLAUDE.md
├── frontend/
│   └── CLAUDE.md             # Frontend service → frontend/CLAUDE.md
└── personal/
    └── .claude/
        └── CLAUDE.md         # Personal         → ~/.claude/CLAUDE.md
```

> **Note on `personal/`:** In a real project the personal file lives in the developer's home directory (`~/.claude/CLAUDE.md`, or `%USERPROFILE%\.claude\CLAUDE.md` on Windows) and is never committed. It is included here only so the full submission can be reviewed in one place.

## Scope Map

| File | Scope | Loaded when | Version control | Covers |
|------|-------|-------------|-----------------|--------|
| `~/.claude/CLAUDE.md` | Personal | Every session, this developer only | Never committed | Response style |
| `./CLAUDE.md` | Team-wide | Every session in the repo | Committed | Pre-commit testing, protected build output |
| `api/CLAUDE.md` | API service | Working inside `api/` | Committed with code | Endpoint design and versioning |
| `frontend/CLAUDE.md` | Frontend service | Working inside `frontend/` | Committed with code | React component style |

## Design Decisions

- **Each rule lives in exactly one file.** Subdirectory files are layered on top of the root file, so repeating a rule would only add ambiguity and waste context.
- **Service rules stay out of the root.** `api/CLAUDE.md` and `frontend/CLAUDE.md` only activate inside their own subtree, so API conventions never load during frontend work, and vice versa.
- **Personal preferences stay out of the repo.** Response style is an individual choice, so it belongs in the user-level file rather than being imposed on the team.
- **Directive language throughout.** Every rule starts with *Always*, *Never* or *Use*, so it reads as an unambiguous instruction.

## Requirements Checklist

- [x] `~/.claude/CLAUDE.md` contains only the personal preference
- [x] `./CLAUDE.md` contains only the team-wide rules
- [x] `api/CLAUDE.md` contains only the API-specific conventions
- [x] `frontend/CLAUDE.md` contains only the frontend-specific conventions
- [x] No rule appears in more than one file
- [x] All rules use directive language ("Always…", "Never…", "Use…")

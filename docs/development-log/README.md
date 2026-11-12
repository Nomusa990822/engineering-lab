# Development Log

This directory records meaningful engineering work across the ENGINEERING LAB portfolio.

## Purpose

The log provides a chronological record of implementation, investigation, verification, technical learning and decisions. It complements—not replaces—Git history, issues, pull requests, ADRs and project-specific documentation.

## File naming

Use one file per meaningful work session or closely related set of sessions:

`YYYY-MM-DD.md`

If multiple distinct projects need separate entries on the same date, use:

- `YYYY-MM-DD-project-name.md`

Use lowercase kebab-case for the project name.

## What to record

- The objective and scope of the work.
- Relevant project, branch and commit identifiers.
- Files or components changed.
- Commands and tests actually run, with results.
- Decisions and links to ADRs.
- Problems, blockers and unresolved questions.
- New technical understanding.
- The next concrete action.

## Evidence and accuracy

- Link commits, pull requests, CI runs, releases and demonstrations.
- Record failed tests as well as successful ones when they affect the next action.
- Distinguish implemented, tested, reviewed and released states.
- Do not copy secrets, access tokens, personal data or sensitive production information into logs.
- Do not record unsupported performance, coverage or security claims.
- Correct an inaccurate entry with a dated clarification rather than silently rewriting history.

## Relationship to product repositories

The portfolio log records cross-project work and major portfolio-level sessions. Product-specific implementation logs should normally live in their respective repositories. Link to them when useful; avoid duplicating every commit or daily task.

## Template

Start from [the development log template](../templates/DEVELOPMENT-LOG-TEMPLATE.md).

## Entries

- [2026-11-10.md](2026-11-10.md) — portfolio documentation and governance foundation.
- [2026-11-11-aegis.md](2026-11-11-aegis.md) — AEGIS detection verification, UTC timestamp correction, container hardening, verified permissions, session stopping point and next verification plan.

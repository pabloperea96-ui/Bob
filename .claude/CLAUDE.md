# CLAUDE.md — Bob

## Project Type
static

## Single File
bob.html — the entire application lives here. Never split it.

## What Bob Is
A personal Project Workflow Guide for solo founders. Bob tracks up to 5 projects
through a phase-based workflow. State persists in localStorage between sessions.

## Read Before Every Session
docs/CONTEXT.md — full project brief, phase structure, data model, and visual language.

## localStorage Schema
All keys must be prefixed bob_*
- bob_projects — array of project summaries (max 5)
- bob_project_{id} — full state for each project
See docs/CONTEXT.md §7 for the exact data model. Follow it exactly.

## Non-Negotiables
- Single HTML file — never split into multiple files
- No external network requests of any kind
- No data leaves the browser
- Max 5 projects enforced in code, not just UI
- Soft-warn phase gates only — never hard-lock a phase
- All localStorage keys prefixed bob_*
- Two Google Fonts max, loaded via <link>
- One accent color only

## Agents
- Start every structural session with: planner
- All code writing: builder
- After every implementation: reviewer

## Open Decisions to Resolve in First Session
See docs/CONTEXT.md §8 — four UI decisions need to be made before building starts.

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

## Visual Implementation Guidance

### Aesthetic Direction
Commit fully to: editorial / luxury-refined / field guide.
Not minimal for minimalism's sake — considered and intentional.
The one thing someone should remember: it feels like a tool made by a designer who cares.

### Typography
- Heading font: distinctive, characterful — something with personality (ex: Fraunces, Playfair Display, Cormorant, DM Serif Display)
- Body font: readable, neutral but not generic (ex: Lora, Source Serif, Instrument Serif)
- Weight and size carry hierarchy — not color, not badges
- Never: Inter, Roboto, Arial, Space Grotesk, system fonts

### Color
- Monochrome base (near-black / near-white)
- One accent color — warm or cool, used sparingly
- CSS variables for every color value — no hardcoded hex in components
- Dark mode via prefers-color-scheme — equally intentional, not just inverted

### Motion
- Phase transitions: subtle, like turning a page — not a button click
- One well-orchestrated load sequence with staggered reveals
- Hover states that feel considered, not default
- CSS-only animations — no JS animation libraries

### Spatial Composition
- Generous whitespace — let content breathe
- Strong vertical rhythm
- Avoid symmetrical card grids — this is not a dashboard
- Phase status through typography and subtle indicators, never colored badges

### What Bob Must Never Look Like
- A Jira clone
- A generic to-do app
- A startup dashboard with purple gradients
- Anything that looks like it came from a UI kit

# Bob — Project Context & Design Brief

**Version**: 1.0
**Author**: Pablo Perea
**Status**: Pre-build
**Last updated**: March 2026

---

## 1. What Bob Is

Bob (named after Bob the Builder) is a personal Project Workflow Guide for solo founders.

It is a single HTML file that lives locally or in a project repo. It helps the person building a project move through a structured, phase-based workflow — from initial discovery through to deployment — without skipping steps, losing context between sessions, or defaulting to ad-hoc process.

**Bob is not:**
- A task manager or to-do app
- A kanban board
- A project management platform
- A dashboard you monitor passively

**Bob is:**
- A guide you work through actively
- An opinionated process encoded in a tool
- A personal accountability system for solo founders
- A lightweight artifact that travels with any project

---

## 2. The Problem Bob Solves

Solo founders building digital products frequently:
- Start coding before the problem is clearly defined
- Skip the PRD because it "takes too long"
- Make stack decisions before understanding scope
- Lose track of what phase they're in after time away from a project
- Have no structured place to capture mindfulness notes or decisions made

Bob encodes a proven workflow so the founder doesn't have to hold it in their head.

---

## 3. Core Design Decisions (Final — Do Not Revisit Without Explicit Instruction)

| Decision | Choice | Reason |
|----------|--------|--------|
| Format | Single HTML file | Zero infra, portable, no deployment |
| Persistence | localStorage | No backend needed, personal tool |
| Phase gates | Soft-warn (not hard-lock) | Discovery is non-linear in practice |
| Project types | 5 fixed types | Covers Pablo's realistic project range |
| Max projects | 5 | Keeps tool focused, manageable in localStorage |
| Tasks | Pre-filled + editable | Opinionated defaults + flexibility |
| Geographic context | None | Tool must work for any project type anywhere |
| PRD phase | Checklist + external link | PRD is written in Claude.ai, not inside Bob |
| Visual language | Design-sensible, editorial | Tool should feel good to open |

---

## 4. Project Types

### 4.1 Website
A multi-page informational or portfolio site. Typically public-facing, SEO-relevant, content-driven.

### 4.2 Landing Page
A single-page conversion-focused page. Product launch, campaign, waitlist, or announcement.

### 4.3 B2C / B2B App
A full-stack application with user accounts, database, and product logic. The most complex type.

### 4.4 Internal Tool
A utility built for internal use — no public users, no SEO, typically simpler auth requirements.

### 4.5 Marketing Project
A campaign, content system, or creative project. May include social assets, email sequences, or content calendars. Lighter on engineering, heavier on strategy and content.

---

## 5. Phase Structure

### Phase 0 — Discovery

**Objective**: Validate that a real problem exists worth solving before committing to build anything.

**Universal tasks** (apply to all project types):
- Define the problem in one sentence without mentioning a solution
- Identify who specifically experiences this problem
- Document what they currently do instead (the workaround)
- List the top 3 assumptions you're making that could kill this project
- Identify the closest existing alternatives

**Type-specific tasks**:
- *App*: Conduct at least 3 problem interviews with real potential users
- *Website / Landing*: Define the primary audience and the one action you want them to take
- *Internal Tool*: Map the current manual process this tool replaces
- *Marketing*: Define the campaign goal and the single metric that will define success

**What to be mindful of**:
- A solution is not a problem statement. "I want to build an app that does X" is not a problem.
- Talking to friends who agree with you is not validation.
- If you can't articulate what people do today without your solution, you don't understand the problem yet.
- Enthusiasm is not evidence.

**Checklist**:
- [ ] Problem statement written without mentioning a solution
- [ ] Target user defined with at least 3 specific characteristics
- [ ] Current workaround documented
- [ ] Top assumptions listed
- [ ] At least one existing alternative identified and analyzed

---

### Phase 0b — MVP Scope

**Objective**: Define the smallest possible version that delivers the core value — and nothing else.

**Universal tasks**:
- List every feature you're tempted to build
- For each feature, write the job it enables (what does the user achieve?)
- Cut everything that doesn't enable the core job
- Define P0 (launch blockers), P1 (v1 but not blockers), P2 (v2 and beyond)
- Write the kill criteria: what result at day 60 would make you stop?

**Type-specific tasks**:
- *App*: Define the single core flow a user must complete to get value — max 5 steps
- *Website*: Define the 3 pages minimum to launch (usually: home, about, contact or equivalent)
- *Landing*: Define the single conversion action and the 3 sections that lead to it
- *Internal Tool*: Define the one workflow this tool must replace to justify building it
- *Marketing*: Define the deliverables for phase 1 only — not the full campaign

**What to be mindful of**:
- "Minimum" means minimum. If you're not uncomfortable cutting, you haven't cut enough.
- Every feature added to v1 multiplies your build time non-linearly.
- P2 is not a promise. It's a parking lot.
- Kill criteria defined now are worth 10x kill criteria defined later.

**Checklist**:
- [ ] Full feature list written (including everything you want eventually)
- [ ] Each feature mapped to a specific user job
- [ ] P0 / P1 / P2 priorities assigned
- [ ] Features without a clear job have been cut or deferred
- [ ] Kill criteria written with specific metrics and thresholds

---

### PRD — Product Requirements Document

**Objective**: Produce a single written document that captures everything needed to build v1 — so Claude Code and any future collaborator can work from it without asking you to re-explain the product.

**Note**: The PRD is written in conversation with your product consultant (Claude.ai), not inside Bob. Bob tracks whether it exists and is complete.

**Universal tasks**:
- Complete the PRD using your standard template
- Export it as `docs/PRD.md` in the project repo
- Add the Figma file link to the PRD
- Reference the PRD in your project's `CLAUDE.md`

**What to be mindful of**:
- A PRD written before Phase 0 and 0b are complete is expensive fiction.
- The PRD is a living document — update it when decisions change, don't let it go stale.
- The technical requirements section of the PRD is what drives Phase 1 (stack decision).
- If you can't fill in the success metrics section, your scope is still unclear.

**Checklist**:
- [ ] Problem definition section complete
- [ ] Target user defined with persona
- [ ] MVP features listed with acceptance criteria
- [ ] Technical stack section filled
- [ ] North Star metric defined
- [ ] Kill criteria documented
- [ ] PRD exported to `docs/PRD.md` in repo
- [ ] Figma file link added (paste URL below)

**Figma / Notion link**: *(paste here)*

---

### Phase 1 — Stack Decision

**Objective**: Choose the technical stack for this project based on its actual requirements — not habits or defaults.

**Universal tasks**:
- Read the PRD technical requirements section before making any decision
- Decide: does this project need SEO? (determines frontend framework)
- Decide: does this project need a backend? (determines if Supabase or simpler)
- Decide: does this project need auth? (determines complexity)
- Document the stack decision with a one-line reason for each choice

**Type-specific tasks**:
- *App*: Define the database schema at a high level before writing code
- *Website*: Decide between Next.js (SEO-critical) and Astro (content-heavy, static)
- *Landing*: Consider whether a no-code tool (Framer, Webflow) is faster than code
- *Internal Tool*: Define who has access and how — even if auth is simple
- *Marketing*: Decide which deliverables need code and which don't

**What to be mindful of**:
- The best stack is the one that ships. Not the most impressive one.
- Next.js has real complexity cost for non-developers. Only use it when SEO is genuinely required.
- Supabase is the right default for apps, but overkill for a landing page.
- Deciding the stack before reading the PRD is how you end up rebuilding.

**Checklist**:
- [ ] Frontend framework chosen with reason documented
- [ ] Backend/database decision made (or explicitly decided not needed)
- [ ] Auth approach decided
- [ ] Hosting/deployment target confirmed
- [ ] Stack written into project CLAUDE.md

---

### Phase 2 — Scaffold

**Objective**: Set up the project repository with the correct structure, configuration, and security baseline before writing a single line of product code.

**Universal tasks**:
- Create the GitHub repository
- Set up the folder structure per global CLAUDE.md conventions
- Create `.gitignore` — include `.env*` before the first commit
- Create `docs/` folder with `CONTEXT.md` and `PRD.md`
- Create `.claude/` folder with `CLAUDE.md`, `settings.json`, and `agents/`
- Configure localStorage security or secrets management per stack
- Make the first commit with scaffolding only — no product code yet

**Type-specific tasks**:
- *App / Website*: Initialize the framework (Vite, Next.js, Astro)
- *Landing*: Decide if this is a single HTML file or a framework — scaffold accordingly
- *Internal Tool*: Set up access control before any UI work
- *Marketing*: Create the file/folder structure for deliverables and assets

**What to be mindful of**:
- `.env*` must be in `.gitignore` before the first commit. Not after.
- The scaffold commit is not the place to start building features.
- A `CLAUDE.md` with no stack info is worse than no `CLAUDE.md` — Claude Code will make wrong assumptions.
- The reviewer subagent should check the scaffold before Phase 3 begins.

**Checklist**:
- [ ] GitHub repo created
- [ ] `.gitignore` includes `.env*`
- [ ] Folder structure matches global convention
- [ ] `docs/CONTEXT.md` committed
- [ ] `docs/PRD.md` committed
- [ ] `.claude/CLAUDE.md` committed
- [ ] `.claude/settings.json` with deny rules committed
- [ ] Three subagent files committed
- [ ] First scaffold commit pushed

---

### Phase 3 — Design to Code

**Objective**: Translate Figma designs into working frontend components, systematically and without skipping the design system foundations.

**Universal tasks**:
- Connect Figma MCP to Claude Code for the project file
- Build design tokens and CSS custom properties first (colors, typography, spacing)
- Build layout and navigation before content components
- Build reusable components before page-level compositions
- Reference Figma frames explicitly in builder subagent prompts

**Type-specific tasks**:
- *App*: Build the core flow screens first (the flow defined in the PRD)
- *Website*: Build the component library before assembling pages
- *Landing*: Build above-the-fold first, then scroll sections, then footer
- *Internal Tool*: Prioritize function over form — tables, forms, and navigation before polish
- *Marketing*: Define asset formats and sizes before designing in Figma

**What to be mindful of**:
- Start with tokens, not components. A component built without the design system will need rebuilding.
- Figma MCP gives Claude Code direct access to your file — use frame names as references.
- Every component should be tested in isolation before being composed into a page.
- Don't polish until the structure is right.

**Checklist**:
- [ ] Figma MCP connected and project file accessible
- [ ] Design tokens/CSS variables defined and committed
- [ ] Navigation and layout structure built
- [ ] Core components built (list them in notes)
- [ ] Core user flow navigable in browser
- [ ] Reviewer subagent run on component code

---

### Phase 4 — Backend Wiring

**Objective**: Connect the frontend to data persistence, authentication, and any external services — in that order.

**Universal tasks** (skip if project type has no backend):
- Define and create the database schema
- Set up authentication (if required)
- Implement Row Level Security (RLS) policies before writing any data queries
- Connect frontend components to real data (replace all mock data)
- Test every data operation: create, read, update, delete

**Type-specific tasks**:
- *App*: Auth before data. RLS before queries. Never the other way around.
- *Website*: If CMS-backed, connect the content source and test with real content
- *Landing*: Connect the conversion action (form submission, waitlist signup)
- *Internal Tool*: Verify access control is working before connecting any real data
- *Marketing*: Connect any tracking, analytics, or automation workflows (n8n)

**What to be mindful of**:
- RLS policies in Supabase are not optional. Without them, all authenticated users can read all data.
- Never test auth flows with production credentials.
- Every external API integration needs error handling — what happens when it's down?
- The Supabase MCP lets Claude Code interact with your database directly — use it carefully.

**Checklist**:
- [ ] Database schema created and documented
- [ ] Authentication working (if applicable)
- [ ] RLS policies implemented and tested (if applicable)
- [ ] All mock data replaced with real data fetching
- [ ] Error states handled (empty state, loading state, error state)
- [ ] Reviewer subagent run on all data-touching code

---

### Phase 5 — Review and Deploy

**Objective**: Ship a version that works, is secure, and can be maintained — then stop adding features.

**Universal tasks**:
- Run the reviewer subagent on the full codebase
- Fix all critical and warning findings before deploying
- Test the complete user flow end-to-end
- Set up deployment pipeline (Vercel or equivalent)
- Configure environment variables in the deployment platform (never in code)
- Deploy to staging first, verify, then deploy to production
- Document the deployment setup in `docs/CONTEXT.md`

**Type-specific tasks**:
- *App*: Test auth flow, data persistence, and core job completion end-to-end
- *Website*: Test all pages, all links, and performance (target: <2s load on 4G)
- *Landing*: Test the conversion action and verify it reaches the right destination
- *Internal Tool*: Test with a real use case, not synthetic test data
- *Marketing*: QA all deliverables against the brief before handoff or publish

**What to be mindful of**:
- "Done" means the core job works reliably — not that every edge case is handled.
- Deploy to staging before production, even if staging is just a preview URL.
- Environment variables set in the deployment platform, never committed to the repo.
- The first deployment is not the last — define what v1.1 means before closing this phase.

**Checklist**:
- [ ] Reviewer subagent run on full codebase
- [ ] Critical findings resolved
- [ ] Full user flow tested end-to-end
- [ ] Deployment pipeline configured
- [ ] Environment variables set in deployment platform (not in code)
- [ ] Deployed to staging and verified
- [ ] Deployed to production
- [ ] Deployment documented in `docs/CONTEXT.md`
- [ ] v1.1 scope defined (or explicitly decided not to continue)

---

## 6. Visual Language

Bob should feel like a tool made by a designer, not a developer.

**Aesthetic direction**: Editorial, refined, considered. Think a well-typeset field guide or a design studio's internal system. Not corporate, not generic SaaS.

**Principles**:
- Generous whitespace
- Strong typographic hierarchy — weight and size do the work, not color
- One accent color, used sparingly and intentionally
- Monochrome base palette with a single warm or cool accent
- Subtle transitions — phase changes should feel like turning a page, not clicking a button
- Phase status communicated through typography and subtle indicators, not colored badges

**Dark mode**: Supported via `prefers-color-scheme`. Should feel equally intentional in both modes.

**Accent color**: `#F0C70E` (bright yellow). Use sparingly — interactive states, active phase indicator, and key CTAs only. No other accent color.

**Typography**: IBM Plex Sans only, loaded from Google Fonts. No secondary font. Hierarchy through weight and size alone.

| Use | Weight | Size |
|-----|--------|------|
| UI labels / metadata | 400 | 12px |
| Body / task text | 400 | 14px |
| Section headers | 500 | 14px |
| Phase titles | 600 | 18px |
| App header / project name | 700 | 24px+ |

**Load animation**: On initial open, all UI elements fade in together (`opacity: 0 → 1`). CSS only. Duration: 250ms. Easing: `ease-out`. No movement, no slide, no stagger. A `sessionStorage` flag prevents replay on subsequent renders within the same session.

**What Bob should NOT look like**: A Jira clone. A generic to-do app. A startup dashboard with purple gradients. Anything that feels like a template.

---

## 7. localStorage Data Model

```javascript
// bob_projects — array of project summaries
[
  {
    id: "proj_abc123",
    name: "My Project",
    type: "app",            // website | landing | app | internal | marketing
    createdAt: 1711234567,
    updatedAt: 1711234567,
    currentPhase: "0",      // phase id
    status: "active"        // active | complete | archived
  }
]

// bob_project_{id} — full project state
{
  id: "proj_abc123",
  name: "My Project",
  type: "app",
  createdAt: 1711234567,
  updatedAt: 1711234567,
  phases: {
    "0": {
      status: "complete",   // locked | active | warned | complete
      tasks: [
        { id: "t1", text: "Define the problem...", done: true, custom: false },
        { id: "t2", text: "Custom task added by user", done: false, custom: true }
      ],
      checklist: [
        { id: "c1", text: "Problem statement written...", done: true }
      ],
      notes: "Free text notes from user",
      unlockedAt: 1711234567,
      completedAt: 1711234500
    },
    // ... other phases
  },
  prdUrl: "https://figma.com/...",  // from PRD phase
  stackDecision: ""                  // free text from Phase 1
}
```

---

## 8. Open Decisions

These are not yet decided and should be resolved in the first build session:

| Question | Options | Notes |
|----------|---------|-------|
| Phase navigation UI | Sidebar / top tabs / vertical stepper | Stepper feels most aligned with sequential workflow |
| Project list view | Card grid / simple list | List is cleaner for max 5 projects |
| Completed project state | Greyed out / separate archive section | Keep simple for v1 |
| Soft-warn UI | Modal / inline banner / toast | Toast feels lightest |

---

## 9. Out of Scope for v1

- Collaboration or sharing
- Export to PDF or Markdown
- Notifications or reminders
- Cloud sync
- Mobile-first layout
- More than 5 project types
- AI-generated phase content
- Integration with external tools (Notion, Linear, etc.)
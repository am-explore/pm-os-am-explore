# PM OS — Your AI Product Management Partner
> An AI-powered product management operating system. Clone it, fill in your context, and get a PM partner that knows your product.

> **Note:** This is Akash Mohan's personal customization of [agentmart/pm-os](https://github.com/agentmart/pm-os) (MIT licensed), published as a public example. Context-library files here are placeholders only — real product context lives in a private companion repo.

---

## What This Is

PM OS turns your AI coding assistant into a dedicated product partner — not a generic assistant, but a system that knows your product, your users, your strategy, and your competitive position. It compounds over time, getting sharper with every session.

**Works with:** Claude Code, GitHub Copilot (VS Code Agent Mode), and Claude Cowork. Each tool uses different configuration mechanisms — PM OS includes the right adapter files for each.

**The result:** You think faster, decide better, and ship with more confidence.

---

## Quick Start (10 minutes to launch)

### Step 1: Get PM OS

**Option A — Use as GitHub template (recommended):**
Click the green **"Use this template"** button at the top of this repo. This creates your own private copy.

**Option B — Clone directly:**
```bash
git clone https://github.com/agentmart/pm-os.git
cd pm-os
```

### Step 2: Choose your AI tool

<details>
<summary><strong>🔵 Claude Code / Claude Cowork</strong></summary>

Open Claude Code or Cowork with this folder as your project root.

```bash
cd pm-os
claude
```

**How it works:**
- `CLAUDE.md` is auto-loaded every session with `@` imports that pull in `SOUL.md` and all `context-library/` files
- `.claude/rules/` contains operating principles and output standards (auto-loaded)
- `.claude/agents/` contains 7 specialist reviewer subagents (available via `/agents`)
- `.claude/skills/` contains 15 skill router files — invoke via `/write-prd`, `/discover`, `/strategy`, etc.
- Full skill frameworks live in `skills/` — the router files point Claude to them

</details>

<details>
<summary><strong>🟢 GitHub Copilot (VS Code Agent Mode)</strong></summary>

1. Open this folder in VS Code
2. Copilot loads two instruction layers automatically:
   - **`.github/copilot-instructions.md`** — Repository-wide instructions (always loaded)
   - **`CLAUDE.md`** — Agent instructions (loaded in [agent mode](https://docs.github.com/en/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot))
3. Path-specific instructions in `.github/instructions/` provide context when working with skills or context-library files
4. Use `@workspace` to reference context-library files in Copilot Chat

**Note:** Copilot cannot auto-import files the way Claude Code can. When you mention trigger keywords, Copilot will follow the instructions in `CLAUDE.md` to read the relevant skill files using its file-reading tools.

</details>

### Step 3: Fill in the context library

Open each file in `context-library/` and fill in your actual product context. This is the highest-leverage 30 minutes you'll spend. The better your context, the smarter the OS.

> **Note:** Out of the box, the files in `context-library/` are placeholders. The "knows your product" promise activates after you fill them in — this step is what turns the template into *your* PM OS.

**Priority order:**
1. `company.md` — 5 min
2. `product.md` — 10 min
3. `users.md` — 10 min
4. `metrics.md` — 5 min

Each file has guidance comments explaining what to fill and why it matters.

### Step 4: Run your first session

Start with: *"I need to prioritize our Q3 roadmap. Our biggest challenge is [X]."*

---

## How It Works

### The Three Core Files

| File | Purpose | How often to update |
|------|---------|-------------------|
| **`CLAUDE.md`** | System brain — hub file with `@` imports for context, skills, workflows, modes | Rarely (when adding custom skills) |
| **`SOUL.md`** | PM judgment framework and values (imported by `CLAUDE.md` via `@SOUL.md`) | Never (unless you disagree with the philosophy) |
| **`README.md`** | This file — setup and reference | Never |

### The Context Library (your product knowledge)

| File | What it contains | Update frequency |
|------|-----------------|-----------------|
| `context-library/company.md` | Business model, mission, revenue, stage | Quarterly |
| `context-library/product.md` | Product overview, tech stack, current state | After major launches |
| `context-library/users.md` | Personas, JTBD, pain points, research | After research rounds |
| `context-library/competitors.md` | Competitive landscape, positioning | Monthly |
| `context-library/metrics.md` | North Star, AARRR funnel, OKRs | Weekly |
| `context-library/team.md` | Team structure, stakeholders, dynamics | When team changes |

### Skills (auto-loaded frameworks)

| Category | Skills | Triggered by |
|----------|--------|-------------|
| **Discovery** | Opportunity Solution Tree, User Interviews | "discovery", "research", "interview" |
| **Strategy** | Product Strategy Canvas | "strategy", "positioning", "vision" |
| **Execution** | PRD Writing, Roadmapping, Stakeholder Comms | "PRD", "roadmap", "stakeholder" |
| **Growth** | North Star, PLG Strategy, Launch Planning | "growth", "retention", "launch", "GTM" |
| **Research** | Competitive Research | "competitor", "market" |
| **Design** | Product Design Review | "design", "UX", "mockup", "prototype" |
| **Automation** | Routine Setup | "routine", "automate", "schedule", "recurring" |

### Sub-Agents (specialist reviewers)

| Agent | File | What they critique |
|-------|------|-------------------|
| Engineer | `sub-agents/engineer-reviewer.md` | Feasibility, tech debt, implementation risk |
| Designer | `sub-agents/designer-reviewer.md` | UX quality, design system, user flow gaps |
| Executive | `sub-agents/exec-reviewer.md` | Strategic alignment, business impact, board-readiness |
| User Researcher | `sub-agents/user-researcher.md` | Evidence quality, assumption risk, user empathy |
| Data Analyst | `sub-agents/data-analyst.md` | Metric validity, measurement plan, statistical rigor |
| Legal/Privacy | `sub-agents/legal-reviewer.md` | Compliance risk, data handling, regulatory flags |
| Competitor Watcher | `sub-agents/competitor-watcher.md` | Competitive gaps, differentiation, market timing |

### Proactive Agent Definitions (reviewer/monitor personas)

| Agent | File | What they do (when invoked) |
|-------|------|-------------|
| Metrics Tracker | `.claude/agents/metrics-tracker.md` | Monitors metrics, flags anomalies, suggests investigations |
| Assumption Validator | `.claude/agents/assumption-validator.md` | Tracks assumptions, designs validation experiments |
| Decision Logger | `.claude/agents/decision-logger.md` | Captures decisions with rationale and counter-arguments |
| Context Updater | `.claude/agents/context-updater.md` | Detects stale context-library entries, suggests updates |
| Risk Monitor | `.claude/agents/risk-monitor.md` | Scans for dependency risks, blockers, and threats |

These are persona/prompt definitions, not always-on background agents. Invoke them in a session, or wire them to Claude Code hooks / scheduled routines to make them continuous.

### Multi-Agent Debates

| Agent | File | What they do |
|-------|------|-------------|
| Debate Facilitator | `sub-agents/debate-facilitator.md` | Structures cross-reviewer tensions and agreements |
| Synthesis Agent | `sub-agents/synthesis-agent.md` | Produces weighted must-fix / should-fix / consider recommendations |

### Templates

| Template | Use for |
|----------|---------|
| `templates/PRD-template.md` | New feature or initiative briefs |
| `templates/experiment-template.md` | A/B tests and growth experiments |
| `templates/decision-template.md` | Product decision records |
| `templates/routine-template.md` | Custom PM automation routines |

### Routines (schedule-ready PM tasks)

Routines are markdown definitions. They run once wired to a scheduler (Claude Code `/schedule`, GitHub Actions cron) or invoked manually in a session.

| Routine | File | Suggested schedule |
|---------|------|-------------------|
| Weekly Metrics Digest | `routines/weekly-metrics-digest.md` | Monday 8am |
| Competitive Pulse | `routines/competitive-pulse.md` | Monday 9am |
| Backlog Grooming | `routines/backlog-grooming.md` | Weeknights 10pm |
| Stakeholder Update Draft | `routines/stakeholder-update-draft.md` | Friday 3pm |
| Sprint Retro Prep | `routines/sprint-retro-prep.md` | Bi-weekly |
| User Feedback Synthesis | `routines/user-feedback-synthesis.md` | Wednesday 10am |

### Hooks (quality gates)

| Hook | File | Default |
|------|------|---------|
| PRD Quality Gate | `hooks/prd-quality-gate.md` | advisory |
| Context Freshness | `hooks/context-freshness-check.md` | advisory |
| Launch Readiness | `hooks/launch-readiness.md` | advisory |

### Decision Log

Product decisions are captured in `decision-log/decisions/`. See `decision-log/README.md`.

---

## Directory Structure

```
pm-os/
├── CLAUDE.md               ← Hub file: AI reads this first (uses @imports for Claude Code)
├── SOUL.md                 ← PM identity and judgment framework
├── README.md               ← This file
├── LICENSE                 ← MIT License
├── CONTRIBUTING.md         ← Contribution guidelines
├── .gitignore
├── .claude/                ← Claude Code-specific configuration
│   ├── rules/
│   │   ├── operating-principles.md  ← Auto-loaded behavioral rules
│   │   └── output-standards.md      ← Auto-loaded quality standards
│   ├── agents/             ← Claude Code subagents (available via /agents)
│   │   ├── engineer-reviewer.md
│   │   ├── designer-reviewer.md
│   │   ├── exec-reviewer.md
│   │   ├── user-researcher.md
│   │   ├── data-analyst.md
│   │   ├── legal-reviewer.md
│   │   ├── competitor-watcher.md
│   │   ├── metrics-tracker.md       ← Proactive: metric anomaly detection
│   │   ├── assumption-validator.md  ← Proactive: assumption tracking
│   │   ├── decision-logger.md       ← Proactive: decision capture
│   │   ├── context-updater.md       ← Proactive: context freshness
│   │   └── risk-monitor.md          ← Proactive: risk scanning
│   └── skills/             ← Claude Code skill routers (invoke via /skill-name)
│       ├── write-prd/SKILL.md
│       ├── discover/SKILL.md
│       ├── strategy/SKILL.md
│       ├── competitive/SKILL.md
│       ├── roadmap/SKILL.md
│       ├── north-star/SKILL.md
│       ├── plg-audit/SKILL.md
│       ├── interview-prep/SKILL.md
│       ├── launch-plan/SKILL.md
│       ├── stakeholder-update/SKILL.md
│       ├── growth-experiment/SKILL.md
│       ├── design-review/SKILL.md
│       ├── retro/SKILL.md
│       ├── review-prd/SKILL.md
│       ├── review-strategy/SKILL.md
│       └── review-launch/SKILL.md
├── .github/
│   ├── copilot-instructions.md  ← GitHub Copilot repo-wide instructions
│   ├── instructions/            ← Copilot path-specific instructions
│   │   ├── skills.instructions.md
│   │   └── context-library.instructions.md
│   ├── CODEOWNERS
│   └── workflows/
│       └── close-prs.yml       ← Auto-closes stale PRs (add cron workflows here to schedule routines)
├── context-library/        ← Fill these with your product context
│   ├── company.md
│   ├── product.md
│   ├── users.md
│   ├── competitors.md
│   ├── metrics.md
│   └── team.md
├── skills/                 ← Auto-loaded PM frameworks
│   ├── discovery/
│   │   ├── SKILL-opportunity-solution-tree.md
│   │   └── SKILL-user-interview.md
│   ├── strategy/
│   │   └── SKILL-product-strategy.md
│   ├── execution/
│   │   ├── SKILL-prd-writing.md
│   │   ├── SKILL-roadmap.md
│   │   └── SKILL-stakeholder-communication.md
│   ├── growth/
│   │   ├── SKILL-launch-plan.md
│   │   ├── SKILL-north-star.md
│   │   └── SKILL-plg-strategy.md
│   ├── research/
│   │   └── SKILL-competitive-research.md
│   ├── design/
│   │   └── SKILL-product-design-review.md
│   └── automation/
│       └── SKILL-routine-setup.md
├── sub-agents/             ← Specialist reviewer personas
│   ├── engineer-reviewer.md
│   ├── designer-reviewer.md
│   ├── exec-reviewer.md
│   ├── data-analyst.md
│   ├── user-researcher.md
│   ├── legal-reviewer.md
│   ├── competitor-watcher.md
│   ├── debate-facilitator.md   ← Orchestrates multi-agent review debates
│   └── synthesis-agent.md      ← Produces weighted recommendations
├── templates/              ← Document templates
│   ├── PRD-template.md
│   ├── experiment-template.md
│   ├── decision-template.md    ← Product decision records
│   └── routine-template.md     ← Custom routine configuration
├── decision-log/           ← Institutional memory of product decisions
│   ├── README.md
│   └── decisions/
├── routines/               ← Schedule-ready recurring PM task definitions
│   ├── README.md
│   ├── weekly-metrics-digest.md
│   ├── competitive-pulse.md
│   ├── backlog-grooming.md
│   ├── stakeholder-update-draft.md
│   ├── sprint-retro-prep.md
│   └── user-feedback-synthesis.md
├── hooks/                  ← Quality gates for PM artifacts
│   ├── README.md
│   ├── prd-quality-gate.md
│   ├── context-freshness-check.md
│   └── launch-readiness.md
└── tools/                  ← Integrations and extensibility
    ├── README.md
    ├── custom-skill-template.md
    └── example-mcp-config.json
```

---

## Slash Commands

These map trigger words to skill files. **In Claude Code** they are native slash commands (skill routers live in `.claude/skills/`). **In GitHub Copilot** they are prompt shorthands — type them as natural language and Copilot follows the `CLAUDE.md` routing to load the right skill file.

| Command | What happens |
|---------|-------------|
| `/discover` | Full discovery cycle: OST → assumptions → experiments |
| `/strategy` | Product strategy canvas |
| `/write-prd [topic]` | Full PRD with sub-agent review |
| `/roadmap` | Quarterly roadmap planning |
| `/competitive [competitor]` | Deep competitive research + battlecard |
| `/north-star` | Define or refine your North Star Metric |
| `/plg-audit` | PLG audit with growth backlog |
| `/interview-prep [topic]` | User interview guide + synthesis template |
| `/launch-plan [feature]` | Full launch checklist + GTM plan |
| `/retro` | Sprint/project retrospective with insights + action items |
| `/stakeholder-update` | Draft stakeholder communication |
| `/growth-experiment` | Experiment design + analysis framework |
| `/setup-routine` | Create a custom PM automation routine |
| `/log-decision` | Capture a product decision with full context |
| `/mode [precise/creative]` | Switch between structured and divergent thinking |
| `/review-prd` | Trigger all 7 sub-agent reviewers on current PRD |

---

## Operating Modes

PM OS supports two thinking modes you can switch between at any time:

| Mode | Behavior | Best for |
|------|----------|----------|
| **Precise** (default) | Structured, repeatable, template-exact, data-driven, conservative | PRDs, stakeholder updates, metrics, launch checklists, decision memos |
| **Creative** | Divergent, provocative, explores edge cases, loose structure | Strategy sessions, discovery, brainstorming, competitive analysis, ideation |

Switch with `/mode precise` or `/mode creative`. Every session starts in Precise mode.

---

## Extending PM OS

### Add Custom Skills
Create your own PM frameworks by adding skill files to `skills/`. Copy `tools/custom-skill-template.md` to get started.

### Add Custom Routines
Automate recurring PM tasks by adding routine files to `routines/`. Copy `templates/routine-template.md` or use `/setup-routine`. Configure with Claude Code (`/schedule`) or Copilot Cloud Agent (GitHub Actions).

### Add Quality Hooks
Create custom quality gates by adding hook files to `hooks/`. Default enforcement is `advisory` — switch to `blocking` when ready.

### Connect External Tools (MCP)
Plug in Jira, Linear, Notion, Figma, analytics platforms, and more via MCP servers. Your AI partner can then read/write to these tools directly.

### Bring Your Own Data
Drop analytics exports, research syntheses, or competitive analyses into your context-library files.

See **`tools/README.md`** for full integration guide.

---

## Keeping the OS Sharp

**Update context after major events:**
- New user research → update `context-library/users.md`
- Competitor moves → update `context-library/competitors.md`
- New metrics data → update `context-library/metrics.md`
- Team changes → update `context-library/team.md`
- Strategic pivots → update `context-library/company.md`

**Recommended cadence:**
- Weekly: update metrics, log experiment results
- Monthly: update competitive context
- Quarterly: review and refresh all context files

---

## The Compound Effect

```
Month 1:  Your AI partner knows your product context
Month 3:  It anticipates your questions
Month 6:  It surfaces patterns you would have missed
Month 12: It's the institutional memory of your product team
```

---

## Philosophy

This OS is built on the conviction that:
1. Great PM decisions come from rigorous frameworks + deep user empathy + honest data
2. AI should add judgment, not just generate text
3. Context compounds — every session should build on the last
4. The best PM partner is opinionated, honest, and faster than you

---

## Credits & Inspiration
- Teresa Torres: Opportunity Solution Tree
- Marty Cagan: Product discovery philosophy
- Alberto Savoia: Pretotyping
- Roger Martin: Strategy as integrated choices
- Reforge / Brian Balfour: Growth loops and retention
- phuryn/pm-skills: Open source PM skills marketplace (MIT License)

---

*PM OS v1.0 — Built for Claude Code and GitHub Copilot*

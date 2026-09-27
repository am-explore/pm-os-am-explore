# SKILL: Roadmap & Prioritization
> Skill type: Framework Reference + Planning Workflow
> Auto-activates when: user mentions "roadmap", "prioritize", "backlog", "planning", "what to build next", "quarterly planning"
> Force load: /roadmap

---

## What This Skill Does
Guides roadmap construction and feature prioritization with explicit tradeoffs — not just a framework, but a complete decision process that connects every item to a strategic bet.

---

## Roadmap Philosophy

**A roadmap is a communication tool about bets under uncertainty.**

It is NOT:
- A commitment to ship exact features by exact dates
- A list of customer requests
- A feature factory backlog
- A document to satisfy leadership

It IS:
- A coherent sequence of bets tied to your strategy
- A way to align the team on priorities
- A communication tool for stakeholders (with appropriate abstraction per audience)
- A living document that updates as you learn

**The roadmap abstraction rule:**
- Engineering team: sprints + stories + rough dates
- Stakeholders: outcomes + initiatives + quarters (no features)
- Board: themes + metrics + annual OKRs (no quarters)

---

## Prioritization Frameworks

### Framework 1: RICE (Best for: Feature backlog prioritization)
Score = (Reach × Impact × Confidence) / Effort

| Factor | Definition | Scale |
|--------|-----------|-------|
| Reach | # users affected per quarter | Count |
| Impact | Impact on the metric if it works | 0.25, 0.5, 1, 2, 3 |
| Confidence | How sure are we the estimate is right? | 50%, 80%, 100% |
| Effort | Person-months of work | Person-months |

**When to use RICE:** When you have many features competing for similar user segments and need a fast, defensible ranking.

**RICE warning:** High RICE score ≠ strategically important. Always sanity-check: does the highest-RICE item advance your North Star?

### Framework 2: Opportunity Scoring (Best for: Discovery prioritization)
Score = Importance + (Importance - Satisfaction)

Identifies the gap between how important a job-to-be-done is and how well current solutions serve it.

### Framework 3: ICE (Best for: Growth experiment prioritization)
Score = Impact × Confidence × Ease (all 1-10)

**When to use ICE:** Growth experiments, A/B tests, optimization initiatives. Fast and intuitive.

### Framework 4: Kano Model (Best for: Feature classification)
Categories features into:
- **Basic (Must-have):** Absence causes dissatisfaction; presence is expected (e.g., reliable uptime)
- **Performance (More = better):** Linear satisfaction increase (e.g., speed)
- **Delighter:** Unexpected features that create disproportionate delight (e.g., Loom's reaction feature)
- **Indifferent:** Users don't care either way
- **Reverse:** Some users hate it (e.g., aggressive notifications)

**When to use Kano:** Deciding what NOT to build; identifying where investment in quality vs. novelty makes sense.

### Framework 5: Now/Next/Later (Best for: Stakeholder roadmaps)
Simple 3-horizon format that communicates direction without false precision:
- **Now (this quarter):** In progress or committed — specific
- **Next (next quarter):** High confidence — directional
- **Later (6+ months):** Under consideration — thematic

---

## The Prioritization Decision Process

> For a single hard call between competing options (rather than sequencing a whole roadmap), use `/evaluate` — `skills/strategy/SKILL-tradeoff-evaluation.md`. New requests should arrive here already routed by `/intake`.

### Step 1: Filter by Strategy
Before scoring anything, filter the backlog:
- Does this item connect to an OKR or strategic bet?
- If not, it goes to "Later" or gets removed entirely

### Step 2: Score Remaining Items
Apply the most relevant framework. Use RICE for feature backlog, ICE for experiments.

### Step 3: Sanity Check the Ranking
Ask the team:
- Does the top of this list feel right?
- Is there anything at the bottom that we're avoiding for emotional reasons?
- Is there anything at the top that's there because of squeaky stakeholders, not evidence?

### Step 4: Identify Dependencies and Sequencing
Some items enable others. Map the critical path:
- Which items must come first?
- Which items would make subsequent items 10x easier?
- What's the minimum viable sequence for learning?

### Step 5: Communicate Tradeoffs Explicitly
For every item you choose, name what you're not doing:
"We're building X this quarter, which means we're NOT building Y and Z."

This is the most important step. Unstated tradeoffs create politics. Stated tradeoffs create alignment.

---

## Roadmap Format for Stakeholders

### Outcome-Based Roadmap (Recommended)
Instead of: "Feature: Enhanced search functionality — Q2"
Write: "Users find relevant content 3x faster — Q2 | Initiative: Search overhaul"

| Outcome | Initiative | Confidence | OKR Connection | Quarter |
|---------|-----------|-----------|----------------|---------|
| [OUTCOME] | [INITIATIVE] | H/M/L | [OKR] | [Q] |

### Anti-Feature-Matrix Roadmap
Never show stakeholders a feature list. Show them a problem → bet → outcome chain.

---

## Roadmap Review Rhythm
- **Sprint level:** What's in the next 2 weeks? (Daily visibility)
- **Monthly:** Is the current quarter on track? Any learned pivots needed?
- **Quarterly:** Is the next quarter bet still right? What did we learn?
- **Annually:** Are the 3-year strategic bets still valid?

---

## Common Roadmap Failure Modes

❌ **The customer-request roadmap:** Every item traces back to a specific customer who complained. No strategic thread.

❌ **The date-driven roadmap:** Committed dates for 12 months out with detailed features. False precision creates broken trust.

❌ **The consensus roadmap:** Every stakeholder got something. Nothing coheres into a strategy.

❌ **The never-updated roadmap:** A beautiful document that doesn't reflect current reality.

✅ **The bet-based roadmap:** Each item is a hypothesis about what will move the North Star, with clear success criteria.

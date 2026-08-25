# SKILL: Opportunity Solution Tree (OST)
> Skill type: Framework Reference + Guided Workflow
> Auto-activates when: user mentions "discovery", "opportunity", "OST", "solution tree"
> Force load: /opportunity-solution-tree

---

## What This Skill Does
Guides the PM through Teresa Torres's Opportunity Solution Tree — the discipline of separating problem space (opportunities) from solution space, and ensuring every feature decision is connected to a user outcome.

This is the antidote to feature factory mode.

---

## The OST Framework

```
DESIRED OUTCOME (Business Goal)
    │
    ├── Opportunity 1 (User Need / Pain / Desire)
    │       ├── Opportunity 1a (Sub-need)
    │       │       ├── Solution A
    │       │       └── Solution B
    │       └── Opportunity 1b (Sub-need)
    │               └── Solution C
    │
    ├── Opportunity 2 (User Need / Pain / Desire)
    │       └── Opportunity 2a (Sub-need)
    │               ├── Solution D
    │               └── Solution E
    │
    └── Opportunity 3 (User Need / Pain / Desire)
```

**Key rule:** Never jump from Desired Outcome → Solution.
Always go: Outcome → Opportunity (user need) → Solution.

---

## How to Use This Skill

### Step 1: Define the Desired Outcome
Ask: What business metric do we want to move?
Format: "Increase [metric] from [current] to [target] by [date]"

Example: "Increase weekly active teams from 1,200 to 2,000 by end of Q3"

### Step 2: Identify Opportunities (User Needs)
Run the Interview Snapshot: Talk to 5-10 users. Ask:
- "Walk me through the last time you tried to [desired behavior]"
- "What made that harder than it needed to be?"
- "What would need to be true for you to do this 10x more often?"

Cluster findings into opportunity categories. An opportunity is:
✅ A user need, pain, or desire
✅ Stated in user language, not solution language
✅ Directly connected to the desired outcome
❌ NOT a feature request
❌ NOT a solution hypothesis

### Step 3: Prioritize Opportunities
Apply the Opportunity Score (Anthony Ulwick):
- **Importance:** How important is solving this? (1-10)
- **Satisfaction:** How satisfied are users with current solutions? (1-10)
- **Score:** Importance + (Importance - Satisfaction) → higher = better opportunity

Focus on high-importance, low-satisfaction opportunities.

### Step 4: Generate Solutions (per priority opportunity)
For each top-priority opportunity, generate 3+ solution options. Ask:
- What's the simplest thing that could work?
- What's the most creative/unexpected solution?
- What would a 10x better version look like?

### Step 5: Identify Assumptions per Solution
For each solution: "What would need to be true for this to work?"
Categorize assumptions: Value / Usability / Viability / Feasibility

### Step 6: Design Tests for Top Assumptions
Use the Assumption Risk Matrix:
- **High evidence confidence + High importance** → Build it
- **Low evidence confidence + High importance** → Test it first
- **Low evidence confidence + Low importance** → Deprioritize
- **High evidence confidence + Low importance** → Skip it

---

## OST Output Template

**Desired Outcome:** [METRIC GOAL]

**Priority Opportunity:** [USER NEED IN USER LANGUAGE]
- Evidence: [RESEARCH SUPPORTING THIS]
- Importance score: [X/10]
- Satisfaction score: [X/10]
- Opportunity score: [CALCULATED]

**Solution Options:**
1. [SOLUTION A] — Key assumption: [ASSUMPTION] — Test: [EXPERIMENT]
2. [SOLUTION B] — Key assumption: [ASSUMPTION] — Test: [EXPERIMENT]
3. [SOLUTION C] — Key assumption: [ASSUMPTION] — Test: [EXPERIMENT]

**Recommended bet:** [SOLUTION] because [REASONING]
**What we'll learn first:** [EXPERIMENT DESIGN]

---

## Common OST Mistakes
- ❌ Starting with solutions and working backwards to "opportunities"
- ❌ Treating every customer feature request as an opportunity
- ❌ Having so many branches the tree becomes unnavigable
- ❌ Never updating the tree as you learn new things
- ✅ Revisiting the tree every sprint to reflect new learning

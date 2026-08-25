# SKILL: North Star Metric
> Skill type: Guided Workshop + Framework
> Auto-activates when: user mentions "north star", "NSM", "OKR", "key metric", "what to measure", "metrics framework"
> Force load: /north-star

---

## What This Skill Does
Facilitates the North Star Metric definition process, designs the metric cascade from NSM to OKRs to leading indicators, and creates the measurement framework for the whole team.

---

## Why the North Star Metric Matters

The NSM is the one number that, if it goes up over time, means:
1. You're creating real, durable value for users
2. The business will be healthy as a consequence

Without a North Star, you get:
- Teams optimizing for local maxima (their feature's metric) at the cost of the whole
- Roadmap decisions that can't be connected to a shared outcome
- Stakeholder debates that have no resolution mechanism

---

## North Star Metric Definition Workshop

### Step 1: Test Your Candidate Metrics

For each metric candidate, answer these 5 questions:

| Question | What to look for |
|----------|----------------|
| Does this represent real user value, not just usage? | Activity ≠ value. "Users logged in" ≠ users got value. |
| Is it leading (future indicator) or lagging (outcome)? | Prefer leading. Revenue is lagging. |
| Can a team take action on it? | If it can only be moved by external factors, it's not a metric — it's a result. |
| Does it compound over time? | The best NSMs grow as users get more embedded. |
| Would a technically high number actually be bad? | (Goodhart's Law check) |

### Step 2: Common NSM Patterns by Business Model

| Business Model | Example NSM |
|---------------|-------------|
| B2B SaaS (usage-based) | "Weekly active teams with 3+ collaborations" |
| Consumer app | "Users who complete 1+ [core action] per week" |
| Marketplace | "Successful transactions per week" |
| Content/media | "Articles read to completion per week" |
| Developer tools | "APIs called per active developer per week" |
| E-commerce | "Repeat purchases per user per year" |
| PLG SaaS | "Users who reach activation event within 7 days" |

### Step 3: The NSM Formula Template
"[FREQUENCY]-[USERS] who [COMPLETE CORE ACTION] [CONTEXT/QUALIFIER]"

Examples:
- "Weekly active users who create and share at least one document"
- "Monthly teams where every member has sent at least 5 messages"
- "Developers who make at least 10 successful API calls per week"

### Step 4: Validate Your NSM
Run the correlation check (retrospective):
- Look at your best, most satisfied customers
- Do they have high values of your candidate NSM?
- Look at churned customers
- Did they have low values before churning?

If yes: your NSM is a leading indicator of retention and growth.
If no: wrong metric.

---

## The Metric Cascade

### Level 1: North Star Metric
*What this skill helps you define above.*

### Level 2: Input Metrics (Leading Indicators)
These are the levers that move the NSM. Usually 3-5.

If NSM = "Weekly teams with 3+ collaborations," inputs might be:
- New team creation rate
- Invitation conversion rate (invited → active member)
- Time to first collaboration
- Feature engagement depth

**For each input metric:**
- Which team owns it?
- What's the current value?
- What would moving it by X% do to the NSM?

### Level 3: OKRs
Quarterly objectives that target improvement in the input metrics.

**Format:**
Objective: [Inspiring, directional goal]
KR1: [Input metric] from [X] to [Y] by [DATE]
KR2: [Input metric] from [X] to [Y] by [DATE]

### Level 4: Feature-Level Success Metrics
Each feature should have a hypothesis about which input metric it moves and by how much.

"This feature will improve [INPUT METRIC] by [X]% because [MECHANISM]."

---

## The Anti-Metrics (Guardrails)

Define what you will NOT sacrifice to move your NSM:

| Guardrail | Current | Threshold | Why |
|-----------|---------|-----------|-----|
| Churn rate | [%] | Max [%] | Revenue health |
| Support ticket volume | [#/week] | Max [#] | Quality signal |
| Error rate | [%] | Max [%] | Technical health |
| Time-to-first-response (support) | [hrs] | Max [hrs] | Trust |

**Rule:** If moving the NSM requires sacrificing a guardrail metric, that's not a win — that's gaming.

---

## Metric Review Cadence

| Cadence | Who | What |
|---------|-----|------|
| Weekly | PM + Data | NSM trend + 3 input metrics. 15 min. |
| Monthly | Product team | Full funnel review. Experiment results. OKR progress. |
| Quarterly | Leadership | OKR scoring. NSM trajectory. Strategy calibration. |
| Annually | All hands | NSM evolution: is this still the right metric as the product matures? |

---

## NSM Anti-Patterns

❌ **Revenue as NSM:** Revenue is an output. It tells you something happened, not why or whether users got value.

❌ **Vanity metrics:** "Total users registered" goes up even if no one uses the product.

❌ **The average trap:** "Average session duration" can improve when bad users leave, not when experience improves.

❌ **Multiple NSMs:** You cannot have three North Stars. Pick one. The debate about which one to pick IS the strategic conversation.

❌ **Never revisiting the NSM:** As products mature, the right NSM changes. Startups measure activation; growth-stage companies measure retention; mature companies measure expansion.

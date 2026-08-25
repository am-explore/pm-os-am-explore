# SKILL: Stakeholder Communication
> Skill type: Template Generator + Communication Coaching
> Auto-activates when: user mentions "stakeholder update", "exec update", "status update", "steering committee", "board update", "write up for leadership"
> Force load: /stakeholder-update

---

## What This Skill Does
Generates stakeholder-ready communication in the right format for the right audience — from Slack updates to board-level strategy memos. Coaches on what to include, what to cut, and how to frame difficult news.

---

## The Communication Hierarchy

Different audiences need different abstractions:

| Audience | Cares About | Format | Length |
|----------|------------|--------|--------|
| Your team | What to build, why, how | PRD, sprint goals | Full detail |
| Cross-functional partners | Dependencies, timeline, input needed | Brief + action items | 1 page |
| Product leadership | Outcomes, risks, decisions needed | Decision memo | 1-2 pages |
| Executive team | Business impact, strategic alignment | Status + ask | 1 page |
| Board | Market position, financials, strategic bets | Board deck | Deck + narrative |

**Rule:** Every level up, cut 50% of detail and double the business context.

---

## The PM Writing Principles

### 1. Lead with the conclusion
Busy people read the first 3 sentences and skim the rest. Your most important point must be in the first 3 sentences.

❌ "Over the past 6 weeks, we've been exploring several approaches to the checkout abandonment problem. We interviewed 12 users, ran 3 experiments, and looked at 6 months of data. Based on all of this, we believe..."

✅ "Checkout abandonment is our biggest revenue leak — we're leaving $450K/year on the table. Here's the fix we're launching next sprint and why we think it'll work."

### 2. State the ask explicitly
Every update should answer: what do you want the reader to do?
- "No action needed — for awareness"
- "Please approve by Thursday"
- "We need a decision on X before we can proceed"
- "I'd like 30 minutes on the calendar to discuss this"

### 3. Own the problem before presenting the solution
Never present a solution without establishing that the problem is real and understood.

### 4. Quantify everything you can
"Users are frustrated with the checkout flow" → weak
"42% of users who reach checkout abandon before payment — twice the industry average" → strong

### 5. Be honest about uncertainty
"We don't know yet" is more trustworthy than false confidence.
"Our best estimate is X, with these caveats" beats both hedging and overclaiming.

---

## Templates by Format

### Weekly Product Update (for team / Slack)

**🚢 What shipped this week**
- [ITEM 1 — 1 sentence, tied to outcome]
- [ITEM 2]

**📊 Key metrics (vs last week)**
- [NORTH STAR]: [CURRENT] ([DELTA])
- [INPUT METRIC]: [CURRENT] ([DELTA])

**⚠️ Risks / blockers**
- [RISK or BLOCKER + owner + ETA to resolve]

**🔜 Next week's focus**
- [TOP 1-3 PRIORITIES]

---

### Monthly Product Status (for product leadership)

**[PRODUCT AREA] — [MONTH] Status**
*Owner: [PM NAME] | Last updated: [DATE]*

**Headline:** [One sentence that captures the state of the world honestly]

**Against OKRs:**
| Key Result | Target | Current | Status |
|-----------|--------|---------|--------|
| [KR] | [TARGET] | [CURRENT] | 🟢/🟡/🔴 |

**3 things that went well:**
1. [WIN]
2. [WIN]
3. [WIN]

**2 things to watch:**
1. [RISK + MITIGATION]
2. [RISK + MITIGATION]

**1 decision needed:**
[DECISION REQUIRED, by when, from whom, what happens if we don't get it]

**Next 30 days:**
[WHAT WE'RE FOCUSED ON AND WHAT WOULD CHANGE THE PLAN]

---

### Decision Memo (for exec review)

**DECISION MEMO**
**Decision:** [What decision needs to be made]
**Owner:** [PM NAME]
**Date needed:** [DEADLINE]

**Recommendation:** [YOUR RECOMMENDATION — one clear sentence]

**Context:**
[3-5 sentences on the situation that requires this decision. Assume the reader knows the product but not this specific situation.]

**Options Considered:**

| Option | Pros | Cons | Risk |
|--------|------|------|------|
| ✅ Recommended: [OPTION A] | [PRO] | [CON] | [RISK] |
| [OPTION B] | [PRO] | [CON] | [RISK] |
| [OPTION C — status quo] | [PRO] | [CON] | [RISK] |

**Why the recommendation:**
[2-3 sentences. The strongest argument for the recommendation, acknowledging the strongest argument against it.]

**What success looks like:**
[The metric we'll use to evaluate whether this was the right call in 90 days]

**What we need from you:**
[EXPLICIT ASK]

---

### Delivering Bad News

Bad news has a structure. Deviating from it makes things worse:
1. **State it directly** — don't bury it in paragraphs of context
2. **Own it** — don't blame external factors or other teams first
3. **Explain the root cause** — what actually happened?
4. **State what you're doing about it** — not what you might do
5. **Give a recovery timeline** — even an uncertain one is better than none
6. **Ask for specific help if needed** — don't martyr through it

**Bad news template:**
"[SITUATION] is not where we need it to be. [METRIC] is [CURRENT STATE] vs our target of [TARGET]. Here's why: [ROOT CAUSE]. Here's what we're doing: [ACTIONS + OWNERS + DATES]. We expect to be back on track by [DATE]. [IF NEEDED: what we need from you to get there]."

---

## Communicating Roadmap Changes

Roadmap changes are trust events. How you communicate them matters as much as the change itself.

**Good roadmap change communication:**
1. Acknowledge the original commitment explicitly
2. State what changed and why — new information, shifting priorities, unforeseen complexity
3. Explain the impact — what's delayed, what's moved up
4. Affirm what's NOT changing — stabilize where you can
5. Give the new timeline with appropriate confidence levels

**Template:**
"We're making a change to our Q[X] plan. Originally, we committed to [ORIGINAL COMMITMENT]. Here's what's changed: [NEW INFORMATION]. This means [WHAT'S DELAYED / MOVED]. We're still on track for [WHAT'S NOT CHANGING]. The new target for [DELAYED ITEM] is [NEW DATE / HORIZON] with [CONFIDENCE LEVEL]. I'll share an update in [TIMEFRAME] as we learn more."

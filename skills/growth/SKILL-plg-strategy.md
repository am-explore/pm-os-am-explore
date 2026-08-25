# SKILL: Product-Led Growth (PLG) Strategy
> Skill type: Framework Reference + Audit Workflow
> Auto-activates when: user mentions "PLG", "product-led", "activation", "onboarding", "free trial", "freemium", "growth loop", "virality", "retention"
> Force load: /plg-audit

---

## What This Skill Does
Runs a comprehensive PLG audit across the full user lifecycle — from acquisition through expansion — and generates a prioritized growth backlog with experiment designs.

---

## PLG Foundations

**The core insight:** In PLG, the product IS the marketing, sales, and retention channel. Every product decision has a growth implication.

**The PLG equation:**
Good PLG = (Fast time-to-value) × (Viral mechanics) × (Expansion revenue) × (Low churn)

**2026 PLG context:**
- Time-to-value is now measured in seconds, not onboarding steps
- AI-powered onboarding is table stakes (ask the user what they want, configure instantly)
- Pricing is shifting from per-seat to per-task to per-outcome
- The "user" is increasingly an AI agent, not a human — design for both

---

## PLG Audit Framework

### Layer 1: Acquisition
**Key question:** How do new users find and choose you?

| Audit Area | Current State | PLG Score (1-5) | Top Opportunity |
|-----------|--------------|----------------|----------------|
| Organic / SEO | | | |
| Viral / word of mouth | | | |
| Product-led referral program | | | |
| Freemium / free trial conversion | | | |
| Self-serve signup (no sales required) | | | |
| Network effects (each user makes product better) | | | |

**Key metrics:**
- CAC (Customer Acquisition Cost)
- Organic vs. paid acquisition ratio
- Viral coefficient (K-factor): `invitations sent × conversion rate`
- Time from awareness to signup

### Layer 2: Activation — THE MOST IMPORTANT LAYER
**Key question:** How fast do users reach their first "aha moment"?

**The activation law:** Every hour between signup and the aha moment is a churn accelerant.

**Aha moment definition for this product:** [Fill from context-library/users.md]

**Activation audit steps:**
1. Map every step between signup → aha moment
2. Identify the drop-off point with the highest fallout
3. Calculate time-to-activation percentiles: p25, p50, p75
4. Segment activation rate by acquisition channel, user type, pricing tier

| Step in Activation Flow | Completion Rate | Drop-off Delta | Priority |
|------------------------|----------------|----------------|---------|
| [STEP 1] | [%] | | |
| [STEP 2] | [%] | | |
| [AHA MOMENT] | [%] | | |

**Activation improvement patterns:**
- Remove friction: every required field, confirmation email, and tutorial step bleeds activation
- Personalize the path: ask "what are you trying to do?" → route to value instantly
- Empty state magic: the worst moment is the blank screen after signup — fill it meaningfully
- Progressive onboarding: don't front-load all setup — defer until needed
- Early win design: find the smallest possible action that delivers real value in < 5 minutes

### Layer 3: Retention
**Key question:** Why do users come back?

**The retention hierarchy:**
1. **Habit retention:** Daily/weekly product use baked into their workflow
2. **Feature retention:** Specific features they rely on enough to not want to leave
3. **Switching cost retention:** Data, integrations, team networks built in your product
4. **Community retention:** The social fabric of your product keeps them

**Retention metrics:**
- Day 1, Day 7, Day 30, Day 90 retention curves
- Net Revenue Retention (NRR) — target: >120% for healthy PLG companies
- Feature adoption depth: % of users using 3+ key features
- Reactivation rate: % of churned users who return

**Cohort analysis template:**
Group users by: signup week, acquisition channel, activation event, persona
Look for: which cohorts retain best? What's different about them?

### Layer 4: Referral / Virality
**Key question:** Does using the product naturally create more users?

**Viral loop types:**
1. **Collaboration viral:** Invite teammates to view/edit (Figma, Notion, Slack)
2. **Output viral:** Sharing something created with the product carries the brand (Canva, Loom)
3. **Achievement viral:** Users share milestones/results (Spotify Wrapped, Strava)
4. **Integration viral:** Your product appears in other people's workflows (Calendly, DocuSign)
5. **Referral incentive viral:** Explicit reward for bringing friends (Dropbox, Cash App)

Viral coefficient (K-factor) = (Avg invitations per user) × (Invitation conversion rate)
- K > 1: exponential growth
- K = 0.5-1: strong assist to growth
- K < 0.3: viral is not a primary lever

### Layer 5: Revenue / Expansion
**Key question:** How does revenue grow per customer over time?

**Expansion motions:**
- Seat expansion: value grows with team size (Slack, Linear)
- Usage expansion: value grows with usage (OpenAI API, AWS)
- Feature upsell: power users upgrade for advanced capabilities
- Cross-sell: adjacent product line (HubSpot CRM → Marketing → Service)
- Network expansion: customer's customers become your customers (Stripe, Twilio)

**Product-Qualified Lead (PQL) definition:**
A PQL is a free/trial user who has taken [ACTIVATION EVENT] + [USAGE SIGNAL] and is ready for a sales conversation or upgrade prompt.

Define your PQL: [USER HAS DONE X AND Y WITHIN Z DAYS]

**PQL conversion tactics:**
- In-app upgrade prompt at the moment of hitting the PQL signal
- Automated email sequence triggered by PQL signal
- Sales notification + outreach for high-value PQLs
- Feature gate that surfaces value before blocking (see the locked feature, understand why it matters, then hit the paywall)

---

## User Behavior Analytics Playbook

### The 5 Analytics Questions Every PM Should Answer Weekly
1. **Where are users dropping off in the activation flow?** → Funnel analysis
2. **Which features correlate with long-term retention?** → Correlation analysis (Mixpanel / Amplitude)
3. **Which user segments have the best expansion revenue?** → Cohort + revenue analysis
4. **What are power users doing that average users aren't?** → Behavioral segmentation
5. **Where is friction in the user journey?** → Session recordings + heatmaps

### Instrumentation Must-Haves
Every product needs these events tracked at minimum:
- `user_signed_up` (with: acquisition channel, referral source)
- `activation_event_completed` (the aha moment)
- `core_feature_used` (per key feature)
- `collaboration_started` (if collaborative product)
- `upgrade_prompted` (with: trigger, location)
- `upgrade_completed` / `upgrade_rejected` (with: plan, amount)
- `churned` (with: last activity date, usage depth)

### A/B Test Design for Growth
Every growth experiment needs:
1. **Hypothesis:** "We believe [CHANGE] will cause [USERS] to [BEHAVIOR] because [REASON]"
2. **Primary metric:** [THE ONE METRIC THIS TEST WILL MOVE]
3. **Guardrail metrics:** [METRICS THAT MUST NOT DEGRADE]
4. **Sample size:** [CALCULATE — use stats calculator for 80% power, 95% confidence]
5. **Runtime:** [MIN 2 WEEKS to account for day-of-week effects]
6. **Decision criteria:** Ship if [PRIMARY METRIC improves by X% and guardrails hold]

---

## PLG Backlog Generator
When you run `/plg-audit`, this skill will:
1. Audit each layer of the PLG model
2. Identify the biggest gap (lowest-performing layer)
3. Generate 5 experiment ideas for that layer
4. Score each experiment on: Impact × Confidence × Effort (ICE)
5. Output a prioritized growth backlog

**Focus rule:** Work the weakest layer first. Filling a leaky bucket is futile.

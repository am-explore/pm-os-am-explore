# SKILL: Launch Planning & GTM
> Skill type: Checklist + Planning Workflow
> Auto-activates when: user mentions "launch", "GTM", "go-to-market", "release plan", "ship", "announce"
> Force load: /launch-plan

---

## What This Skill Does
Builds a complete launch plan: readiness checklist, GTM strategy, communication plan, rollout strategy, and post-launch review schedule.

---

## Launch Philosophy

**A launch is not the end of a project. It's the beginning of a learning cycle.**

The goal of a launch is not to ship — it's to learn whether your bets were right, at the smallest possible risk, with the fastest possible feedback loop.

**The launch maturity spectrum:**
1. Feature flag → team only
2. Internal dogfood → all employees
3. Closed beta → invited customers
4. Open beta → self-select customers
5. Gradual rollout → X% of traffic
6. GA → 100% of users
7. Marketing launch → external announcement

You don't need to go from 0 → 7. Match launch type to risk level and confidence.

---

## Launch Readiness Checklist

### Product Readiness
- [ ] Core user flow works end-to-end on all supported platforms
- [ ] Edge cases and error states handled gracefully
- [ ] Performance tested under expected load
- [ ] Instrumentation live and validated (events firing correctly)
- [ ] Feature flag in place for controlled rollout
- [ ] Rollback plan documented and tested

### Metrics Readiness
- [ ] Baselines captured for all success metrics
- [ ] Analytics dashboards created and shared with team
- [ ] Alerting configured for guardrail metric breaches
- [ ] First analysis date scheduled (suggest: 2 weeks post-launch)

### Support Readiness
- [ ] Help documentation written and published
- [ ] Support team briefed and trained
- [ ] Known issues / limitations documented
- [ ] FAQs prepared for expected questions

### Communication Readiness
- [ ] Internal announcement ready (what it does, why it matters, how to use it)
- [ ] Customer communication written (if externally visible)
- [ ] Sales/CS enablement: battlecard updated, demo updated
- [ ] Marketing assets ready (if marketing launch)

### Legal / Compliance
- [ ] Privacy review completed (if new data handling)
- [ ] Terms of service update required? (if yes, done)
- [ ] Enterprise customers' DPAs reviewed (if applicable)
- [ ] Accessibility baseline met

---

## GTM Strategy by Launch Type

### Internal Feature / Workflow Improvement
- Announce in team channel with: what changed, why, how to use it
- Update internal documentation
- No customer communication needed

### Beta Launch (Customer-facing)
- Identify beta cohort: power users, design partners, customers who requested the feature
- Personal outreach from PM or CSM — not blast email
- Set explicit expectations: "This is early, we want your feedback"
- Create feedback channel (Slack, email, dedicated survey)
- Commit to weekly synthesis of feedback → product changes

### GA Launch (Low-complexity feature)
- In-app announcement for relevant users
- Help article published
- Optional: email for high-visibility features
- Sales/CS heads-up 48 hours before

### GA Launch (High-impact feature)
- Full communication plan: email, in-app, blog, social
- Press outreach if newsworthy
- Demo video or walkthrough GIF
- Customer success webinar or office hours
- Sales enablement: new talk track, updated demo, battlecard
- Analyst briefings if relevant

### Pricing / Packaging Change
- Extra care: pricing changes are high-trust-risk moments
- Clear, early communication with plenty of lead time
- Grandfather existing customers where possible
- CEO-level communication for significant changes
- FAQ document addressing all anticipated concerns
- CSM outreach to top accounts before announcement

---

## Communication Templates

### Internal Launch Announcement

**Subject:** 🚀 [Feature Name] is live

**What we shipped:**
[2-3 sentences — plain English, no jargon]

**Why it matters:**
[Connect to the user problem and the metric we're trying to move]

**How to use it:**
[1-3 sentences or link to help article]

**What success looks like:**
[The metric we're watching and what we expect]

**Feedback:**
[Where to share observations]

---

### Customer Beta Invite

**Subject:** You're invited: Early access to [feature]

Hi [NAME],

We're getting ready to launch [FEATURE], and based on how you use [PRODUCT], I think you'd be the perfect person to try it early and give us feedback.

[FEATURE] lets you [DO WHAT], which means [OUTCOME THEY CARE ABOUT].

To join the beta: [CTA]

I'll personally read every piece of feedback you share. This is early, so expect rough edges — that's exactly why your input matters.

Thanks,
[PM NAME]

---

## Post-Launch Review Schedule

| Timeline | Action |
|----------|--------|
| Day 1 | Monitor dashboards. Check for errors, anomalies. Rapid response if critical issues. |
| Day 3 | First user feedback synthesis (support tickets, beta feedback, session recordings). |
| Day 7 | First metric review: activation rate, core engagement, error rate. Share update with team. |
| Day 14 | Full success metrics review against targets. Decision: iterate, stay the course, or rollback. |
| Day 30 | Cohort retention analysis. Did users who activated continue to use it? |
| Day 90 | Impact assessment: did this move the North Star Metric? What did we learn? |

---

## Launch Retrospective Template

**Feature:** [NAME]
**Launch date:** [DATE]
**PM:** [NAME]

**Did we achieve our success metrics?**
| Metric | Target | Actual | Delta |
|--------|--------|--------|-------|
| [METRIC] | [TARGET] | [ACTUAL] | [+/-] |

**What went well?**
[What should we do more of on future launches?]

**What went poorly?**
[What would we do differently?]

**What surprised us?**
[Things users did that we didn't expect]

**What we're doing next based on what we learned:**
[Concrete follow-up actions]

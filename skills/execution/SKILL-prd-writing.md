# SKILL: PRD Writing
> Skill type: Guided Workflow + Template Generator
> Auto-activates when: user mentions "PRD", "spec", "product requirement", "write up", "brief"
> Force load: /write-prd

---

## What This Skill Does
Produces production-ready PRDs that are short, opinionated, and decision-forcing.
Not documents that describe features. Documents that communicate bets.

---

## PRD Philosophy

**A PRD is a decision document.** Its real job is to surface assumptions and tradeoffs so the team can push back before anyone writes a line of code.

**Length target:** 1-2 pages for most features. 3-4 pages for complex systems.
A PRD that takes 30 minutes to read has already failed.

**The test:** After reading this PRD, can engineering estimate it and design challenge it without a meeting?

---

## PRD Quality Signals

✅ The problem section is longer than the solution section
✅ There are explicit tradeoffs stated ("We chose X over Y because...")
✅ Success metrics are defined and measurable
✅ Assumptions are listed explicitly
✅ Open questions are surfaced, not buried
✅ There's a clear "what we're NOT building" section
❌ Solution described before problem
❌ No data or user research referenced
❌ Success metrics are activities (shipped on time) not outcomes (X% improvement)
❌ No edge cases or constraints considered
❌ Written to get approval, not to invite challenge

---

## PRD Template

---

# [Feature / Initiative Name]
**Author:** [PM NAME]
**Status:** [Draft / In Review / Approved / Shipped]
**Date:** [DATE]
**Links:** [OST | User Research | Mocks | Epic]

---

## TL;DR
*One paragraph. Problem. Solution. Why now. Expected impact. Time horizon.*

---

## Problem Statement

### The User Problem
[Write this in user language. What job are they trying to do? Where are they failing today? How do we know this is real — what's the evidence from research or data?]

### The Business Problem
[Why does this matter to the business? Which metric(s) does this move? What's the current gap?]

### Why Now?
[Why is this the right thing to build this quarter vs last quarter or next quarter?]

---

## Users
**Primary user:** [PERSONA from users.md]
**Secondary users (if any):** [PERSONA]
**Out of scope users:** [WHO WE'RE NOT SOLVING FOR — be explicit]

---

## Solution

### What We're Building
[Plain English description of the solution. Not a feature list. A narrative of the experience.]

### What We're NOT Building (and Why)
[Options you considered and rejected. This is one of the most valuable sections — it saves future arguments.]

| Option | Why We Rejected It |
|--------|-------------------|
| [OPTION A] | [REASON] |
| [OPTION B] | [REASON] |

### UX / Flow
[Link to Figma / mocks. Or describe the key user flow in plain language if mocks don't exist yet.]

Key flows:
1. [FLOW 1 — happy path]
2. [FLOW 2 — edge case]
3. [FLOW 3 — error state]

---

## Success Metrics

| Metric | Current | Target | Timeframe | How We'll Measure |
|--------|---------|--------|-----------|------------------|
| [PRIMARY METRIC] | [X] | [Y] | [DATE] | [TOOL/METHOD] |
| [SECONDARY METRIC] | [X] | [Y] | [DATE] | [TOOL/METHOD] |

**Guardrail metrics** (must not get worse):
- [METRIC] stays above [THRESHOLD]

**How we'll know if this worked:** [1-2 sentences on the evaluation criteria post-launch]

---

## Assumptions
> Things that would need to be true for this to succeed. The riskiest assumptions should be tested before or during build.

| Assumption | Risk Level | How We'll Validate |
|-----------|-----------|-------------------|
| [ASSUMPTION] | H/M/L | [TEST] |
| [ASSUMPTION] | H/M/L | [TEST] |

---

## Technical Considerations
[Written with engineering, not by engineering. Known constraints, dependencies, data requirements, API integrations, performance requirements, security implications.]

- Dependencies: [LIST]
- Data requirements: [EVENTS TO TRACK]
- Scale requirements: [IF RELEVANT]
- Known risks: [TECHNICAL RISKS]

---

## Phasing (if applicable)

| Phase | Scope | Launch criteria | ETA |
|-------|-------|----------------|-----|
| Phase 1 (MVP) | [SCOPE] | [CRITERIA] | [DATE] |
| Phase 2 | [SCOPE] | [CRITERIA] | [DATE] |

---

## Launch Plan
- **Release type:** [GA / Beta / Feature flag / A/B test]
- **Rollout:** [100% / Gradual — X% → X%]
- **Communication:** [Internal / Customer comms needed?]
- **Support readiness:** [Help docs / Training needed?]
- **Rollback plan:** [If metrics go wrong, what do we do?]

---

## Open Questions
> Explicitly surface what's unresolved. Don't bury uncertainty.

| Question | Owner | Due Date |
|---------|-------|---------|
| [QUESTION] | [NAME] | [DATE] |

---

## Decision Log
| Date | Decision | Rationale |
|------|---------|-----------|
| [DATE] | [DECISION] | [WHY] |

---

## Sub-Agent Review Checklist
- [ ] **Engineering review:** Feasibility, complexity, hidden dependencies
- [ ] **Design review:** UX quality, design system alignment
- [ ] **Data review:** Instrumentation plan, metric validity
- [ ] **Legal/Privacy review:** Data handling, compliance flags
- [ ] **Exec review:** Strategic alignment, business case strength

---

## Multi-Agent PRD Review Protocol
When PRD is ready for review, invoke:
`/review-prd` → triggers all sub-agents to review in parallel → surfaces consolidated critique → PM addresses top issues → PRD updated → final approval

Top 3 things reviewers look for:
1. Is the problem clearly validated with evidence?
2. Are the success metrics actually measurable and outcome-focused?
3. Are the most critical assumptions identified and testable?

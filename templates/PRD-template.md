# PRD: [Feature / Initiative Name]
**Author:** 
**Status:** Draft
**Date:** 
**Links:** 

---

## TL;DR
*One paragraph. Problem + solution + why now + expected impact.*

---

## Problem Statement

### The User Problem


### The Business Problem


### Why Now?


---

## Users
**Primary user:** 
**Secondary users:** 
**Out of scope:** 

---

## Solution

### What We're Building


### What We're NOT Building (and Why)
| Option | Why We Rejected It |
|--------|-------------------|
| | |

### Key User Flows
1. 
2. 
3. 

---

## Acceptance Criteria (ISC — Ideal State Criteria)
> Inspired by the Ideal State Criteria discipline from [danielmiessler/TheAlgorithm](https://github.com/danielmiessler/TheAlgorithm) — not that repo's content, just its method. Every criterion below must be binary-testable (true/false, pass/fail), not a matter of opinion. This is what makes a PRD "done" instead of merely "read."

| # | Type | Criterion | Test |
|---|------|-----------|------|
| F1 | Functional | | |
| S1 | Structural | | |
| B1 | Behavioral | | |
| N1 | Negative constraint (must NOT happen) | | |

**Type key:** **[F]unctional** — the system does X. **[S]tructural** — the system is built/shaped a certain way (schema, architecture, permission model). **[B]ehavioral** — the system responds to a specific input/sequence a specific way. **[N]egative constraint** — an explicit thing that must not happen (a regression, a side effect, a boundary that must hold).

**Before marking this PRD ready for review, self-check against three gates:**
- **Coverage** — does every facet of "done" have at least one ISC covering it? (no silent gaps)
- **Tightness** — could any single criterion be deleted and the spec still fully describe success? If yes, cut it (no padding/redundancy)
- **Uniqueness** — could a meaningfully different implementation satisfy this same criteria set? If yes, the spec is under-determined — tighten it

A PRD that passes all three gates is one an engineer (or an AI reviewer) can't rubber-stamp without either pointing to an unmet criterion, or having no objection left to make.

---

## Success Metrics
| Metric | Current | Target | Timeframe | Tool |
|--------|---------|--------|-----------|------|
| | | | | |

**Guardrails (must not worsen):**
- 

---

## Assumptions
| Assumption | Risk Level | Validation Method |
|-----------|-----------|------------------|
| | | |

---

## Technical Considerations
- **Dependencies:**
- **Data/Events needed:**
- **Known risks:**

---

## Phasing
| Phase | Scope | Launch Criteria | ETA |
|-------|-------|----------------|-----|
| MVP | | | |

---

## Launch Plan
- **Release type:**
- **Rollout:**
- **Customer comms:**
- **Rollback plan:**

---

## Open Questions
| Question | Owner | Due |
|---------|-------|-----|
| | | |

---

## Decision Log
| Date | Decision | Rationale |
|------|---------|-----------|
| | | |

---

## Sub-Agent Review Checklist
- [ ] **Engineering review:** Feasibility, complexity, hidden dependencies
- [ ] **Design review:** UX quality, design system alignment, user flow gaps
- [ ] **Data review:** Instrumentation plan, metric validity
- [ ] **Exec review:** Strategic alignment, business impact, board-readiness
- [ ] **User Research review:** Evidence quality, assumption risk
- [ ] **Legal/Privacy review:** Data handling, compliance, regulatory flags
- [ ] **Competitive review:** Positioning impact, differentiation, market timing

---

## Review Process
When this PRD is ready for review:
1. Set Status to **In Review**
2. Run `/review-prd` — triggers all sub-agents in parallel
3. Address top feedback items and update this document
4. Log key decisions in the Decision Log above
5. Set Status to **Approved** when consensus is reached

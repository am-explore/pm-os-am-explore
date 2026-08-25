---
applyTo: "context-library/**"
---

# PM OS Context Library

Files in this directory contain the PM's product-specific knowledge. These are the highest-leverage files in the system — the better the context, the smarter the AI partner.

When working with any context-library file:
- Treat the content as ground truth for this product
- Reference specific data points when making recommendations
- Flag when context seems outdated and suggest updates
- Never contradict information in these files without stating the conflict

## Files

- `company.md` — Business model, mission, revenue, stage
- `product.md` — Product overview, current state, tech stack
- `users.md` — User personas, segments, JTBD, pain points
- `competitors.md` — Competitive landscape, positioning
- `team.md` — Team structure, stakeholders
- `metrics.md` — North Star metric, OKRs, KPIs

# Routine: Competitive Pulse
> Weekly scan of competitive landscape for new signals, launches, and positioning shifts.

---

## Configuration

```yaml
trigger: schedule
schedule: "0 9 * * 1"  # Every Monday at 9am
context_sources:
  - context-library/competitors.md
  - context-library/product.md
  - context-library/company.md
output: competitive-brief
enforcement: advisory
```

---

## Claude Code Setup
```
/schedule weekly competitive pulse every Monday at 9am
```

## Copilot Cloud Agent Setup
Create `.github/workflows/routine-competitive-pulse.yml`:
```yaml
name: Competitive Pulse
on:
  schedule:
    - cron: '0 9 * * 1'
  workflow_dispatch:
```

---

## Prompt

You are running the Competitive Pulse routine for PM OS.

**Your task:** Scan for competitive signals and produce a brief for the product team.

### Steps:
1. Read `context-library/competitors.md` for the current competitive landscape
2. For each tracked competitor, search for:
   - New feature launches or product announcements
   - Pricing changes
   - Funding, M&A, or partnership news
   - Hiring patterns that signal strategic direction
   - Customer reviews or sentiment shifts (G2, Product Hunt, Twitter/X)
3. Assess: does any signal change our competitive positioning?
4. Recommend: should we adjust strategy, accelerate a feature, or investigate further?

### Output format:

```markdown
## Competitive Pulse — Week of [Date]

### Signal Summary
| Competitor | Signal | Source | Impact Assessment |
|-----------|--------|--------|-------------------|
| | | | 🟢 Low / 🟡 Medium / 🔴 High |

### Top Signal This Week
**[Competitor]:** [What happened]
- **What it means for us:** [Analysis]
- **Recommended response:** [Action or no action, and why]

### Positioning Check
- Our positioning remains [strong/vulnerable] because: [reason]
- Biggest gap to address: [gap]

### Watchlist Updates
[Any competitors to add, remove, or re-prioritize in tracking]
```

---

## Quality Checks
- [ ] All tracked competitors from `competitors.md` are covered
- [ ] Signals are sourced (not fabricated) — includes source attribution
- [ ] Impact assessment is specific to our product, not generic
- [ ] At least one actionable recommendation (even if "no action needed")
- [ ] Positioning check references our actual competitive moat from `company.md`

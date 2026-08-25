# Routine: User Feedback Synthesis
> Weekly aggregation of user signals — support tickets, NPS, reviews, feature requests — into actionable insights.

---

## Configuration

```yaml
trigger: schedule
schedule: "0 10 * * 3"  # Every Wednesday at 10am
context_sources:
  - context-library/users.md
  - context-library/product.md
  - context-library/metrics.md
output: feedback-report
enforcement: advisory
```

---

## Claude Code Setup
```
/schedule weekly user feedback synthesis every Wednesday at 10am
```

## Copilot Cloud Agent Setup
Create `.github/workflows/routine-feedback-synthesis.yml`:
```yaml
name: User Feedback Synthesis
on:
  schedule:
    - cron: '0 10 * * 3'
  workflow_dispatch:
```

---

## Prompt

You are running the User Feedback Synthesis routine for PM OS.

**Your task:** Aggregate and analyze user feedback from the past week into a structured report.

### Steps:
1. Read `context-library/users.md` for known personas, JTBD, and pain points
2. Collect feedback signals from connected sources:
   - Support tickets (via MCP: Zendesk, Intercom, etc.)
   - NPS/CSAT responses
   - App store reviews
   - Feature requests (via MCP: Linear, Jira, Productboard, etc.)
   - Social mentions and community discussions
3. Categorize feedback by:
   - Persona segment (from `users.md`)
   - Feedback type (bug, feature request, praise, confusion, churn signal)
   - Product area
4. Identify emerging themes vs. known issues
5. Flag any feedback that challenges current assumptions in `users.md`

### Output format:

```markdown
## User Feedback Synthesis — Week of [Date]

### Volume Summary
| Source | This Week | Last Week | Trend |
|--------|-----------|-----------|-------|
| Support tickets | | | ↑/↓/→ |
| Feature requests | | | |
| NPS responses | | | |
| Reviews | | | |

### Top 3 Themes This Week
1. **[Theme]** ([count] mentions)
   - Representative quote: "[verbatim user quote]"
   - Affected persona: [persona from users.md]
   - Product area: [area]
   - New or recurring: [new/recurring — Nth week]

2. **[Theme]** ([count] mentions)
   - Representative quote: "[verbatim user quote]"
   - Affected persona: [persona]
   - Product area: [area]
   - New or recurring: [new/recurring]

3. **[Theme]** ([count] mentions)
   - Representative quote: "[verbatim user quote]"
   - Affected persona: [persona]
   - Product area: [area]
   - New or recurring: [new/recurring]

### Churn Signals
| Signal | User Segment | Severity | Recommended Action |
|--------|-------------|----------|-------------------|
| | | 🟡/🔴 | |

### Assumption Challenges
[Any feedback that contradicts current assumptions in users.md]
- **Current assumption:** [what we believe]
- **Contradicting signal:** [what users are saying]
- **Recommended action:** [investigate / update assumption / design experiment]

### Bright Spots
[Positive feedback worth amplifying — features users love, aha moments]

### Recommended Actions
1. [Action]: [why, based on what feedback]
2. [Action]: [why, based on what feedback]
```

---

## Quality Checks
- [ ] Themes are categorized by persona from `users.md`, not generic segments
- [ ] At least one verbatim user quote per theme (not paraphrased)
- [ ] "New or recurring" flag helps distinguish emerging issues from known ones
- [ ] Churn signals section is present even if empty (with "none detected" note)
- [ ] Assumption challenges reference specific entries in `users.md`
- [ ] Bright spots included — not just problems

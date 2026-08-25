# Routine: Sprint Retro Prep
> Pre-retro analysis that surfaces data-driven insights so the team discusses what matters, not just what's top of mind.

---

## Configuration

```yaml
trigger: schedule
schedule: "0 9 * * 5/14"  # Every other Friday at 9am (adjust to sprint cadence)
context_sources:
  - context-library/product.md
  - context-library/metrics.md
  - context-library/team.md
output: retro-document
enforcement: advisory
```

---

## Claude Code Setup
```
/schedule sprint retro prep bi-weekly on Fridays at 9am
```

## Copilot Cloud Agent Setup
Create `.github/workflows/routine-sprint-retro.yml`:
```yaml
name: Sprint Retro Prep
on:
  schedule:
    - cron: '0 9 */14 * *'  # Adjust to match sprint cadence
  workflow_dispatch:
```

---

## Prompt

You are running the Sprint Retro Prep routine for PM OS.

**Your task:** Prepare a data-grounded sprint retrospective document.

### Steps:
1. Analyze the sprint's commits, PRs merged, and issues closed
2. Read `context-library/metrics.md` — did sprint work move key metrics?
3. Read `context-library/product.md` — compare what was planned vs. delivered
4. Identify velocity patterns: scope changes, carry-overs, blockers
5. Surface team dynamics signals from PR review cycles and collaboration patterns

### Output format:

```markdown
## Sprint Retro Prep — Sprint [N] ([Date Range])

### Sprint Scorecard
| Dimension | Score | Notes |
|-----------|-------|-------|
| Delivery vs. Plan | [%] | [what shipped vs. committed] |
| Metric Impact | [↑/↓/→] | [which metrics moved] |
| Scope Stability | [stable/shifted] | [scope changes during sprint] |
| Team Health Signals | [🟢/🟡/🔴] | [review cycles, blockers, collaboration] |

### What Went Well (data-backed)
1. [Achievement]: [evidence — e.g., "shipped 2 days early, PR cycle avg was 4hrs"]
2. [Achievement]: [evidence]

### What Didn't Go Well (data-backed)
1. [Issue]: [evidence — e.g., "3 scope changes mid-sprint, 2 carry-overs"]
2. [Issue]: [evidence]

### Patterns Worth Discussing
- [Pattern from this sprint + comparison to previous sprints]
- [Recurring theme that's appearing for the 2nd+ time]

### Suggested Discussion Topics
1. [Topic]: [Why it matters + data point]
2. [Topic]: [Why it matters + data point]
3. [Topic]: [Why it matters + data point]

### Previous Action Items Check
| Action Item | Status | Evidence |
|------------|--------|---------|
| [from last retro] | ✅/❌/🔄 | [what happened] |
```

---

## Quality Checks
- [ ] Scorecard dimensions are filled with actual data, not placeholders
- [ ] "Went well" and "didn't go well" sections have evidence, not opinions
- [ ] Patterns reference previous sprints for comparison (not just this sprint)
- [ ] Discussion topics are framed as questions, not accusations
- [ ] Previous retro action items are tracked for accountability

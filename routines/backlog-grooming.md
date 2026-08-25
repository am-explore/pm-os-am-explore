# Routine: Backlog Grooming
> Nightly triage of new issues — label, assign, prioritize, and surface what needs PM attention.

---

## Configuration

```yaml
trigger: schedule
schedule: "0 22 * * 1-5"  # Weeknights at 10pm
context_sources:
  - context-library/product.md
  - context-library/team.md
  - context-library/metrics.md
output: groomed-queue  # Updated issue tracker + summary
enforcement: advisory
```

---

## Claude Code Setup
```
/schedule nightly backlog grooming weeknights at 10pm
```

## Copilot Cloud Agent Setup
Create `.github/workflows/routine-backlog-grooming.yml`:
```yaml
name: Backlog Grooming
on:
  schedule:
    - cron: '0 22 * * 1-5'
  workflow_dispatch:
```

---

## Prompt

You are running the Backlog Grooming routine for PM OS.

**Your task:** Triage all new/ungroomed issues since the last run.

### Steps:
1. Read `context-library/product.md` for current product priorities and roadmap themes
2. Read `context-library/team.md` for team structure and ownership areas
3. For each ungroomed issue:
   - Apply labels based on area (feature, bug, tech-debt, research, ops)
   - Assign to the correct owner based on code area from `team.md`
   - Estimate priority using RICE or impact/effort against current OKRs
   - Add a brief PM note explaining the prioritization rationale
4. Surface issues that need PM decision (ambiguous scope, cross-team, strategic)

### Output format:

```markdown
## Backlog Grooming Summary — [Date]

### Issues Triaged: [count]

### Auto-Assigned
| Issue | Label | Owner | Priority | Rationale |
|-------|-------|-------|----------|-----------|
| | | | | |

### Needs PM Decision
| Issue | Why It Needs Attention | Recommended Action |
|-------|----------------------|-------------------|
| | | |

### Patterns Noticed
- [Any recurring themes: e.g., "3 bugs in auth module this week — may need deeper investigation"]

### Queue Health
- **Open bugs:** [count] (was [last week])
- **Unassigned items:** [count]
- **Oldest untouched:** [issue] ([days] days)
```

---

## Quality Checks
- [ ] Every new issue has a label and owner
- [ ] Priority rationale references current OKRs or product themes
- [ ] "Needs PM Decision" items have clear context — not just "unclear"
- [ ] Patterns section identifies at least one trend (or explicitly states "no patterns")
- [ ] Queue health metrics are included for tracking backlog trajectory

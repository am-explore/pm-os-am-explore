# Routine: Weekly Metrics Digest
> Automated weekly summary of key product metrics for stakeholders.

---

## Configuration

```yaml
trigger: schedule
schedule: "0 8 * * 1"  # Every Monday at 8am
context_sources:
  - context-library/metrics.md
  - context-library/product.md
  - context-library/company.md
output: stakeholder-summary  # Slack, email, or document
enforcement: advisory
```

---

## Claude Code Setup
```
/schedule weekly metrics digest every Monday at 8am
```

## Copilot Cloud Agent Setup
Create `.github/workflows/routine-metrics-digest.yml`:
```yaml
name: Weekly Metrics Digest
on:
  schedule:
    - cron: '0 8 * * 1'
  workflow_dispatch:
```

---

## Prompt

You are running the Weekly Metrics Digest routine for PM OS.

**Your task:** Generate a concise, exec-ready metrics summary for the past week.

### Steps:
1. Read `context-library/metrics.md` for current North Star metric, OKRs, and KPIs
2. Compare current values to targets and previous period
3. Identify the top 3 movers (biggest changes, positive or negative)
4. For each mover, provide a 1-sentence hypothesis on why it moved
5. Flag any metric that is off-track with a recommended investigation

### Output format:

```markdown
## Weekly Metrics Digest — [Date Range]

### North Star: [Metric Name]
- **Current:** [value] | **Target:** [value] | **Trend:** [↑/↓/→]

### Top 3 Movers This Week
1. **[Metric]:** [change] — [hypothesis]
2. **[Metric]:** [change] — [hypothesis]
3. **[Metric]:** [change] — [hypothesis]

### Off-Track Alerts
| Metric | Current | Target | Gap | Recommended Action |
|--------|---------|--------|-----|-------------------|
| | | | | |

### Key Takeaway
[One sentence: what should leadership know this week?]
```

---

## Quality Checks
- [ ] North Star metric is included with trend direction
- [ ] At least 3 movers identified with hypotheses (not just numbers)
- [ ] Off-track metrics flagged with specific recommended actions
- [ ] Summary is under 1 page — exec-scannable
- [ ] No generic statements — everything references actual product context

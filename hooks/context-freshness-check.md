# Hook: Context Freshness Check
> Flags context-library files that are overdue for review based on their recommended cadence.

---

## Configuration

```yaml
trigger: session-start | on-demand
enforcement: advisory  # Change to "blocking" to require context updates before proceeding
applies_to: context-library/*.md
```

### Claude Code (optional wiring)
To fire this check automatically at session start in Claude Code, add a `SessionStart` hook in `.claude/settings.json`:
```json
{
  "hooks": {
    "SessionStart": [
      {
        "type": "command",
        "command": "echo 'Context freshness: review last-validated dates in context-library/ against hooks/context-freshness-check.md'"
      }
    ]
  }
}
```

### GitHub Copilot
Copilot does not support repo-local hook configs. Invoke this check manually at the start of a session:
```
Run the context freshness check (hooks/context-freshness-check.md) across all context-library files
```
Or run it as a scheduled GitHub Actions job that opens an issue when files go stale.

---

## Freshness Rules

Each context-library file has a recommended review cadence. The hook checks the `<!-- Last validated: DATE -->` header against these thresholds:

| File | Review Cadence | Warning Threshold | Critical Threshold |
|------|---------------|-------------------|-------------------|
| `metrics.md` | Weekly | 14 days | 30 days |
| `competitors.md` | Monthly | 45 days | 90 days |
| `users.md` | After research rounds | 60 days | 120 days |
| `product.md` | After major launches | 45 days | 90 days |
| `company.md` | Quarterly | 120 days | 180 days |
| `team.md` | On team changes | 60 days | 120 days |

### Status Definitions
- 🟢 **Fresh** — Within recommended cadence
- 🟡 **Warning** — Past recommended cadence but within warning threshold
- 🔴 **Stale** — Past warning threshold, likely outdated

---

## Quality Checks

For each context-library file:
- [ ] `<!-- Last validated: DATE -->` header is present
- [ ] `<!-- Confidence: high/medium/low -->` header is present
- [ ] Date is within the recommended review cadence
- [ ] Content is not still using placeholder `[FILL IN]` values
- [ ] No sections are completely empty

---

## Output Format

```markdown
## Context Freshness Report — [Date]

### Overall Status: 🟢 All Fresh / 🟡 Some Stale / 🔴 Critical Staleness

| File | Last Validated | Days Ago | Cadence | Status |
|------|---------------|----------|---------|--------|
| company.md | [date] | [N] | Quarterly | 🟢/🟡/🔴 |
| product.md | [date] | [N] | Post-launch | 🟢/🟡/🔴 |
| users.md | [date] | [N] | Post-research | 🟢/🟡/🔴 |
| competitors.md | [date] | [N] | Monthly | 🟢/🟡/🔴 |
| metrics.md | [date] | [N] | Weekly | 🟢/🟡/🔴 |
| team.md | [date] | [N] | On change | 🟢/🟡/🔴 |

### Files Needing Attention
1. **[file.md]** — Last validated [N days] ago (cadence: [X])
   - Likely stale sections: [specific sections]
   - Trigger: [what probably changed since last update]
   - Action: Review and update, then set `<!-- Last validated: [today] -->`

### Unfilled Templates
[Any context files still using [FILL IN] placeholders]
```

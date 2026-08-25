# Routine: [Name]
> [One-line description of what this routine does and who it serves]

---

## Configuration

```yaml
trigger: [schedule | api | github-event]
schedule: "[cron expression]"         # For schedule triggers — e.g., "0 9 * * 1" (Monday 9am)
event: "[pull_request.opened]"        # For GitHub event triggers
context_sources:
  - context-library/[file1].md
  - context-library/[file2].md
output: [where results go — Slack, document, PR, issue, etc.]
enforcement: advisory                 # advisory (default) | blocking
```

---

## Claude Code Setup
```
/schedule [natural language description and cadence]
```
Or create at [claude.ai/code/routines](https://claude.ai/code/routines) with:
- **Prompt:** Copy the Prompt section below
- **Repositories:** [your repo]
- **Trigger:** [schedule/API/GitHub event as configured above]
- **Connectors:** [list any MCP connectors the routine needs]

## Copilot Cloud Agent Setup
Create `.github/workflows/routine-[name].yml`:
```yaml
name: [Routine Name]
on:
  schedule:
    - cron: '[cron expression]'
  workflow_dispatch:                   # Allow manual triggers
```

---

## Prompt

You are running the [Name] routine for PM OS.

**Your task:** [Clear, specific description of what to produce]

### Steps:
1. Read [context source] for [what context]
2. [Analysis step]
3. [Synthesis step]
4. [Output step]

### Output format:

```markdown
## [Routine Name] — [Date/Range]

### [Section 1]
[Template for section content]

### [Section 2]
[Template for section content]

### Recommended Actions
1. [Action template]
2. [Action template]
```

---

## Quality Checks
- [ ] [Check that output includes required elements]
- [ ] [Check that analysis is specific to product context, not generic]
- [ ] [Check that recommendations are actionable, not vague]
- [ ] [Check that output is the right length for audience]
- [ ] [Check that sources are referenced, not fabricated]

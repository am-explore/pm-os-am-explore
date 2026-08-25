# PM Routines — Schedule-Ready PM Task Definitions
> Reusable PM task definitions. Wire them to a scheduler (Claude Code `/schedule`, GitHub Actions cron, or manual prompts) to make them run on their own.

---

## What Are Routines?

Routines are **markdown definitions** of recurring PM tasks — prompt + context sources + quality checks. Out of the box they do **not** run autonomously; they are structured templates ready to be wired to a scheduler or invoked on demand.

Each routine file defines:
- **What** to do (prompt + context sources)
- **When** to do it (suggested schedule — cron or natural language)
- **Where** to output (Slack, document, PR, issue, etc.)
- **How** to validate (quality checks before delivery)

You activate a routine by (a) running it manually in an AI session, (b) scheduling it with Claude Code `/schedule`, or (c) adding a matching GitHub Actions workflow.

---

## How Routines Work

### With Claude Code
Use `/schedule` in any Claude Code session to create a routine:
```
/schedule daily metrics digest at 8am
/schedule weekly competitive pulse on Mondays at 9am
```
Or create routines at [claude.ai/code/routines](https://claude.ai/code/routines).

### With GitHub Copilot / GitHub Actions
Copilot does not auto-execute routines from this repo. To make a routine recurring in a Copilot/GitHub environment, add a GitHub Actions workflow under `.github/workflows/` that runs on a cron schedule and invokes the routine's prompt (e.g., via an AI step, a Copilot cloud agent job, or a custom script). Each routine file below includes a starter workflow snippet you can copy.

If you want to organize per-routine Copilot cloud agent configs, create them under `.github/agents/` (this directory is not pre-created — add it if/when you wire a cloud agent).

### Manual Execution
Any routine can be run on-demand by referencing it in conversation:
```
Run the weekly-metrics-digest routine now
```

---

## Routine File Format

Each routine file follows this structure:

```yaml
# Routine: [Name]
# Trigger: [schedule | api | github-event]
# Schedule: [cron expression or natural language]
# Context sources: [which context-library files to read]
# Output: [where results go — Slack, document, PR, etc.]
# Enforcement: advisory (default) | blocking
```

Followed by the prompt and quality checks.

---

## Available Routines

| Routine | File | Suggested schedule | Output |
|---------|------|--------------------|--------|
| Weekly Metrics Digest | `weekly-metrics-digest.md` | Weekly (Monday 8am) | Stakeholder summary |
| Competitive Pulse | `competitive-pulse.md` | Weekly (Monday 9am) | Competitive brief |
| Backlog Grooming | `backlog-grooming.md` | Daily (weeknights) | Groomed issue queue |
| Stakeholder Update Draft | `stakeholder-update-draft.md` | Weekly (Friday 3pm) | Draft update |
| Sprint Retro Prep | `sprint-retro-prep.md` | Bi-weekly (sprint end) | Retro document |
| User Feedback Synthesis | `user-feedback-synthesis.md` | Weekly (Wednesday) | Feedback report |

---

## Creating Custom Routines

1. Copy `templates/routine-template.md` to `routines/`
2. Fill in the trigger, context sources, prompt, and quality checks
3. (Optional) For Claude Code auto-trigger: run `/schedule` referencing the routine file
4. (Optional) For GitHub-based scheduling: add a `.github/workflows/` cron workflow that invokes the routine

See `skills/automation/SKILL-routine-setup.md` for the full setup framework.

---

## Configuration

### Claude Code Setup
```bash
# In a Claude Code session:
/schedule create routines/weekly-metrics-digest.md
```

### Copilot Cloud Agent Setup
Create a matching workflow in `.github/workflows/`:
```yaml
name: Weekly Metrics Digest
on:
  schedule:
    - cron: '0 8 * * 1'  # Monday 8am UTC
  workflow_dispatch:       # Manual trigger
```

### MCP Connectors
Routines can use any connected MCP servers (Slack, Linear, Jira, etc.) to read inputs and deliver outputs. Configure connectors in `tools/example-mcp-config.json`.

---

## Best Practices

1. **Start small** — Begin with one routine, validate the output quality, then expand
2. **Review outputs** — Treat routine outputs as drafts until you trust the quality
3. **Tune prompts** — If outputs are generic, make the prompt more specific to your product context
4. **Scope connectors** — Only give routines access to the tools they need
5. **Set enforcement** — Use `advisory` (default) for suggestions, switch to `blocking` when the routine must meet quality gates before delivery

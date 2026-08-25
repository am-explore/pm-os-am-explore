# PM Hooks — Quality Gates for Product Artifacts
> Automated checks that run at key points in the PM workflow to catch issues before they compound.

---

## What Are Hooks?

Hooks are automated quality checks that run when PM artifacts are created or modified. They act as guardrails — catching missing elements, inconsistencies, and quality issues early.

**Default enforcement: advisory** — hooks surface issues as suggestions. You can switch any hook to `blocking` to require fixes before proceeding.

---

## How Hooks Work

Out of the box, hooks are **markdown check definitions** — structured checklists + output formats. They are not wired to fire automatically until you configure a trigger. The most reliable way to use them is manual invocation; optional wiring is available for Claude Code and GitHub Actions.

### Manual Invocation (works everywhere)
Run any hook check on demand in Claude Code, Copilot, or any AI session:
```
Run the PRD quality gate (hooks/prd-quality-gate.md) on the current PRD
Run the context freshness check (hooks/context-freshness-check.md) across all context files
Run the launch readiness check (hooks/launch-readiness.md) for [feature]
```

### Claude Code (optional auto-trigger)
Claude Code supports `.claude/settings.json` hooks that fire at lifecycle events:
- `PreToolUse` — Before a file is written (validate before save)
- `PostToolUse` — After a file is written (check what was produced)
- `SessionStart` — At the start of a session (useful for freshness checks)
- `SubagentStop` — When a subagent finishes

Each hook file below includes an example `settings.json` snippet you can copy in.

### GitHub Copilot
GitHub Copilot does not currently support repo-local hook config files. Use manual invocation, or enforce hooks in CI via GitHub Actions workflows (trigger on file changes to `prd/`, `launch-plans/`, or `context-library/`).

See the official [Copilot custom instructions docs](https://docs.github.com/en/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot) for the currently supported customization surface (`copilot-instructions.md` + path-specific instructions).

---

## Available Hooks

| Hook | File | Trigger | Enforcement |
|------|------|---------|-------------|
| PRD Quality Gate | `prd-quality-gate.md` | After PRD creation/edit | advisory (default) |
| Context Freshness | `context-freshness-check.md` | Session start / on demand | advisory (default) |
| Launch Readiness | `launch-readiness.md` | Before launch plan finalization | advisory (default) |

---

## Enforcement Modes

Each hook has an `enforcement` field:

| Mode | Behavior |
|------|----------|
| `advisory` (default) | Surfaces issues as suggestions. The PM sees the warnings but can proceed. |
| `blocking` | Requires all checks to pass before the artifact is considered complete. |

To change enforcement, edit the hook's `enforcement` field:
```yaml
enforcement: blocking  # Change from advisory to blocking
```

---

## Creating Custom Hooks

1. Create a new markdown file in `hooks/`
2. Define the trigger, checks, and enforcement mode
3. (Optional) For Claude Code auto-trigger: reference the hook in `.claude/settings.json`
4. (Optional) For CI enforcement with Copilot or any team: add a GitHub Actions workflow that runs the check on relevant file changes

### Hook File Structure

```yaml
# Hook: [Name]
# Trigger: [when this hook fires]
# Enforcement: advisory | blocking
# Applies to: [what artifact types]
```

Followed by the check criteria and output format.

---

## Best Practices

1. **Start advisory** — Get comfortable with hook outputs before switching to blocking
2. **Fix the checks, not the hook** — If a hook keeps flagging false positives, refine its criteria
3. **Less is more** — A few high-signal hooks beat many noisy ones
4. **Chain hooks** — PRD quality gate → context freshness → launch readiness
5. **Review monthly** — Remove hooks that aren't catching real issues

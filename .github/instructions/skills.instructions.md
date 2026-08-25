---
applyTo: "skills/**"
---

# PM OS Skills

Files in this directory are PM frameworks that activate based on conversation triggers.

Each skill file follows the format:
- **Auto-activates when:** keywords appear in the conversation
- **Force load:** via a slash command (e.g., `/write-prd`)

Skills are NOT auto-loaded. Read the specific skill file referenced in `CLAUDE.md` when the conversation matches a trigger keyword.

## Skill Categories

- `skills/discovery/` — Research, opportunity mapping, user interviews
- `skills/strategy/` — Product strategy, positioning, vision
- `skills/execution/` — PRD writing, roadmapping, stakeholder communication
- `skills/growth/` — North Star metrics, PLG strategy, launch planning
- `skills/research/` — Competitive research and battlecards
- `skills/design/` — Product design review and UX evaluation

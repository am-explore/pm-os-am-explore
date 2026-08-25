# Tools & Integrations
> Extend PM OS by connecting external tools, adding custom skills, or bringing in live data.

PM OS is designed to be self-contained out of the box — but it becomes significantly more powerful when connected to your actual tools and data sources.

---

## 1. MCP Servers (AI ↔ Tool Integration)

**What:** Model Context Protocol (MCP) servers let your AI partner read from and write to external tools directly — Jira tickets, Figma designs, analytics dashboards, Notion docs, and more.

**Works with:** Claude Code, GitHub Copilot (VS Code Agent Mode)

### How to Set Up

**Claude Code:** Create a `.mcp.json` file in your project root. Claude Code discovers this file automatically. See `example-mcp-config.json` in this directory for a starter config.

**GitHub Copilot (VS Code):** Configure MCP servers in your VS Code settings or create a `.vscode/mcp.json` file. See the [Copilot MCP documentation](https://code.visualstudio.com/docs/copilot/chat/mcp-servers) for setup details.

### Recommended MCP Servers for PMs

| Tool | What It Enables | MCP Server |
|------|----------------|------------|
| **Jira / Linear** | Read/create tickets, check sprint status, update priorities | `@anthropic/jira-mcp`, `linear-mcp` |
| **Notion** | Read docs, update wikis, pull meeting notes | `@anthropic/notion-mcp` |
| **Figma** | Review designs, extract specs, check component usage | `figma-mcp` |
| **Mixpanel / Amplitude** | Query analytics, pull funnel data, check experiment results | `analytics-mcp` |
| **PostHog** | Feature flags, session replays, event queries | `posthog-mcp` |
| **GitHub** | PRs, issues, repo management | `@anthropic/github-mcp` |
| **Slack** | Read channels, search conversations, post updates | `@anthropic/slack-mcp` |
| **Google Sheets** | Pull data, update trackers | `google-sheets-mcp` |

> **Note:** MCP server names and availability change frequently. Check the [MCP server registry](https://github.com/modelcontextprotocol/servers) for the latest.

### Example Usage
Once configured, you can say things like:
- *"Pull the latest sprint velocity from Jira and update our roadmap confidence levels"*
- *"Check Mixpanel for this week's activation rate and update context-library/metrics.md"*
- *"Review the latest Figma mockup for the onboarding redesign"*

---

## 2. Custom Skills (Extend PM OS)

**What:** Add your own frameworks, workflows, or domain-specific knowledge by creating skill files that follow the PM OS pattern.

### How to Add a Custom Skill

1. Copy `custom-skill-template.md` from this directory
2. Rename it to `SKILL-<your-skill-name>.md`
3. Place it in the appropriate `skills/` subdirectory:
   - `skills/discovery/` — Research and insight generation
   - `skills/strategy/` — Strategic planning and positioning
   - `skills/execution/` — Building and shipping
   - `skills/growth/` — Growth, retention, and monetization
   - `skills/research/` — Market and competitive research
   - `skills/design/` — UX and design review
4. Add an activation trigger in `CLAUDE.md` under "Skill Activation":
   ```markdown
   | "your-keyword" | `skills/category/SKILL-your-skill-name.md` |
   ```
5. **Claude Code only:** Create a router file at `.claude/skills/<skill-name>/SKILL.md` with YAML frontmatter (`name`, `description`) that tells Claude to read your full framework file. This makes the skill discoverable via `/skill-name` in Claude Code. See existing skills in `.claude/skills/` for examples.

### Skill Ideas for Different PM Specializations

| Specialization | Skill Idea | Trigger Keywords |
|---------------|-----------|-----------------|
| B2B / Enterprise | Account-based product strategy | "enterprise", "account", "deal" |
| Marketplace | Supply/demand balancing | "marketplace", "supply", "liquidity" |
| Platform | API strategy and developer experience | "platform", "API", "developer" |
| AI/ML Products | Model evaluation and AI ethics | "model", "AI", "fairness" |
| Customer Success | Churn prediction and intervention | "churn", "retention", "health score" |
| Payments/Fintech | Compliance and transaction design | "payment", "compliance", "KYC" |

---

## 3. External Data Sources

**What:** Bring live data into your PM OS context for richer, more grounded recommendations.

### Pattern A: Manual Data Snapshots (Simplest)
Copy-paste key metrics into your context-library files:
- Weekly: Update `context-library/metrics.md` with fresh numbers
- Monthly: Update `context-library/competitors.md` with competitive intel
- After research: Update `context-library/users.md` with new insights

### Pattern B: Automated via MCP (Most Powerful)
Use MCP servers to let your AI partner pull live data:
- *"Pull this week's AARRR funnel from Mixpanel and update my metrics context"*
- *"Check G2 for new reviews of [competitor] and summarize sentiment changes"*

### Pattern C: File-Based Context (For Offline/Secure Data)
Drop data exports into a `data/` directory:
```
data/
├── analytics-export-2026-04.csv
├── user-research-synthesis.md
└── competitive-pricing-analysis.xlsx
```
Then reference them: *"Analyze the data in data/analytics-export-2026-04.csv and identify our biggest activation bottleneck."*

---

## Tips

- **Start simple.** Fill in the context-library manually first. Add MCP servers when you feel the friction of manual updates.
- **One tool at a time.** Don't configure 5 MCP servers on day one. Start with your analytics tool, then add Jira/Linear.
- **Custom skills compound.** A custom skill you use once a week saves more time than an MCP server you use once a month.

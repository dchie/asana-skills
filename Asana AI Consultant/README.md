# Asana AI Teammate Advisor

A Claude skill that reviews your Asana workspace and tells you exactly where AI Studio rules and AI Teammates can replace manual work.

Not a generic list of AI ideas. Actual recommendations with behavior instructions you can paste directly into Asana.

---

## What it does

Connect it to your Asana workspace (via MCP or paste your project structure), and it will:

- Analyze your projects, sections, triggers, and handoffs
- Check workflow readiness before recommending anything
- Route each opportunity to the right tool: AI Teammate, AI Studio rule, Claude Code agent, or hybrid
- Output a prioritized build plan with copy-paste behavior instructions, key resources to attach, access requirements, and a test case for each recommendation
- Tell you what **not** to build yet (and why)

---

## Sample output structure

```
## AI Teammate Recommendation Report

### Summary
[What the workflow does, where the leverage is, what to skip for now]

### Readiness Notes
- [blockers or green lights]

### Tier 1 — Build First
[Full specs with behavior instructions, triggers, access requirements]

### Tier 2 — Build Next
### Tier 3 — Build Later
### AI Studio Workflows / Rules
### Do Not Build Yet
```

---

## How to use it

### Option 1 — With Asana MCP (best)
Connect the [Asana MCP server](https://developers.asana.com/docs/using-asanas-mcp-server) to Claude. The skill will read your live workspace directly.

### Option 2 — Paste your structure
Export or describe your project structure, sections, task types, and team workflow. The skill works from that.

### Option 3 — Describe your workflow
Even a rough paragraph about what your team does daily is enough to get useful recommendations.

---

## Installation

### In Claude.ai (Projects)

1. Create a new Project in Claude
2. Upload `SKILL.md` and the `references/` folder as Project knowledge
3. Start a conversation and say: *"Review my Asana workspace and recommend where AI Teammates and AI Studio rules can save time"*

### As a Claude Code skill

Drop the folder into your skills directory:

```
your-skills/
  asana-ai-teammate-advisor/
    SKILL.md
    references/
      asana-ai-capabilities.md
      industry-playbooks.md
      teammate-spec-format.md
```

---

## File structure

```
asana-ai-teammate-advisor/
  SKILL.md                              # Main skill instructions
  references/
    asana-ai-capabilities.md           # What Teammates can and can't do today
    industry-playbooks.md              # Pre-built patterns by team type
    teammate-spec-format.md            # Output format for each recommendation
  README.md
```

---

## Requirements

- Claude (any tier — works in claude.ai Projects or via API)
- Asana workspace (MCP connection optional but recommended)
- AI Studio Pro if you plan to build AI Teammates (required by Asana for Teammate access)

---

## Built by

[David Chie](https://www.linkedin.com/in/davidchie/) — Founder of [Maple Drive](https://mapledrive.com) and Palo Alto Talent.

Built to solve a real problem: every Asana-heavy team I work with is staring at AI Studio wondering where to start. This gives them a straight answer.

---

## Contributing

PRs welcome. If you add a new industry playbook or find a capability that's changed, open a PR with a note on what you verified and when.

The capabilities reference (`references/asana-ai-capabilities.md`) needs periodic updates as Asana ships. Last verified: March 2026.

---

## License

MIT

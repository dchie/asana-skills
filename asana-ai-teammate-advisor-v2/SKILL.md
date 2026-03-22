---
name: asana-ai-teammate-advisor-v2
description: >
  Reviews an Asana workspace, project, or workflow description and recommends
  the right mix of AI Teammates, AI Studio workflows, lightweight process fixes,
  and external agents. Use this skill when the user mentions Asana, AI
  Teammates, AI Studio, workflow automation, or asks what to automate inside an
  Asana-driven team. Produces a prioritized recommendation report with real
  Asana setup guidance: scope, access, behavior instructions, key resources,
  starter tasks, trigger configuration, and validation steps.
---

# Asana AI Teammate Advisor v2

Review an Asana workspace, project, or workflow and recommend the smallest set
of builds that will save real time without promising product magic.

Default posture:
- Prefer 1 to 3 high-confidence recommendations over a long automation wishlist.
- Route work to the simplest tool that can actually do it.
- Treat Asana's current product limits as hard constraints.
- When the workspace is messy, recommend cleanup before AI.

---

## Inputs

Use the best available input in this order:

1. **Live Asana access** — best. Read representative teams, projects, sections, tasks, and comments.
2. **Project export / screenshots** — good. Reconstruct the workflow from structure, owners, sections, and sample tasks.
3. **Workflow description** — acceptable. Use a rough description when nothing else is available.

Trigger phrases include:
- "review my Asana"
- "suggest AI Teammates"
- "what should I automate"
- "how can AI help my team"
- "build AI Teammates for this workflow"

---

## Step 1 — Gather enough context

If live Asana access is available, inspect:
- 1 to 3 representative teams
- 2 to 4 representative projects
- project sections, custom fields, recurring tasks, and recent task/comment history
- whether the work is public-to-domain or private
- whether useful docs already exist (playbooks, templates, SOPs, briefs, examples)
- whether AI Studio workflows or rules already exist

If live access is not available, ask only for the missing minimum:
1. What does the team do?
2. What are the most common project or task types?
3. What work is repetitive, delayed, or always done late?
4. What docs or templates does the team already use?
5. Is the relevant work mostly public in Asana or private/restricted?

Do not skip context gathering. Generic AI recommendations are low value.

---

## Step 2 — Check readiness before recommending AI

Before you recommend a build, assess:

**Workflow repeatability**
- Does the same type of work happen often enough to justify setup?

**Context quality**
- Is the necessary context already in Asana tasks/projects/comments or in connected files?

**Knowledge assets**
- Are there templates, SOPs, examples, or style guides a Teammate can use?

**Access model**
- Will the Teammate actually be able to see the private projects/tasks/files it needs?

**Operational hygiene**
- Are owners, sections, due dates, and custom fields disciplined enough for automation to latch onto?

Flag these as blockers or warnings:
- no clear trigger
- no stable output format
- no reusable source documents
- heavily private workflow with unclear access ownership
- work is really one-off expert judgment, not repeatable collaboration
- the team wants bulk back-office changes that Asana Teammates cannot do

If readiness is poor, recommend:
- a process fix
- a template or checklist
- an AI Studio workflow/rule
- or "not yet"

Do not force a Teammate recommendation.

---

## Step 3 — Route each opportunity to the right tool

### Recommend an Asana AI Teammate when most of these are true:
- The work is collaborative and visible work-in-progress matters.
- Multiple people benefit from seeing the output in the task or project.
- The output is a draft, brief, summary, checklist, status synthesis, risk review, or recommendation.
- The main inputs live in Asana or in connected files the acting user can access.
- A human will review, approve, or iterate on the output.
- The work is triggered by assignment, @mention, recurring task, section/state change, custom field change, or a handoff task created in Asana.

Best-fit patterns:
- intake task -> structured brief
- recurring task -> weekly update or digest
- stage change -> prep pack or review notes
- closeout task -> debrief or lessons learned
- bug/spec/review task -> gap analysis or triage summary

### Recommend an AI Studio workflow or rule when:
- The logic is mostly routing, tagging, assigning, reminding, or field updates.
- The workflow can be described as clear "when / then" logic.
- The team needs high-volume consistency more than collaborative reasoning.

Best-fit patterns:
- assign by category
- move when field changes
- remind when overdue
- create a follow-up task on a predictable event

### Recommend a Claude Code agent when:
- The workflow needs live web research, external APIs, CRM/database writes, or scheduled processing outside Asana.
- The team needs system-to-system sync.
- The volume or complexity makes Asana-native interaction the wrong execution surface.

Best-fit patterns:
- web research pipelines
- CRM sync
- external database checks
- market monitoring
- scheduled enrichment jobs

### Recommend a Hybrid when:
- External intelligence must be gathered outside Asana, but the team should review and act in Asana.
- The right pattern is: agent gathers/processes -> pushes a task, comment, or linked file into Asana -> Teammate or human collaborates from there.

### Recommend a human/process fix first when:
- The workspace has no consistent structure.
- The work is too ambiguous for repeatable automation.
- Permissions or source documents are missing.
- A plain project template would solve 80 percent of the problem.

---

## Step 4 — Write the recommendations

Use the format in `references/teammate-spec-format.md`.

Prioritize by:
1. **Impact** — revenue protected, work shipped faster, client risk reduced, or high-friction internal coordination removed
2. **Frequency** — how often the workflow runs
3. **Readiness** — whether access, docs, and structure already exist
4. **Complexity** — faster wins first

Group recommendations into:
- **Tier 1 — Build first**
- **Tier 2 — Build next**
- **Tier 3 — Build later**

Default to a short list. More than 3 Teammate builds in one report usually means you are hand-waving.

---

## Step 5 — Deliver the report

Use this structure:

```md
## AI Teammate Recommendation Report
### Workspace / Project: [name]
### Analyzed: [date]

### Summary
[2 to 4 sentences: what the workflow is, where the leverage is, what not to build yet]

### Readiness Notes
- [key blocker or green light]
- [key blocker or green light]

### Recommendations

#### Tier 1 — Build First
[specs]

#### Tier 2 — Build Next
[specs]

#### Tier 3 — Build Later
[specs]

### AI Studio Workflows / Rules
[quick wins]

### External Agents / Hybrids
[only when needed]

### Do Not Build Yet
- [ideas that sound clever but are a bad fit today]

### Build Order Rationale
[short paragraph]
```

---

## Output standards

Every recommendation must include:
- the right tool choice, with a short reason
- exact scope and access requirements
- behavior instructions that can be pasted into Asana
- specific key resources to attach
- a real starter task or trigger
- a human review boundary
- a concrete test case
- a specific expected impact

Never produce:
- a generic list of AI ideas
- a Teammate recommendation that actually needs web/API/database access
- a build that depends on capabilities Asana does not support today
- a giant "master Teammate" that is supposed to run an entire team
- advice that ignores permissions, sharing, or setup effort

When uncertain, say so and choose the simpler recommendation.

---

## Reference files

- `references/asana-ai-capabilities.md` — current capability and limit model; treat this as the default truth
- `references/teammate-spec-format.md` — required output format
- `references/industry-playbooks.md` — starting patterns by team type

Read the capability reference before producing any build recommendation.

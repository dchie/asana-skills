---
name: asana-ai-teammate-spec-format
description: >
  Required output format for every AI Teammate, AI Studio rule, hybrid, and
  Claude Code agent recommendation. Every spec must include tool justification,
  access requirements, behavior instructions, key resources, human review
  boundary, test case, and expected impact.
---

---
name: asana-ai-teammate-spec-format
description: >
  Required output format for every AI Teammate recommendation. Covers the
  full spec template for AI Teammates, AI Studio workflow rules, hybrid
  builds, and Claude Code agents. Every recommendation must follow this
  structure before it is ready to ship. Includes a quality checklist to
  verify completeness.
---

# Teammate Spec Format

Every recommendation should read like something an operator can actually build in
Asana today. Do not hide the operational details behind one giant prompt.

---

## AI Teammate template

```md
### [NUMBER] — [TEAMMATE NAME]
**Team:** [which team this serves]
**Tool:** Asana AI Teammate
**Priority:** Tier 1 / 2 / 3
**Why this tool:** [why a Teammate is the right fit instead of a rule, process fix, or external agent]

**What it does**
[1 to 2 sentences. What recurring collaborative work does this remove or accelerate?]

**Trigger / Starter task**
[Exact trigger or first task to assign. Be specific.]

**Scope and access**
- Team to add it to: [team]
- Projects/tasks it must be able to see: [specific scope]
- Private access requirements: [what must be shared]
- Who should be allowed to use/manage it: [roles or users]
- Connected file tools needed: [Google Drive / SharePoint / OneDrive / none]

**Behavior instructions**
[Copy-paste-ready instructions for the Asana Behavior field. Include:
- role
- expected inputs
- exact output format
- tone
- constraints
- when to ask for clarification
- what not to do]

**Key resources**
- [specific docs, templates, examples, glossaries, or decision criteria]

**Human review boundary**
- [what a human must approve, verify, or send]

**Failure modes / watchouts**
- [what can go wrong]
- [when not to use this Teammate]

**Build steps**
1. [Exact setup steps in Asana]
2. ...

**Test case**
[Specific input, expected output, and how to judge pass/fail]

**Expected impact**
[Specific time saved, quality improvement, or risk reduction]
```

---

## AI Studio workflow / rule template

```md
### Rule / Workflow: [NAME]
**Tool:** AI Studio workflow / rule
**Trigger:** When [condition]
**Action:** Then [action]
**Why not a Teammate:** [pure routing / tagging / assignment / reminder / simple extraction]
**Setup:** [2 to 4 exact setup steps]
**Test case:** [how to verify it]
**Expected impact:** [specific]
```

---

## Hybrid template

```md
### Hybrid: [NAME]
**Tool:** Hybrid
**Why hybrid:** [what requires an external agent, and why the team should still collaborate in Asana]
**External agent job:** [research / sync / processing done outside Asana]
**Asana handoff point:** [task, comment, linked doc, or project]
**Teammate or human next step:** [what happens once the output lands in Asana]
**Dependencies:** [APIs, databases, web access, files]
**Trigger:** [cron, webhook, or manual]
**Test case:** [how to verify the full loop]
**Expected impact:** [specific]
```

---

## Claude Code agent template

```md
### Agent: [NAME]
**Tool:** Claude Code agent
**What it does:** [1 to 2 sentences]
**External dependencies:** [APIs, databases, web access, files]
**Output destination:** [Asana task, linked doc, database, CRM, etc.]
**Trigger:** [cron, webhook, manual]
**Estimated complexity:** Low / Medium / High
**Why not a Teammate:** [specific capability gap]
**Test case:** [how to verify it]
```

---

## Quality checklist

- [ ] Tool choice is justified
- [ ] Access and sharing requirements are explicit
- [ ] Behavior instructions are fully written
- [ ] Key resources are specific
- [ ] Trigger or starter task is concrete
- [ ] Human review boundary is stated
- [ ] Test case is real and specific
- [ ] Expected impact is specific

If any item is missing, the spec is not ready.

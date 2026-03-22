---
name: asana-ai-capabilities
description: >
  Capability and limitation reference for Asana AI Teammates. Read this before
  writing any build recommendation. Treats current Asana product limits as hard
  constraints. Last verified March 2026.
---

---
name: asana-ai-capabilities
description: >
  Capability and limit reference for Asana AI Teammates. Read this before
  writing any build recommendation. Covers what Teammates can and cannot do
  today, the access model, memory guidance, knowledge source limits, and a
  use-case capability table. Treat this as the default truth — if something
  is unclear, prefer conservative wording over hard claims.
---

# Asana AI Teammate Capabilities Reference

Use this file as the baseline capability model when recommending builds.
If something is unclear, prefer conservative wording and avoid hard claims that
go beyond current official Asana docs.

Last verified: March 21, 2026

---

## Current product status

- Asana AI Teammates are currently in beta and not yet generally available.
- Asana says AI Teammates are free to use while in beta.
- Availability and admin controls may vary by workspace or domain.
- Do not hard-gate recommendations on a specific paid tier unless the user has confirmed their current access and admin settings.

---

## What AI Teammates can do today

### Read and reason over work context
- Read tasks, projects, sections, comments, assignees, and existing custom field values they can access.
- Use project, portfolio, goal, and key-resource context when it is available to them.
- Synthesize information across related work they can access.
- Store memories from work they perform, while respecting the same task and project permissions.

### Work inside Asana
- Respond when assigned a task or @mentioned in a comment.
- Create tasks.
- Create subtasks on tasks they created.
- Edit task and subtask titles, descriptions, assignees, and due dates on work they are handling.
- Mark tasks complete.
- Add comments.
- Update existing custom field values.
- Add a task to a project, sometimes with approval depending on access.
- Add or remove task collaborators with approval.
- Assign tasks or subtasks to users, with approval when required by access.
- Delete tasks, with approval if they were not the creator.
- Create projects.
- Create or update sections.

### Work with external files
- Create external files through Google Drive, SharePoint, and OneDrive using the triggering user's authentication.
- Search external files, including documents, slides, sheets, images, and PDFs, when both the acting user and the Teammate have access.
- Create or edit linked Google Docs or Sheets when helpful for longer outputs.

### Strong use cases
- draft briefs
- review specs or bug reports
- summarize status and risks
- create prep packs and checklists
- synthesize recurring updates
- produce closeout or debrief documents

---

## What AI Teammates cannot do today

### External systems and live data
- They cannot browse the live web.
- They cannot call arbitrary external APIs.
- They cannot read from or write to external databases or CRMs directly.
- They cannot perform autonomous multi-system sync.

### Work Graph limits
- They cannot create custom fields.
- They cannot remove a task from a project.
- They cannot create dependencies.
- They cannot perform true bulk updates across large sets of tasks.
- They cannot create milestones or goals.
- They cannot create dashboards or charts.
- They cannot send messages or status updates outside the supported task workflow.
- They cannot add or remove users from Work Graph objects like teams or projects.
- They cannot bypass permissions.

### File and execution limits
- They cannot attach files directly to tasks; they can link to created files.
- They cannot generate images or PDFs.
- They cannot continuously monitor or poll for changes; they must be invoked by a task, mention, workflow trigger, or human action.

---

## Access model that matters in practice

- New AI Teammates can access work that is public to the domain, similar to a new user.
- Private projects, tasks, and teams require the AI Teammate to be explicitly added just like a colleague.
- When a user triggers a Teammate, the result is bounded by what both the user and the Teammate can access.
- Third-party file access uses the triggering user's tokens and permissions.

This means:
- Do not recommend a Teammate for a private workflow unless you also specify how it gets access.
- Do not assume cross-project memory unless the Teammate can access those projects.

---

## Memory guidance

- Memories are useful for continuity, not magic.
- Memories respect the permissions of the underlying task or project.
- Removing access removes memory visibility for that work.
- Recommend memories as a benefit only when the team will repeatedly use the same Teammate on related work.

---

## Knowledge source guidance

Best key resources:
- SOPs and process docs
- templates and exemplars
- style guides and glossaries
- sample briefs, summaries, or debriefs
- policy docs and decision criteria

Weak key resources:
- giant catch-all folders
- stale exports that change daily
- huge files with no clear relevance
- messy documents with no reusable structure

Rule of thumb:
- If a new team member should read it on day one, it is probably a good key resource.
- If the file exists only to compensate for bad project hygiene, fix the workflow first.

---

## Capability table by use case

| Use case | Supported? | Notes |
| --- | --- | --- |
| Draft status update from project history | Yes | Strong fit |
| Turn intake notes into a structured brief | Yes | Strong fit |
| Review a spec for gaps | Yes | Strong fit |
| Build an entire project plan from scratch | Partial | Can help draft structure and tasks, but do not overpromise full autonomous setup |
| Create sections in a project | Yes | Supported today |
| Create milestones or goals | No | Unsupported today |
| Research someone on LinkedIn or the live web | No | External agent required |
| Pull data from Salesforce, HubSpot, or a database | No | External agent or integration required |
| Draft into linked docs/sheets | Yes | Supported through connected file tools |
| Search connected PDFs or documents | Yes, with access | Both user and Teammate need access |
| Send an email on its own | No | Draft only, human or other system sends |
| Bulk reschedule hundreds of tasks | No | Use workflows, scripts, or other tooling |

---

## Planning guidance

When recommending builds:
- Prefer narrow specialists over one giant generalist.
- Include access and sharing requirements every time.
- Separate Asana-native collaboration from external-data automation.
- If a workflow depends on live external intelligence, route it to a Hybrid or Claude Code agent instead of pretending a Teammate can do it.

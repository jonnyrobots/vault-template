# Second Brain Vault

A working-memory vault for a product manager. It tracks parallel work, weekly planning, meeting and 1:1 notes, decisions, reusable knowledge, monthly reports, and personal growth, and is set up so Claude Code or another agent can read and update it.

Adapted from an engineering lead's vault template. Engineering, people-management, and Jira pieces have been removed.

## Folder Structure

```
.
├── Weekly Notes/           # YYYY-MM/YYYY-MM-DD.md, one note per week
├── Notes/                  # Task logs, knowledge notes, and decisions
│   └── investigations/     # Deep-dive research and discovery notes
├── Meetings/               # One note per meeting
├── People/                 # One note per person, with running 1:1 notes
├── Tags/                   # Tag index files used as wiki-link tags
├── Templates/              # Templater templates
├── MBR/                    # Monthly reports, YYYY-MM.md
├── P&G/                    # My own performance and growth notes
├── workflow-prompts/       # Agent workflows, readable by any LLM tool
├── AGENTS.md               # Shared agent instructions
├── CLAUDE.md               # Claude Code entry point (imports AGENTS.md)
└── .claude/commands/       # Claude slash commands that point at workflow-prompts/
```

## Setup

1. Open this folder as an Obsidian vault.
2. Install the community plugins listed below.
3. Enable Templater and set `Templates` as the templates folder.
4. Create your first weekly note from `Templates/Work Weekly Note.md`.
5. Edit `workflow-prompts/tickets.md` with your Azure DevOps organization and project.

## Templates

| Template | Creates | Files into |
|---|---|---|
| Work Weekly Note | This week's plan and summary | `Weekly Notes/YYYY-MM/` |
| Task log | A durable progress trail for a piece of work | `Notes/` |
| Knowledge | A reference or learning note | `Notes/` |
| Decision | A decision record with options and rationale | `Notes/` |
| Meeting | Notes for one meeting | `Meetings/` |
| Person | A person note with running 1:1 notes | `People/` |
| Monthly Report | This month's report | `MBR/` |
| Growth | A review-period growth note | `P&G/` |
| New tag | A tag index file | `Tags/` |

## Obsidian Plugins

These match the enabled plugin IDs in `.obsidian/community-plugins.json`.

| Plugin | ID | Purpose |
|---|---|---|
| **Todo Sort** | `todo-sort` | Keeps task lists ordered. |
| **Rollover Daily Todos** | `obsidian-rollover-daily-todos` | Carries open checkboxes forward. |
| **Tasks** | `obsidian-tasks-plugin` | Powers carried-task queries in weekly notes. |
| **Templater** | `templater-obsidian` | Powers dynamic templates and auto-filing. |
| **Custom Frames** | `obsidian-custom-frames` | Adds optional sidebars for calendar, Azure DevOps, docs, or other web pages. |
| **Dataview** | `dataview` | Builds task-log, decision, and report tables from frontmatter. |
| **Natural Language Dates** | `nldates-obsidian` | Adds quick natural-language date entry. |
| **Claudian** | `realclaudian` | Embeds coding agents in the vault with the vault as their working directory. |

Do not commit plugin credentials or session state.

## Tags

Tags are notes, not hashtags. Each tag has a file in `Tags/`, and notes reference tags from frontmatter as a list of wiki links:

```yaml
tag:
  - "[[task-log]]"
  - "[[in-progress]]"
```

* **Type tags** say what a note is: `task-log`, `decision`, `meetings`, `people`, `weekly-notes`, `mbr`, `growth`, `learning`, `investigation`.
* **Status tags** say where work stands: `in-progress`, `blocked`, `done`. A task log carries exactly one.
* **Theme tags** group notes across types: `strategy`, `idea`, `brag`, `private`.

Open any tag file to see every note that uses it in the backlinks panel. Dataview queries in the weekly note, monthly report, and growth template read these tags.

## Tickets

Tickets live in Azure DevOps. Put a work item's full URL in a note's `ticket` field, or link it inline as `[#1234](<url>)`.

## Assistant Workflows

Workflows live in `workflow-prompts/` as plain markdown, so any agent can follow them. `AGENTS.md` is the shared entry point; `CLAUDE.md` imports it and lists the Claude slash commands.

* `weekly-report`: write a concise summary in the current weekly note.
* `monthly-report`: draft or update this month's report in `MBR/`.
* `create-ticket`: draft an Azure DevOps work item from a short request.

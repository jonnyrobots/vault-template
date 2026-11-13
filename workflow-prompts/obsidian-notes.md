# Obsidian Notes

Read this before creating, moving, or editing files in this vault.

## Folder Layout

| Folder | Contents |
|---|---|
| `Weekly Notes/YYYY-MM/YYYY-MM-DD.md` | One note per week. The filename is the Monday of that week. |
| `Notes/` | Task logs, knowledge notes, and decisions. |
| `Notes/investigations/` | Deep-dive research and discovery notes. Tag with `[[investigation]]`. |
| `Meetings/` | One note per meeting. 1:1s go in the person's note instead. |
| `People/` | One note per person, holding running 1:1 notes. |
| `Tags/` | One file per tag. |
| `Templates/` | Templater templates. Do not edit unless asked. |
| `MBR/` | Monthly reports, one per month, named `YYYY-MM.md`. |
| `P&G/` | My own performance and growth notes, one per review period. |
| `workflow-prompts/` | Workflow instructions shared by every agent. |

## Tags

Tags are notes in `Tags/`, not hashtags. Reference them from the `tag` frontmatter field, always as a list of wiki links:

```yaml
tag:
  - "[[task-log]]"
  - "[[in-progress]]"
```

There are three kinds:

* **Type tags** say what a note is: `task-log`, `decision`, `meetings`, `people`, `weekly-notes`, `mbr`, `growth`, `learning`, `investigation`.
* **Status tags** say where work stands: `in-progress`, `blocked`, `done`. A task log carries exactly one. Swap it when the state changes.
* **Theme tags** group notes across types: `strategy`, `idea`, `brag`, `private`.

Use only tags that have a file in `Tags/`. If a new tag is needed, ask first, then create `Tags/<tag>.md` with a heading and a one-line "Use for ..." description.

## Frontmatter Schema

Task log (`Notes/`):

```yaml
---
date: YYYY-MM-DD
type: task-log
priority: medium        # high, medium, low
ticket:                 # full Azure DevOps work item URL
topic:
tag:
  - "[[task-log]]"
  - "[[in-progress]]"   # or [[blocked]] or [[done]]
---
```

Knowledge note (`Notes/`):

```yaml
---
date: YYYY-MM-DD
type: note
topic:
source:
tag:
  - "[[learning]]"
---
```

Decision (`Notes/`):

```yaml
---
date: YYYY-MM-DD
type: decision
topic:
tag:
  - "[[decision]]"
---
```

Meeting (`Meetings/`):

```yaml
---
date: YYYY-MM-DD
attendees: []
project:
tag:
  - "[[meetings]]"
---
```

Person (`People/`):

```yaml
---
team:
role:
tag:
  - "[[people]]"
---
```

Growth (`P&G/`):

```yaml
---
start: YYYY-MM-DD
end: YYYY-MM-DD
tag:
  - "[[growth]]"
---
```

Monthly report (`MBR/YYYY-MM.md`):

```yaml
---
month: YYYY-MM
tag:
  - "[[mbr]]"
---
```

Weekly note:

```yaml
---
week: YYYY-MM-DD / YYYY-MM-DD
tag:
  - "[[weekly-notes]]"
---
```

## Note Formats

**Weekly note.** Sections in order: Focus, Todos, Carried Over (Tasks query), Active Task Logs (Dataview table), Meetings This Week (Dataview list), Notes, Weekly Summary. Add todos as `- [ ]` checkboxes under Todos.

**Task log.** Sections: Goal, Links, Context, Progress, Blockers, Next Steps. Add progress as a new `### YYYY-MM-DD` heading under Progress, newest last. Keep each entry short: what changed, why it matters, what is next.

**Person.** Sections: Context, Open Topics, 1:1 Notes, Feedback. Add each 1:1 as a `### YYYY-MM-DD` heading under 1:1 Notes, newest first. Move resolved Open Topics into that day's notes.

**Decision.** Sections: Context, Options Considered, Decision, Rationale, Consequences, Links.

## Tickets

Tickets live in Azure DevOps. Put the full work item URL in the `ticket` field. In body text, link with `[#1234](<url>)`. See `workflow-prompts/tickets.md`.

## Agent Rules

* Read the current weekly note before answering questions about current work.
* Do not create notes outside the folders above.
* Templates use Templater syntax (`<% ... %>`), which only runs inside Obsidian. When creating a note directly, copy the template's structure and write real values instead of Templater tags.
* Do not edit or replace Dataview or Tasks query blocks.
* Do not delete notes. If work is dropped, tag it `[[done]]` and say why under Progress.
* Do not quote or summarise notes tagged `[[private]]`, or Feedback sections in `People/`, in reports, ticket drafts, or anything meant to leave the vault, unless asked.
* Use wiki links (`[[Note name]]`) for internal references.
* Follow `workflow-prompts/writing-style.md`.

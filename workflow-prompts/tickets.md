# Tickets (Azure DevOps)

Customize this file for your team before drafting tickets.

## Project

* Organization: `https://dev.azure.com/<org>`
* Project: `<project>`
* Area path: `<area path>`
* Work item types in use: `Epic`, `Feature`, `User Story`, `Bug`, `Task`

## Linking From Notes

Work item URLs look like:

```
https://dev.azure.com/<org>/<project>/_workitems/edit/<id>
```

Put the full URL in a note's `ticket` field. In body text, write `[#<id>](<url>)`.

## Drafting a Ticket

1. Ask for the work item type if it is not clear from the request.
2. Read any related task log, decision, or meeting notes in the vault and link them in the draft.
3. Draft:
   * **Title:** specific and imperative, or "As a <user>, I want <goal>, so that <reason>" for user stories.
   * **Description:** the problem, who it affects, and why now. Two to five sentences.
   * **Acceptance criteria:** a checklist that can be verified. Use Given/When/Then when behaviour matters.
   * **Links:** related work items, docs, and designs.
4. Return the draft as markdown for pasting into Azure DevOps. Do not create the work item unless a connected tool is available and the user confirms.
5. Follow `workflow-prompts/writing-style.md`.

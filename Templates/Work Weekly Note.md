<%*
const weekNotesFolder = "Weekly Notes"
const dayOfWeek = tp.date.now("d");
const offsetToMonday = (dayOfWeek == 0) ? -6 : 1 - dayOfWeek;

const currentMonday = tp.date.now("YYYY-MM-DD", offsetToMonday);
const currentMondayFolder = tp.date.now("YYYY-MM", offsetToMonday);
const currentWeekExists = app.vault.getAbstractFileByPath(`Weekly Notes/${currentMondayFolder}/${currentMonday}.md`) !== null;
const weekOffset = currentWeekExists ? 7 : 0;

const thisMonday = tp.date.now("YYYY-MM-DD", offsetToMonday + weekOffset);
const thisFriday = tp.date.now("YYYY-MM-DD", offsetToMonday + 4 + weekOffset);
const thisMondayFolder = tp.date.now("YYYY-MM", offsetToMonday + weekOffset);
const pastWeekMonday = tp.date.now("YYYY-MM-DD", offsetToMonday - 7 + weekOffset);
const pastWeekFolder = tp.date.now("YYYY-MM", offsetToMonday - 7 + weekOffset);
const nextWeekMonday = tp.date.now("YYYY-MM-DD", offsetToMonday + 7 + weekOffset);
const nextWeekFolder = tp.date.now("YYYY-MM", offsetToMonday + 7 + weekOffset);
-%>
---
week: <%- `${thisMonday} / ${thisFriday}` %>
tag:
  - "[[weekly-notes]]"
---
# Week of <% thisMonday %>

<< [[<% weekNotesFolder %>/<% pastWeekFolder %>/<% pastWeekMonday %>|Previous week]] | [[<% weekNotesFolder %>/<% nextWeekFolder %>/<% nextWeekMonday %>|Next week]] >>

## Focus

-

## Todos

- [ ] 

## Carried Over

```tasks
not done
path includes Weekly Notes
path does not include <% thisMonday %>
group by filename
```

## Active Task Logs

```dataview
TABLE choice(contains(tag, [[blocked]]), "blocked", "in progress") AS state, priority, ticket, topic
FROM "Notes"
WHERE type = "task-log" AND (contains(tag, [[in-progress]]) OR contains(tag, [[blocked]]))
SORT priority ASC, date DESC
```

## Meetings This Week

```dataview
LIST
FROM "Meetings"
WHERE date >= date("<% thisMonday %>") AND date <= date("<% thisFriday %>")
SORT date ASC
```

## Notes

## Weekly Summary

<%* await tp.file.move(`${weekNotesFolder}/${thisMondayFolder}/${thisMonday}`) %>

<%* const month = tp.date.now("YYYY-MM") -%>
---
month: <% month %>
tag:
  - "[[mbr]]"
---
# <% month %>

## Summary

## Highlights

## Weekly Notes

```dataview
LIST
FROM "Weekly Notes/<% month %>"
SORT file.name ASC
```

## Decisions

```dataview
LIST
WHERE contains(tag, [[decision]]) AND date >= date("<% month %>-01") AND date < date("<% month %>-01") + dur(1 month)
SORT date ASC
```

## Wins

```dataview
LIST
WHERE contains(tag, [[brag]]) AND date >= date("<% month %>-01") AND date < date("<% month %>-01") + dur(1 month)
SORT date ASC
```

## Learnings

## Next Month

<%* await tp.file.move("MBR/" + month) %>

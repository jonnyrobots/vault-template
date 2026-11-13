---
start:
end:
tag:
  - "[[growth]]"
---
# <% tp.file.title %>

%% Set start and end to the review period as YYYY-MM-DD. %%

## Goals

## Evidence

```dataview
LIST
WHERE contains(tag, [[brag]]) AND date >= this.start AND date <= this.end
SORT date ASC
```

## Feedback Received

## Reflections

## Focus for Next Period

<% await tp.file.move("P&G/" + tp.file.title) %>

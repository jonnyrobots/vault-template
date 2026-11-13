---
date: <% tp.date.now("YYYY-MM-DD") %>
attendees: []
project:
tag:
  - "[[meetings]]"
---
# <% tp.file.title %>

## Purpose

## Notes

* 

## Decisions

## Action Items

* [ ] 

<% await tp.file.move("Meetings/" + tp.file.title) %>

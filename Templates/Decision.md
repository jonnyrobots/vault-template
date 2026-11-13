---
date: <% tp.date.now("YYYY-MM-DD") %>
type: decision
topic:
tag:
  - "[[decision]]"
---
# <% tp.file.title %>

## Context

## Options Considered

## Decision

## Rationale

## Consequences

## Links

<% await tp.file.move("Notes/" + tp.file.title) %>

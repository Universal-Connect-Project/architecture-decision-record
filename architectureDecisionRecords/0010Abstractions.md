# Title

Abstractions

## Context

Creating abstractions too early increases complexity, slows down development, and risks creating the wrong abstration.

## Decision

We will wait to create abstractions until there is an actual need for them. We can create abstractions after we've duplicated the code at least twice and understand how the abstraction will function with multiple use cases.

## Consequences

We may have more code duplication. We will build less poor abstractions. We won't waste time on abstractions that only end up being used once.
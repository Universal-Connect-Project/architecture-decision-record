# Title

Code Style

## Context

Developers have code style preferences that result in code style flip flopping between pull requests. We want a unified code style to solve this problem.

## Decision

This ADR will house the insignificant code style preferences that aren't big enough to warrant their own ADRs. The preferences follow:

### Function parameters
We prefer object parameters instead of a list of parameters. Using object parameters makes it obvious what each parameter is used for without having to navigate to function definitions, it requires less passing of null or undefined variables, and it makes it easier to add features to a function.

`const testFunction = ({ a, b }) => {}` instead of `const testFunction = (a, b) => {}`

### Inline exports
We prefer to export things inline instead of at the bottom of the file

`export const example = "example"`

### Camel case
We prefer to use camel case for variable names

`const testVariableName = "test"`

## Consequences

Developers have a source of truth when it comes to code style.
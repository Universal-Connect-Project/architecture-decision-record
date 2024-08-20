# Title

Styling our html

## Context

According to the [state of css 2023](https://2023.stateofcss.com/en-US/) the styling landscape is changing. Our previously preferred styling solution of [styled components](https://styled-components.com/) is on the downward trend. One of the reasons people are moving away from styled-components is that it doesn't have great performance. The most popular up and coming tools are significantly faster and have a smaller bundle size.

The tools that people are the most happy with in 2023 are [css modules](https://github.com/css-modules/css-modules) and [tailwindcss](https://tailwindcss.com/).

Tailwind pollutes your jsx with a lot of classnames, and requires you to learn a bunch of classnames that won't be useful if you move away from the framework.

CSS modules gives a lot of the benefits of styled components, but with faster performance. Using CSS modules will keep our basic css skills in tact.

## Decision

We will use CSS modules for our styling.

## Consequences

We will have a performant and easy to use system for styling.

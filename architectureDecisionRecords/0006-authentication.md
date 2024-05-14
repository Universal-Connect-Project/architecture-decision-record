# Title

Authentication

## Context

We need a way to authenticate our APIs and frontend. The current UCP offering relies on a homegrown auth service, and we want to remove reliance on our hosted services.

The three options for authentication we looked at were [SuperTokens](https://supertokens.com/), [Auth0](https://auth0.com/), and [Cognito](https://aws.amazon.com/cognito/).

Cognito is AWS specific, and isn't great to work with.

SuperTokens has less features and less security compliance than Auth0.

## Decision

We will use Auth0 for our authentication.

## Consequences

Auth0 will provide authentication for our services and UI. Auth0 appears more expensive than the other options, but it provides a great featureset which will speed up development.

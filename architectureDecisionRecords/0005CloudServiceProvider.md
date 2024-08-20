# Title

Cloud service provider

## Context

We need a place to host the new UCP services and UI.

The current services are hosted on [AWS](https://aws.amazon.com/). MX uses GCP, and if we were to host within MX's GCP instance, then we would get some DevOps support. We want complete separation of hosting for the Universal Connect Foundation, so we aren't reliant on MX. We don't have DevOps resources dedicated to this project, so we will need to use a fully managed cloud platform.

### Heroku Pricing

#### Compute Dynos

Eco - $5
Basic - $7
Standard 1x - $25
Standard 2x - $50

#### Postgres DB

Standard 0 - $50
Standard 2 - $200

#### Total Cost Estimate

Auth Service - $5 - Basic Dyno

Performance Service - $250 - Standard 2x dyno, Standard 2 DB (This service might scale enough that we need to upgrade)

Institution Service - $75 - Standard 1x dyno, Standard 0 DB

Demo app - $5 - Eco Dyno

Total - $335 monthly

## Decision

We will use [Heroku](https://www.heroku.com/) to host our services and UI.

## Consequences

We will be able to quickly and easily deploy our apps. We won't need DevOps expertise to secure our apps. The cost to run our apps will be higher than if we were to use AWS or GCP.

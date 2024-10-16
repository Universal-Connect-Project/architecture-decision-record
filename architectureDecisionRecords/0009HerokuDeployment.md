# Title

CI/CD Process

## Context

As was [previously decided](0005CloudServiceProvider.md), Heroku is the cloud service provider for UCP. In order to follow best practices, all services deployed to Heroku will follow a standard CI/CD process. Automating the deployment process will prevent human-caused errors, allow us to deploy small code changes frequently, and reduce overall risk to the project.

Within [Heroku pipelines](https://devcenter.heroku.com/articles/pipelines), there are 2 options for deployments: using Heroku to automatically deploy upon merging to the main branch, or using github actions to manually deploy a pull request.

For a standard Dev/Staging/Production environment set up, that leaves 2 options for deployments:

1. All deployments within Heroku

 * Dev environment: Heroku automatically deploys upon PR creation/update
 * Staging environment: Heroku automatically deploys upon PR merge into main
 * Production environment: Developer deploys code from Staging to Production by clicking the "Promote to production" button in Heroku

Pros of this method:
 * Setup is all point-and-click within Heroku
 * Heroku API keys are not shared with github
 * No custom github actions are needed

Cons of this method:
 * Deployment to production is a manual step, and has the potential to be forgotten by the developer

2. Mix of Heroku and github deployments

 * Dev environment: Heroku automatically deploys upon PR creation/update
 * Staging environment: Developer deploys code by clicking a github action within github
 * Production environment: Heroku automatically deploys code upon PR merge into main

Pros of this method:
 * Production will always match the main branch in github

Cons of this method:
 * Deployment to staging is a manual step, and has the potential to be forgotten by the developer
 * Additional setup of github actions is needed for every github project deployed to Heroku, which introduces a potential breaking point

## Decision

We will use the out-of-the-box tools in Heroku for continuous deployment.

The process for every change will be:
* Developer creates a PR within github
* Github actions run on the PR, running all tests and linters
* Heroku automatically deploys PR to heroku if all github actions pass
* 2nd Developer reviews code in github and approves the PR
* 1st Developer merges the PR
* Heroku automatically deploys the code from main to Heroku staging environment
* Developer verifies the app is running in staging
* Developer promotes code from staging to production using Heroku's "Promote to production" button

## Consequences

We will have a standard deployment process for every app.

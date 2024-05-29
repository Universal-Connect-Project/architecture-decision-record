# Title

Authentication

## Context

We need a way to authenticate our APIs and frontend. The current UCP offering relies on a homegrown auth service, and we 
want to remove reliance on our hosted services.

The three options for authentication we looked at were [SuperTokens](https://supertokens.com/), [Auth0](https://auth0.com/), and [Cognito](https://aws.amazon.com/cognito/).

### SuperTokens
SuperTokens has fewer features than Auth0. For what we need at this time, SuperTokens would work, but may not meet our 
future needs, without a hefty price increase. 

#### Security:
SuperTokens is SOC2 compliant.

#### Pricing:
Taken from https://supertokens.com/pricing/.

Pricing for SuperTokens is a bit simpler, but when multi-tenant is taken into consideration, it pushes it a lot higher. 

- $0.02 per MAU (Monthly Active Users)

For their multi-tenant offering, it adds $50/month for each additional tenant, which would be a drastic price increase as 
we add more customers. In our use-case, each of our customers would be a single tenant within the SuperTokens platform.

Our current feature set wouldn't require the multi-tenant feature, but if we allow self-hosting in the future, it would 
most likely be required.

### Cognito
Cognito is AWS specific, and the SDK isn't great to work with. Based on previous experience, it is not designed well. It 
also does not provide a default UI for sign-up and sign-in, so we would need to create our own.

#### Security:
Cognito is SOC2 compliant.

#### Pricing: 
Taken from https://aws.amazon.com/cognito/pricing/. Scroll down and find the pricing for "Machine-to-machine authorization".

For the M2M (Machine to Machine) model, there are three Tiers.

- 1 - 250,000 token requests per month: $2.250 per 1000 token requests
- 250,000 - 5,000,000 token requests per month: $1.500 per 1000 token requests
- 5,000,001+ token requests per month: $1.125 per 1000 token requests

While the pricing is reasonable, the price benefits of using Cognito are not worth the added overhead of implementing it.

### Auth0

Auth0 is a leader in the authentication space. Some of our current engineers have used Auth0 in the past.

#### Security:
Auth0 is SOC2 compliant.

#### Pricing:
Taken from https://auth0.com/pricing/. Select "B2B" as the use case.

Pricing for Auth0 is a bit more complicated. We are hoping to get Non-profit pricing, which gives us a 50% discount. 

Without that, we will be subject to the B2B pricing, which is listed below. The non-free tiers increase as the MAUs increase.

- Free tier: up to 7500 MAUs, with a limited feature set.
- Essential tier: $150/month - 500 MAUs, with everything in the free tier, plus additional features. More MAUs will cost more.
- Professional tier: $800/month - 500 MAUs, with everything in the essential tier, plus additional features. More MAUs will 
cost more.

At this point in time, with the feature set we have planned, we should be able to use the free tier. If we end up using 
their Organizations feature, we will need to jump to a paid tier.

## Decision

Based on the above, we will use Auth0 for our authentication.

## Consequences

Auth0 will provide authentication for our services and UI. Auth0 appears more expensive than the other options, but it 
provides a great feature set which will speed up development.

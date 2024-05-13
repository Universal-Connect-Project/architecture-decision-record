# Title

Remove reliance on UCP hosted services

## Context

We don't want customers to rely on the services we host to be able to run the universal connect widget. If any of our services are down, then we want customer widgets to continue functioning.

## Decision

We will do our best to have as much uptime as possible for our services, but we will build the universal connect widget in a way that it will continue to function even if our hosted services are down.

The widget will frequently poll and cache data that it needs from UCP hosted services. The widget will always use cached data to make decisions. If a UCP hosted service is down during a poll, then it will keep the old data in the cache. If there is nothing in the cache, then it will use old data that was checked into the code as a default.

## Consequences

Customers will have everything they need to run the widget, and we won't be the cause of any outages.

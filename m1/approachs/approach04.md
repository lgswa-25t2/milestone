# Approach 4: Introduce an Intermediary with a Filter Pipeline to Identify Unregistered Aircraft
There are general tactics for performance.
- Introduce Intermediary (e.g., Filter or Mediator)

  - Inserts a filtering step between data input and processing to isolate unregistered aircraft.

- Abstract Common Services
  - Encapsulates aircraft identification logic as a reusable service to support multiple use cases.

- Parameterize Functionality
  - Makes filtering behavior configurable, allowing future expansion without code changes.
- Filter (Pipe and Filter Pattern)
  - Processes data streams and isolates unregistered aircraft based on specific rules.

## Decision 
To support the extensible and maintainable implementation of unregistered aircraft identification, we will introduce an intermediary component in the data processing flow. This intermediary will be structured using the Filter (Pipe and Filter) design pattern to isolate and process flight data based on registration status.

## Rationale 
Unregistered aircraft identification is a distinct function that should not affect core data processing logic. By introducing an intermediary, we can inject this logic cleanly between data ingestion and display. The Filter pattern enables us to modularize this logic as a composable step in a processing pipeline. This approach improves separation of concerns, promotes code reuse, and allows the system to evolve without impacting other components.

## Status
[Proposed | ***Accepted*** | Deprecated | Superseded]

## Consequences
Resulting context will be described.
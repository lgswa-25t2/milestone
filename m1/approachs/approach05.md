# Approach 5: Supporting new map provider 
The system should allow developers to integrate a new map provider into the user interface with minimal code changes, low risk of introducing bugs, and without affecting unrelated parts of the system.

We have two options.

- Abstract Common Services with Map interface
  - Define a common abstract interface for map services that all map providers implement.
  - The RUI interacts only with this interface, allowing developers to add new providers without modifying core UI logic.
  - This reduces coupling between the UI and specific providers while improving cohesion within map modules.
- Modularize Map Component with Dependency Injection
  - Encapsulate map logic into a standalone module injected at runtime into the RUI.
  - New providers are integrated by injecting a module that adheres to the map interface.
  - This defers binding decisions to runtime, enabling flexibility and clean separation of concerns.

## Decision 
We will use abstract common services with Map Interface to enable structed, low-risk integration of new map providers without disrupting existing UI behavior.

## Rationale 
- ✅ Abstract Common Services with Map Interface
  - Provides compile-time safety and clarity.
  - Ideal when new map providers are added occasionally.
  - Promotes high cohesion within mapping logic and minimizes dependencies.
- ⚠️ Modularize Map Component with Dependency Injection
  - Suitable when map providers need to be added or replaced frequently.
  - Increases flexibility through runtime configuration.
  - Keeps UI logic unchanged, improving long-term maintainability.

## Status
[Proposed | ***Accepted*** | Deprecated | Superseded]

## Consequences
Resulting context will be described.
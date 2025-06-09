# Approach 6: Easily understood, corrected, improved, and adapted over time
The system should allow developers to integrate a new map provider into the user interface with minimal code changes, low risk of introducing bugs, and without affecting unrelated parts of the system.

We have several options.

- Anticipate Expected Changes
  - Description: Isolate parts of the system that are likely to change (e.g., UI elements, business rules) into configurable or modular components.
  - Example: Externalize UI text, styles, or layout structure into configuration files (e.g., JSON, XML).

- Restrict Communication Paths

  - Description: Limit the direct dependencies between modules to reduce the ripple effect of changes.

  - Example: The UI does not directly call data-processing logic but communicates via well-defined interfaces.

- Use Abstract Interfaces

  - Description: Depend on interfaces or abstract classes instead of concrete implementations to allow for easier substitution or extension.

  - Example: Define an interface like Aircraft Identifier to allow swapping between different identification strategies.

- Document Design Decisions

  - Description: Maintain records of architectural decisions to help future developers understand why certain choices were made.

  - Example: Use ADR (Architecture Decision Records) to capture trade-offs and rationale.

## Decision 
We will use *Use Abstract Interfaces* and *Document Design Decisions*.

- Interfaces or abstract classes will be used instead of direct dependencies on concrete implementations, particularly for extensible or volatile parts of the system (e.g., aircraft identification logic, UI event handlers).

- All major architectural and design decisions will be recorded using ADRs (Architecture Decision Records) in a shared repository.

## Rationale 
- This approach promotes modularity and allows multiple implementations to coexist or be swapped without affecting the rest of the system. It also facilitates testing by enabling the use of mocks or stubs.
- Documenting decisions ensures future developers understand the rationale behind architectural choices. This minimizes rework, avoids repeated discussions, and helps with onboarding and system evolution.

## Status
[Proposed | Accepted | ***Deprecated*** | Superseded]

## Consequences
Resulting context will be described.

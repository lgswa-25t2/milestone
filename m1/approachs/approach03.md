# Approach 3: Encapsulate deviation detection logic to isolate change
There are general tactics for extensiblity.
- Separate Interface from Implementation
  - Keeps the UI and analysis logic decoupled, allowing new features to be added independently**.**
    
- Encapsulate Change
  - Isolates frequently changing logic (e.g., deviation algorithms) in separate components.

- Strategy Pattern
  - Enables easy replacement or extension of deviation detection algorithms.

- Observer Pattern
  - Allows the deviation module to respond to changes in real-time flight data.

## Decision 
The deviation detection logic will be encapsulated in a separate, well-defined module to isolate it from the rest of the system.

## Rationale 
Deviation detection is a feature that is likely to evolve, with potential changes in algorithms or detection criteria. Encapsulating this logic reduces coupling and limits the impact of future changes to a single component. This supports extensibility and simplifies maintenance.

## Status
[Proposed | ***Accepted*** | Deprecated | Superseded]

## Consequences
Resulting context will be described.

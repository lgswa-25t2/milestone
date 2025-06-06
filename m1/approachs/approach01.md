# Approach 1: Improving UI respond time
There are general tactics for performance.
- Resource Management
  - Increase computational resources
  - Manage concurrency - Use background threads for data reception and analysis, main thread for UI
- Data Management
  - Caching - Cache aircraft detail panels, map tiles, and frequent UI states
  - Data Prioritization / Filtering - Filter aircraft by current viewport
- Structual
  - Asyncronous communication - Use async/await for user actions, event queue for incoming aircraft data
  - Component isolatoin - Separate rendering engine, data processor, and UI controller into modular components
- User interface handling
  - Progressive Rendering - On zoom/pan, render center-view aircraft first, defer off-screen elements

## Decision 
We can't decide yet. In order to make a decision, it is necessary to determine the current performance, check whether it is a applied, and check the improvement after applying the strategy.

## Rationale 
TBD

## Status
[***Proposed*** | Accepted | Deprecated | Superseded]

## Consequences
Resulting context will be described.
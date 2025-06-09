# Approach 7: Providing pause/resume function 
Users shall be able to pause live aircraft data updates to analyze specific tracks without distraction, then resume updates smoothly.

We have two options.

- Deferred Data Rendering
  - The system continuously receives live ADS-B data, but when the user pauses the view, incoming data is held back from immediate display and stored temporarily.
  - When the user resumes, the stored data is rendered on the UI in a controlled manner, ensuring smooth updates without overwhelming the user.
  - The buffer size is managed to prevent memory overload by discarding the oldest data as needed.
- Approach 2: Adaptive Data Throttling at Source
  - The Raspberry Pi Flight Tracker adjusts its data transmission rate based on the UI state.
  - When paused, the Pi reduces or temporarily halts data streaming to the user interface.
  - On resume, the full data stream is restored for real-time updates.

## Decision 
After evaluating both architectural approaches against key quality attributes — performance, resiliency, extensibility, and modifiability - the recommended solution for implementing Pause/Play functionality is:

Deferred Data Rendering

## Rationale 
Tradeoff Analysis

| Quality Attribute | Deferred Data Rendering                       | Adaptive Data Throttling at Source              |
| ----------------- | --------------------------------------------- | ----------------------------------------------- |
| Performance       | Fast UI response; data still arrives smoothly | May introduce lag due to changing data rates    |
| Resiliency        | High; data always collected locally           | Moderate; depends on reliable communication     |
| Extensibility     | Moderate; buffering logic localized to UI     | Limited; requires changes to source data system |
| Modifiability     | Easier to change within UI component          | More complex; source and UI must coordinate     |

Quality Attribute Deferred Data Rendering Adaptive Data Throttling at Source Performance Fast UI response; data still arrives smoothly May introduce lag due to changing data rates Resiliency High; data always collected locally Moderate; depends on reliable communication Extensibility Moderate; buffering logic localized to UI Limited; requires changes to source data system Modifiability Easier to change within UI component More complex; source and UI must coordinate



- ✅ Deferred Data Rendering
  - Continuous data capture is important, regardless of UI state.
  - Quick UI responsiveness with minimal complexity is required.
  - Modifications should be limited to the UI side.
  - **Observer and Command pattern used:**
- ⚠️ Adaptive Data Throttling at Source
  - Reducing unnecessary data transmission is important (e.g., bandwidth or power saving).
  - There is flexibility and capability to modify the Raspberry Pi software.
  - Close coordination between source and UI is manageable.

## Status
[Proposed | Accepted | ***Deprecated*** | Superseded]

## Consequences
Resulting context will be described.

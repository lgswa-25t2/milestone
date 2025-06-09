# Approach 2: Detecing/recovering failure conditions
There are general tactics for performance.
- Fault detection
  - Heartbeat - Ping Rasp.PI every 1~2 seconds from GUI, check serial/USB data stream heartbeat
- Fault notification
  - User Feedback Mechanism - Show status banner or message box (e.g. Disconnected PI)
- Fault isolation
  - Component Encapsulation - Separate network, UI, data threads with fault boundaries and watchdog recovery
- Fault recovery
  - Automatic Reconnection - On connection loss, start retry logic with fixed backoff (e.g., 5s interval)
  - Graceful Degradation - Keep UI interactive; freeze aircraft state; show “no data” indicator

## Decision 
We can't decide yet. In order to make a decision, it is necessary to determine the current performance, check whether it is a applied, and check the improvement after applying the strategy.

## Rationale 
TBD

## Status
[***Proposed*** | Accepted | Deprecated | Superseded]

## Consequences
Resulting context will be described.
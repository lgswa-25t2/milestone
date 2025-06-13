# Design Decisions

This document clearly documents the key decisions made during the system design process and explains the background, rationale, alternatives, and implications.

| ID           | Related ID | Description                                                  | Link                              |
| ------------ | ---------- | ------------------------------------------------------------ | --------------------------------- |
| APPROACH_001 | QA_001     | Improving UI respond time                                    | [Link](./approachs/approach01.md) |
| APPROACH_002 | QA_002     | Detecing/recovering failure conditions                       | [Link](./approachs/approach02.md) |
| APPROACH_003 | QA_003     | Encapsulate deviation detection logic to isolate change      | [Link](./approachs/approach03.md) |
| APPROACH_004 | QA_004     | Applying Architecture pattern for Modular Aircraft Identification | [Link](./approachs/approach04.md) |
| APPROACH_005 | QA_005     | Supporting new map provider                                  | [Link](./approachs/approach05.md) |







## TODO

# Key Design Strategies

This section describes the key architectural strategies that guide our system design, along with their motivation and impact. The content is organized thematically—not by ID—for better readability.

---

## 1. Improving UI Responsiveness

To ensure smooth user interactions and fast map updates, we:

 - Minimize synchronous operations in the UI thread

 - Use background threads to fetch aircraft data

 - Apply throttling to reduce UI redraw rate without sacrificing usability

_This addresses the quality attribute: performance (QA_001)._

---

## 2. Detecting and Recovering from Failures

The system employs:

 - Heartbeat monitoring from the Raspberry Pi every 500ms

 - Status banners in the UI to inform users of disconnections

 - Retry strategy and fallback logic to recover gracefully

_This supports resilience and availability (QA_002)._

---

## 3. Isolating Deviation Detection Logic

To allow flexibility in changing the deviation-detection criteria without affecting other modules:

 - The logic is encapsulated in a separate service class

 - It only exposes a public method: `bool isDeviated(AircraftTrack track)`

_This supports modifiability (QA_003)._

---

## 4. Modular Aircraft Identification

We apply a plugin-based architecture for aircraft identification:

 - Each module identifies aircraft based on a rule set (e.g., hex pattern, callsign prefix)

 - New identifiers can be added without modifying existing modules

_This supports modifiability and extensibility (QA_004)._

---

## 5. Supporting New Map Providers

To prepare for adding new map layers (e.g., OpenStreetMap):

 - We abstract the map engine behind a `MapProvider` interface

 - Existing Google Maps and IFR/VFR maps implement this interface

_This promotes portability and vendor-independence (QA_005)._

---

### 🔧 Optional: Diagram Example (for e.g., Strategy #4)
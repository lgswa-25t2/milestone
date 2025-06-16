# Architecture - under construction



This document outlines the overall architectural strategy and key design principles of the system. The focus is on performance, resilence, availability, modifiability, extensibility and portability.

---

## 1. Improving UI Responsiveness. --> cache pattern? tactic?
**Decision:**

 - Minimize synchronous operations in the UI thread

 - Frequently used or repeated data is cached in memory to reduce rendering delays.

 - Only changed UI regions are updated rather than redrawing the entire screen

_This addresses the quality attribute: performance (QA_001)._

**Rationale:**

 - Fast and responsive is critical in real-time aircraft monitoring scenarios.
---

## 2. Detecting and Recovering from Failures --> Heartbeat & retry
**Decision:**

 - Heartbeat monitoring from the Raspberry Pi every 500ms

 - Status banners in the UI to inform users of disconnections

 - Retry strategy and fallback logic to recover gracefully

_This supports resilience and availability (QA_002)._

**Rationale:**

 - In real-time systems, high availability and fault isolation are essential to maintain service continuity.

---

## 3. Isolating Deviation Detection Logic --> encapsulated? interface
**Decision:**

 - The logic is encapsulated in a separate service class

 - It only exposes a public method: `bool isDeviated(AircraftTrack track)`

_This supports modifiability (QA_003)._

**Rationale:**

- Complex business logic must be isolated to minimize change impact and increase modularity.
---

## 4. Modular Aircraft Identification
**Decision:**

 - Each module identifies aircraft based on a rule set (e.g., hex pattern, callsign prefix)

 - New identifiers can be added without modifying existing modules

_This supports modifiability and extensibility (QA_004)._

**Rationale:**

- The identification process evolves rapidly and must be flexible and extensible by design.
---

## 5. Supporting New Map Providers --> abstraction??
**Decision:**

 - We abstract the map engine behind a `MapProvider` interface

 - Existing Google Maps and IFR/VFR maps implement this interface

_This promotes portability and vendor-independence (QA_005)._

**Rationale:**

- Avoid vendor lock-in and support different geographical or pricing requirements.
---

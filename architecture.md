# Architecture - under construction

You can find our software architecture documentation for system requirements in this document.

First, the context diagram of our system and external elements is as follows.

![Context Diagram](./images/context-diagram.jpg)



Also, this is a deployment view that shows the infrastructure for each components.

<table>
<tr><td align="center"><a href="./architecture/IFTA_Deployment_View.md">Deployment view<br>
<img src="https://github.com/user-attachments/assets/217bcb79-3f64-4034-b285-ac11970d8b80" width="700"></a></td></tr>
</table>







---

## 아래는 참조용 - 곧 지울거임 TODO TBD NA N/A

Paulo 의 팀 [project 문서](https://github.com/miyagis-forests/farmacy-food-kata/blob/main/README.md#architecture) 참조



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

- Deviation detection is a feature that is likely to evolve, with potential changes in algorithms or detection criteria. Encapsulating this logic reduces coupling and limits the impact of future changes to a single component. This supports extensibility and simplifies maintenance.
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

- ✅ Abstract Common Services with Map Interface
  - Provides compile-time safety and clarity.
  - Ideal when new map providers are added occasionally.
  - Promotes high cohesion within mapping logic and minimizes dependencies.
- ⚠️ Modularize Map Component with Dependency Injection
  - Suitable when map providers need to be added or replaced frequently.
  - Increases flexibility through runtime configuration.
  - Keeps UI logic unchanged, improving long-term maintainability.
---

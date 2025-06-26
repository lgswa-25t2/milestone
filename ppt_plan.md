# IFTA Final Presentation Slide Draft 

---

## Slide 1: Title

* **Project Name**: Intelligent Flight Tracking Assistant (IFTA)
* **Team**: Team #2 Challenger
* **Members**: \[Insert Names]
* **Date**: \[Insert Date]

---

## Slide 2: Introduction

* Project in response to Solvit’s requirements
* Objective: Develop a real-time aircraft monitoring and analysis system
* Platform: Windows GUI application (C++, VCL-based)

---

## Slide 3: Team & Timeline

* 5-week project / 7 team members
* Role distribution (UI, Metadata, Safety, QA, etc.)
* Key schedule summarized as a Gantt chart

---

## Slide 4: Problem Statement

* Real-time processing and visualization of thousands of aircraft
* Ensuring responsive user interface
* Integration of safety analysis features

---

## Slide 5: System Goals

* 100% implementation of mandatory features
* Implement as many desirable features as possible
* Achieve high-quality architecture (performance, extensibility, etc.)

---

## Slide 6: Architecture Drivers

* Stakeholders and constraints
* Key functional requirements categorized (Metadata, Time Series, Safety, UI)
* Prioritized quality attributes (QAR\_001\~005)

---

## Slide 7: Technical Risks & Mitigation

* TR1: Aircraft data overload → Apply sampling and viewport restriction
* TR2: VCL does not support multithreading → Separate UI and logic
* TR4: High code coupling → Decoupled UI, logic, and network components

---

## Slide 8: Architecture Overview

* Summary of key architectural tactics (e.g., Introduce Concurrency, Aggregation)
* Designed for both performance and extensibility

---

## Slide 9: Architecture Views – Runtime & Module

* **Component & Connector (C\&C) View**: Shows aircraft rendering logic with aggregation based on zoom level.
* **Module View**: Illustrates software module dependencies and responsibilities.

---

## Slide 10: Deployment View

* **Deployment View**: Describes the infrastructure including Raspberry Pi, ADS-B hub, and the client system.
* Demonstrates how system components are physically and logically distributed.

## Slide 11: ADR Highlights

* ADR\_01: Viewport Aggregation strategy
* Enhances performance and user clarity (target < 100ms rendering)
* Limit rendering objects on UI to below 1800

---

## Slide 12: Experiment Summary

* **EXP\_01**: Rendering performance test
  → Confirmed lag with >2000 aircraft. Led to ADR\_01 (viewport aggregation) and object count threshold (<1800).

* **EXP\_06**: Raspberry Pi connectivity monitoring
  → Validated disconnection detection logic within 1 sec. Supports QAR\_002 resiliency goals.

* **EXP\_09**: New map provider integration
  → Verified modular integration of OpenStreetMap. Demonstrates system modifiability (QAR\_005).

---

## Slide 13: Functional Features Implemented

### 1. Aircraft Metadata & Route Lookup

* Real-time retrieval of aircraft details (ICAO-based) (done)
* Visual display of origin and destination (airport code) (done)
* Route information shown with waypoints and airway overlay (in progress)

### 2. Time Series Tracking and Visualization

* Real-time position tracking with historical trail (white path lines) (done)
* Automatic removal of stale data (older than 30 seconds) (done)
* 3-step UX for navigation: Tracking → Simulation → Playback (in progress)

### 3. Safety Analysis and Deviation Detection (Desired)

* Detects proximity-based collision risks (1nm/5nm airport zones) (in progress)
* Compares actual path vs. planned route to detect deviation (to do)
* Detect abnormal flight profiles (e.g., abnormal route, unregistered flights) (in progress)

### 4. UI/UX Enhancement

* Improved aircraft icon clarity, category-specific icons (done)
* Aircraft type filter enabled for better control of displayed data (done)
* Integrated airport markers and area polygon filters (done)
* Support for switching to live map view for enhanced usability (done)
* Side panel redesigned to support collapsible sections (done)

---

## Slide 14: Quality Attribute Implementation

* QAR\_001/002: Improved responsiveness (DrawObject optimization, thread separation)
* QAR\_003/004: Ensured extensibility (deviation and identification modules)
* QAR\_005: Modularized map provider integration

---

## Slide 15: Module Refactoring Proposal (Not Implemented)

* Motivation: Eliminate cyclic dependencies and improve maintainability
* Observed issues:

  * DisplayGUI acts as a God Object
  * UI and business logic are tightly coupled
  * Cycles: DisplayGUI ↔ AreaDialog, indirect cycles via SBS\_Message, DecodeRawADS\_B

---

## Slide 16: Planned Layered Architecture

* Proposed 5-layer architecture:

  1. Application Entry
  2. UI & Presentation
  3. Business Logic & Services
  4. Data Models & Entities
  5. Core Utilities
* Key idea: Move business logic to service layer, UI only depends on interfaces

---

## Slide 17: Lessons Learned

* Importance of separating UI and logic layers
* Effectiveness of experiment-based design
* Value of visual tools and translation in international collaboration

---

## Slide 18: Challenges

* Ambiguous requirements → Resolved via mentor/sponsor Q\&A
* Security tools blocking dev/test → Used alternative devices
* Tight schedule → Prioritized essential features and leveraged planning tools

---

## Slide 19: Conclusion

* Achieved key goals (functionality, quality, structure)


---

## Slide 20: Q\&A



# Intelligent Flight Tracking Assistant System - Layered Module View

The ADS-B Display System currently suffers from significant architectural issues that impact maintainability, testability, and extensibility. </br>
To address these challenges, we proposed a layered architecture. </br>
The following is the corresponding architecture view. Due to limited implementation time, the layered structure was not fully applied in the actual system.
  
## 1. Primary Presentation

### Key Diagrams

#### Planned Layered Architecture
![image](https://github.com/user-attachments/assets/6801cebf-a5ca-4aef-889d-9f7550f45c5c)

## 2. Element Catalog

| Layer | Module           | Description                                                                 |
|-------|------------------|-----------------------------------------------------------------------------|
| **1. Application Entry** | `ADS-B-Display`       | Entry point of the system. Initializes UI and manages main flow.         |
| **2. UI & Presentation** | `DisplayGUI`          | Main UI component handling user interactions and data display.           |
|                           | `AreaDialog`         | Manages geographic area settings and interactions.                       |
| **3. Business Logic & Services** | `AircraftService`     | Handles aircraft-related logic and coordinates data access.              |
|                           | `DataProcessor`      | Decodes and validates raw ADS-B data.                                    |
|                           | `GeometryService`    | Computes geographic calculations, e.g., point-in-polygon, coordinate conversion. |
| **4. Data Models & Entities**        | `Aircraft`           | Represents an individual aircraft and its data.                          |
|                           | `SBS_Message`        | Parsed structure of decoded ADS-B message.                               |
|                           | `AircraftDB`         | Data store that maintains and queries aircraft states.                   |
| **5. Core Utilities & Infrastructure**     | `CPA`                | Calculates Closest Point of Approach (CPA) between aircraft.             |
|                           | `TimeFunctions`      | Utility functions for time calculation and formatting.                   |
|                           | `LatLonConv`         | Converts latitude/longitude coordinates to display format.               |


## 3. Behavior
- N/A

## 4. Design Rationale

### Objective
- Eliminate current cyclic dependencies in the system to improve maintainability and modifiability.

#### Legacy Architecture - Key Cyclic Dependencies
| Cycle | Type | Description |
|-------|------|-------------|
| 1 | Bidirectional | `DisplayGUI ↔ AreaDialog` |
| 2 | Indirect | `DisplayGUI → SBS_Message → DisplayGUI` |
| 3 | Indirect | `DisplayGUI → DecodeRawADS_B → DisplayGUI` |

### Root Causes
- **God Object (DisplayGUI)**: Excessive responsibilities concentrated in one class (5946 lines).
- **Lack of Layered Structure**: Business and UI logic are tightly coupled.
- **Direct Coupling**: UI directly depends on data model implementations.

### Architectural Alternatives Considered

| Option | Description | Pros | Cons | Reason Not Chosen |
|--------|-------------|------|------|-------------------|
| **Keep monolithic DisplayGUI** | Continue using DisplayGUI as central coordinator | • No migration effort<br>• Familiar to current developers | • High coupling<br>• Poor testability<br>• Single point of failure | High coupling and poor testability made it unsustainable |
| **MVC Pattern** | Model-View-Controller separation | • Resolves cyclic dependencies<br>• Well-known pattern<br>• Clear UI/logic separation | • Controller can become complex<br>• C++ Builder form constraints<br>• Less granular than needed | Good option, but layered provides more granular separation for complex domain logic |
| **Microservices** | Split into separate processes | • Complete isolation<br>• Independent scaling | • Over-engineering for single-user app<br>• IPC overhead<br>• Deployment complexity | Too complex for desktop application |
| **Component-based** | Plugin architecture with components | • High flexibility<br>• Runtime composition | • Complex plugin management<br>• Performance overhead | Unnecessary complexity for current needs |

### Why Layered + Dependency Inversion Was Chosen

#### Technical Benefits
- **Dependency Control**: Interfaces break cyclic dependencies through inversion
- **Testability**: Each layer can be unit tested independently
- **Maintainability**: Single Responsibility Principle reduces code complexity
- **Extensibility**: New features can be added without modifying existing layers

#### Business Benefits
- **Parallel Development**: Teams can work on different layers simultaneously  
- **Risk Reduction**: Bugs are contained within layer boundaries
- **Future-Proofing**: Architecture supports planned features (multiple data sources, different renderers)

### Key Design Decisions

| Decision | Rationale |
|----------|-----------|
| **5-Layer Structure** | Balances granularity vs. complexity - not too fine-grained, not too coarse |
| **Hash Table for Aircraft Storage** | O(1) lookup performance critical for real-time tracking of 1000+ aircraft |
| **Interface-based Service Layer** | Enables dependency injection and mock objects for testing |
| **C++ Builder Retained for UI** | Leverages existing codebase and team expertise while isolating UI concerns |

### Trade-offs & Consequences

#### Positive
-  **Reduced Coupling**: Clear dependency flow eliminates cycles
-  **Improved Testability**: Business logic can be tested without UI
-  **Better Performance**: Service layer optimizations don't affect UI
-  **Team Productivity**: Parallel development on different layers

#### Negative  
- **Migration Effort**: ~2-3 weeks to refactor existing 5946-line DisplayGUI
- **Initial Complexity**: More files and interfaces to manage
- **Learning Curve**: Team needs to understand layered patterns

#### Mitigation Strategies
- **Incremental Migration**: Extract one service at a time (start with AircraftService)
- **Interface Documentation**: Clear contracts between layers
- **Automated Testing**: Unit tests for each extracted service

### Success Metrics
- **Code Quality**: Reduce cyclic complexity from current 15+ to 0
- **Maintainability**: Reduce average bug fix time by 40%
- **Testability**: Achieve 80%+ unit test coverage for business logic
- **Performance**: Maintain <100ms aircraft update latency


## 5. Related Views
- Deployment View - [Intelligent Flight Tracking Assistant System Deployment View](./IFTA_Deployment_View.md)

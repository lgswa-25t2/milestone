# Intelligent Flight Tracking Assistant System - Layered Module View

## Objective
Eliminate current cyclic dependencies in the system to improve maintainability and modifiability.

### Legacy Architecture - Key Cyclic Dependencies
| Cycle | Type | Description |
|-------|------|-------------|
| 1 | Bidirectional | `DisplayGUI ↔ AreaDialog` |
| 2 | Indirect | `DisplayGUI → SBS_Message → DisplayGUI` |
| 3 | Indirect | `DisplayGUI → DecodeRawADS_B → DisplayGUI` |

### Root Causes
- **God Object (DisplayGUI)**: Excessive responsibilities concentrated in one class.
- **Lack of Layered Structure**: Business and UI logic are tightly coupled.
- **Direct Coupling**: UI directly depends on data model implementations.

---
## 1. Primary Presentation

### Key Diagrams

#### Planned Layered Architecture
![image](https://github.com/user-attachments/assets/2d4cdd67-05b0-4974-94d5-6eb271920841)

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
- Eliminate cycles for better maintainability
- Decouple UI from logic to enhance testability
- Improve adherence to SOLID principles
- Align with layered architectural patterns

## 5. Related Views
- Deployment View - [Intelligent Flight Tracking Assistant System Deployment View](./IFTA_Deployment_View.md)

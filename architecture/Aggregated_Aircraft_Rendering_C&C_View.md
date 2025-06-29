# Aggregated Aircraft Rendering C&C View

## 1. Primary Presentation

### Key Diagrams

#### Component & Connector (C&C) View
![image](https://github.com/user-attachments/assets/1c5a44c2-846a-4f79-bf62-751233dc7e82)


---

## 2. Element Catalog

#### Component & Connector (C&C) View

## Element Catalog – Rendering & Threading Components

| Element                       | Type            | Responsibility                                                                                  |
|-------------------------------|------------------|-----------------------------------------------------------------------------------------------|
| `Timer1Timer`                 | Timer Handler    | Triggers every 500ms to call `DrawObject()`                                                   |
| `Timer2Timer`                 | Timer Handler    | Triggers every 5000ms to purge outdated aircraft data                                         |
| `Aircraft Data Store`        | Shared Variable  | Stores real-time aircraft data accessed and modified by multiple threads                      |
| `Event Handlers`             | UI Component     | Handles user interactions like drag, zoom, and aircraft selection                             |
| `OpenGL Library`             | External Library | Provides rendering capabilities for map and aircraft visualization                            |
| `TConnectionThread`          | Thread           | Establishes the TCP connection independently to prevent UI blocking                          |
| `TTCPClientRawHandleThread`  | Thread           | Receives real-time aircraft data from Raspberry Pi                                            |
| `TTCPClientSBSHandleThread`  | Thread           | Receives aircraft data from ADS-B server                                                      |
| `MainThread`                 | Thread           | Hosts the UI and orchestrates timer events and rendering                                      |
| `UI Object`                  | Component        | Represents drawn elements (airport, aircraft, overlays) on screen                            |
| `DrawObject()`                | Function         | Central drawing logic. Performs multiple visualization tasks triggered by timer or UI events. |
|                               |                  | - 1. OpenGL Rendering Setup                                                                    |
|                               |                  | - 2. Airport Display                                                                           |
|                               |                  | - 3. Map Center Point Display                                                                  |
|                               |                  | - 4. Area Visualization                                                                        |
|                               |                  | - 5. Aircraft Rendering (Region Rendering + Aggregation)                                       |
|                               |                  | - 6. Flight Path Prediction                                                                    |
|                               |                  | - 7. Aircraft Tracking                                                                          |
|                               |                  | - 8. Selected Aircraft Information Display                                                     |
|                               |                  | - 9. CPA (Closest Point of Approach) Visualization                                             |
|                               |                  | - 10. Airport Connection Lines                                                                  |
|                               |                  | - 11. Aggregation Display                                                                      |
|                               |                  | - 12. Re-Draw UI                                                                               |


---

## 3. Behavior
![image](https://github.com/user-attachments/assets/e5d394d1-03fa-4715-8839-a233e0754476)

- **Event Trigger**: Zoom out event or periodic draw event
- **Zoom threshold** (`xf >= cellDrawZoomRate`) triggers clustering mode
- Two-step process:
  1. **Grid Counting**  
     - Iterate over aircraft, calculate screen cell location
     - Count aircraft per 10×10 screen grid cell
  2. **Circle Rendering**  
     - For each populated cell, render a semi-transparent circle with aircraft count
       
### Result:
- **Before**: Thousands of individual aircraft sprites rendered → High load
- **After**: At most 100 region circles shown → Lower load, better user clarity


---

## 4. Context Diagram 

![image](https://github.com/user-attachments/assets/6fb9f489-33b2-4562-935a-189f5942eb8d)


---

## 5. Variability Guide
- N/A

---

## 6. Design Rationale
- ADR - [ADR 1 : Viewport-Based Aircraft Rendering with Aggregation Strategy](../ADRs/ADR01-viewport-and-aggregation.md)

---

## 7. Related Views
- Deployment View - [Intelligent Flight Tracking Assistant System Deployment View](./IFTA_Deployment_View.md)


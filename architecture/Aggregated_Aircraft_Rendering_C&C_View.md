# Aggregated Aircraft Rendering C&C View

The "Aggregated Aircraft Rendering C&C View" document presents the implementation view that reflects our design decisions, which were derived from <a href="../experiments/exp01-aircraft-number.md">Experiment01</a> conducted to improve <a href="../architectural-drivers.md#qa_001_01">QAR_001_01</a>


## 1. Primary Presentation

### Key Diagrams

#### Component & Connector (C&C) View
![image](https://github.com/user-attachments/assets/187c6e03-1291-40e1-a07a-2dad40ed766d)


---

## 2. Element Catalog

#### Component & Connector (C&C) View

## Element Catalog – Rendering & Threading Components

| Element                       | Type            | Responsibility                                                                                  |
|-------------------------------|------------------|-----------------------------------------------------------------------------------------------|
| `Main Thread`                 | Thread           | Handles the remote user interface; triggers rendering and purge events       |
| `Renderer`                    | Component        | Renders aircraft or circles based on zoom level                              |
| `Purge`                       | Component        | Deletes expired aircraft data from the store                                 |
| `Mouse Event Handlers`        | Component        | Handles user input (drag, zoom, right-click)                                 |
| `OpenGL Library`              | Component        | Provides graphics rendering functions                                         |
| `Aircraft Data Store`         | Shared Variable  | Stores and shares aircraft data across threads                               |
| `TTCPClientRawHandleThread`   | Thread           | Receives data from Raspberry Pi and updates data store                       |
| `TTCPClientSBSHandleThread`   | Thread           | Receives SBS-format data from ADS-B server and updates data store            |
| `DistanceThread`              | Thread           | Finds aircraft near specified airport locations                              |
| `TConnectionThread`           | Thread           | Maintains and monitors background TCP connections                            |


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


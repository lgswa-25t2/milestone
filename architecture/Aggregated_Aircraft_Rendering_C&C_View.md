# Aggregated Aircraft Rendering C&C View

## 1. Primary Presentation

### Key Diagrams

#### Component & Connector (C&C) View
![image](https://github.com/user-attachments/assets/1c5a44c2-846a-4f79-bf62-751233dc7e82)


---

## 2. Element Catalog

#### Component & Connector (C&C) View

| Element                | Type          | Responsibility                                                |
|------------------------|---------------|----------------------------------------------------------------|
| `MainThread`         | Thread      | Main UI thread               |
| `DrawObject()`         | Function      | Core drawing method, runs on timer or user event               |
| `Aircraft Data Store`  | Shared Data   | Holds live aircraft data, accessed via HashTable               |
| `TTCPClient*Thread`    | Thread        | Feeds real-time data from Raspberry Pi and ADS-B server        |
| `TConnectionThread`    | Thread        | Establishes the TCP connection in a separate thread to avoid blocking the UI thread        |

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


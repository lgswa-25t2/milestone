TODO 4가지
- C&C 뷰에 thread 추가 및 Element catalog에 new thread 추가 (jeong)
- Context Diagram, Deployment Diagram (sujin) -done

---
# Improve response time Module and C&C View

## Quality Attribute
- **Target**: Performance, Usability
- **Goal**: Improve rendering efficiency and visual clarity when displaying a large number of aircraft on screen.

## System Architecture Description
- This ADS-B Display System implements a sophisticated region-based clustering feature that enhances both user experience and system performance. When users zoom out beyond a certain threshold (cellDrawZoomRate), the system automatically switches from displaying individual aircraft icons to showing regional clusters.

## Core Features
- Adaptive Display: Automatically switches between detailed aircraft view and clustered view based on zoom level
- Grid-based Clustering: Uses a 10x10 grid system to group aircraft by screen regions
- Visual Feedback: Displays white circles with aircraft counts for each populated region
- Performance Optimization: Reduces rendering overhead when dealing with high aircraft density

---

## 1. Primary Presentation

### Key Diagrams

#### Module Dependency Diagram
![image](https://github.com/user-attachments/assets/6268ac37-59e6-4a07-a9ef-0904f99b66be)


#### Component & Connector (C&C) View
![image](https://github.com/user-attachments/assets/2bdc240e-2428-4afa-9233-b907bb7378ac)
TODO: draw.io 에 thread 추가한 것 그리기 (Jeong)

---

## 2. Element Catalog

#### Component & Connector (C&C) View

| Element                | Type          | Responsibility                                                |
|------------------------|---------------|----------------------------------------------------------------|
| `MainThread`         | Thread      | Main UI thread               |
| `DrawObject()`         | Function      | Core drawing method, runs on timer or user event               |
| `Aircraft Data Store`  | Shared Data   | Holds live aircraft data, accessed via HashTable               |
| `TTCPClient*Thread`    | Thread        | Feeds real-time data from Raspberry Pi and ADS-B server        |
| `New *Thread`    | Thread        | TODO: description        |

TODO: New *Thread 관련 추가 (Jeong)

---

## 3. Behavior
![image](https://github.com/user-attachments/assets/1e317fb1-f9c8-45ce-b2ca-53afa9f0e9c5)


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

---


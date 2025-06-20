# Module and C&C View: Improvement response time

## Quality Attribute
- **Target**: Performance, Usability
- **Goal**: Improve rendering efficiency and visual clarity when displaying a large number of aircraft on screen.

---

## 1. Primary Presentation

### Key Diagrams

#### Module Dependency Diagram
![image](https://github.com/user-attachments/assets/6268ac37-59e6-4a07-a9ef-0904f99b66be)


#### Component & Connector (C&C) View
![image](https://github.com/user-attachments/assets/2bdc240e-2428-4afa-9233-b907bb7378ac)


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

---

## 3. Behavior
![image](https://github.com/user-attachments/assets/cfcc4412-8584-4046-ab92-ad24b7789433)

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

TODO:


---

## 5. Variability Guide
- N/A

---

## 6. Design Rationale
TODO: Link to ADR
---

## 7. Related Views
TODO: **Deployment View**: Threads and data flow for TTCPClient modules (defined elsewhere)

---


## 3개의 diagram으로 지피티에게 시켜 template 에 맞게 머지해달라고 한 결과입니다.
---
### 🧭 그렇다면 뷰 이름은 어떻게 정해야 할까?
### View 이름 = [Viewtype 이름]: [기능 또는 품질 속성 중심 설명]
### 이 패턴이 가장 널리 쓰이며 명확하고 일관성 있게 문서를 구성할 수 있습니다.

## 🔹 예시 제목 (지금 상황에 맞게)
### 뷰 이름 제안	설명
### Component & Connector View: Region Clustering	Viewtype 명시 + 기능 중심
### Component & Connector View for Performance Optimization	Viewtype + 품질 속성 중심
### Behavior and C&C View: Region-Based Aircraft Aggregation	복합적인 Viewtype 사용 가능 (필요 시)
---

# Architecture View for Region Clustering Enhancement

## Quality Attribute
- **Target**: Performance, Usability
- **Goal**: Improve rendering efficiency and visual clarity when displaying a large number of aircraft on screen.

---

## 1. Primary Presentation

### Key Diagrams

#### ✅ Module Dependency Diagram
- Shows the static dependencies around the `DisplayGUI` module.
- Highlights newly added logic:
  - `DrawCircleWithNumber()` function
  - `Zoom rate` check logic

#### ✅ Component & Connector (C&C) View
- Depicts runtime interaction:
  - Main thread triggers `DrawObject()` periodically and by user input.
  - Aircraft data is read from a shared hash table and passed to OpenGL.

#### ✅ Sequence Diagram
- Represents clustering behavior when zoomed out:
  - Aircraft data grid counting
  - Circle rendering based on cell data
  - Reverts to normal mode when zoom threshold is not met

> Diagrams explicitly highlight added logic (in red) and performance-optimized flow.

---

## 2. Element Catalog

| Element                | Type          | Responsibility                                                |
|------------------------|---------------|----------------------------------------------------------------|
| `DisplayGUI`           | Component     | Main controller and drawing logic (now includes clustering)    |
| `DrawObject()`         | Function      | Core drawing method, runs on timer or user event               |
| `Aircraft Data Store`  | Shared Data   | Holds live aircraft data, accessed via HashTable               |
| `HashTable lib`        | Library       | High-speed search and iteration over aircraft list             |
| `LatLonConv`           | Library       | Converts geographic coordinates to screen coordinates          |
| `OpenGL`               | Library       | Handles rendering of aircraft, circles, and overlay text       |
| `TTCPClient*Thread`    | Thread        | Feeds real-time data from Raspberry Pi and ADS-B server        |

---

## 3. Behavior

- **Event Trigger**: Zoom out event or periodic draw event
- **Zoom threshold** (`xf >= cellDrawZoomRate`) triggers clustering mode
- Two-step process:
  1. **Grid Counting**  
     - Iterate over aircraft, calculate screen cell location
     - Count aircraft per 10×10 screen grid cell
  2. **Circle Rendering**  
     - For each populated cell, render a semi-transparent circle with aircraft count

### Result:
- **Before**: Hundreds of individual aircraft sprites rendered → High load
- **After**: At most 100 region circles shown → Lower load, better user clarity

---

## 4. Context Diagram (Simplified)

```plaintext
[User] -- Zoom/Drag --> [DisplayGUI]
               ↘︎                ↙︎
        [HashTable] ← LatLonConv → [OpenGL]
````

* User actions flow into `DisplayGUI`
* Aircraft position resolution handled by `LatLonConv`, rendered via `OpenGL`

---

## 5. Variability Guide

* `cellDrawZoomRate` is a tunable threshold for clustering activation.
* `DrawCircleWithNumber()` can be swapped for different visual styles.
* `HashTable` can be replaced with spatial data structures (e.g., QuadTree) in future.

---

## 6. Design Rationale

* **Problem**: Rendering overload and poor UX with high aircraft count
* **Solution**: Region-based aggregation reduces rendering cost and improves clarity
* **Alternatives Considered**:

  * Continue rendering all aircraft: too expensive visually and computationally
  * Server-side aggregation: not real-time and requires more infra
* **Decision**:

  * Local grid-based aggregation with OpenGL circles ensures real-time responsiveness and modularity

---

## 7. Related Views

* **Module View**: Static structure and inter-module dependencies (see Diagram 1)
* **Deployment View**: Threads and data flow for TTCPClient modules (defined elsewhere)
* **Sequence Diagram**: Runtime logic and clustering behavior path

---


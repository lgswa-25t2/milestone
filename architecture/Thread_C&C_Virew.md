# Thread C&C View

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
### Before
![image](https://github.com/user-attachments/assets/b8778a4f-d6b8-4717-8ac6-00268e1ab816)


The user clicks a button → TForm1 calls methods directly on IdTCPClientRaw.
TForm1 also resumes the TCPClientRawHandleThread.
Because all actions run in the UI thread, the interface may become unresponsive while waiting for network operations to complete.


### After
![image](https://github.com/user-attachments/assets/2cd25197-daf0-4c30-970e-53bade5d217a)

The user still clicks the button, but TForm1 spawns a ConnectionThread1.
ConnectionThread1 performs the connection by calling Connect on IdTCPClientRaw.
When the connection is successful, OnConnectionComplete is triggered.
Only then is the TCPClientRawHandleThread resumed and the input is processed asynchronously.
This keeps the UI thread free and responsive.

### Conclusion:
The new design improves system architecture by introducing asynchronous connection handling,
reducing UI thread load, and increasing maintainability and responsiveness. 

---

## 4. Context Diagram 


---

## 5. Variability Guide
- N/A

---

## 6. Design Rationale
- 
---

## 7. Related Views
- Deployment View - [Intelligent Flight Tracking Assistant System Deployment View](./IFTA_Deployment_View.md)

---


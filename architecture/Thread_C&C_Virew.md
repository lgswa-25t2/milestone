# Separation of TConnectionThread Component & Connector View

## 1. Primary Presentation

### Key Diagrams

#### Component & Connector (C&C) View
![image](https://github.com/user-attachments/assets/05bd718a-952e-4a37-a8a1-b9064eba0fe4)


---

## 2. Element Catalog

#### Component & Connector (C&C) View

| Element                | Type          | Responsibility                                                |
|------------------------|---------------|----------------------------------------------------------------|
| `MainThread`         | Thread      | Main UI thread               |
| `UI Object`         | Component      | Represents visual components and interface elements rendered on screen               |
| `Timer1Timer`         | Component      | Triggers every 500ms to call DrawObject() and handle timeout events               |
| `Timer2Timer`         | Component      | Triggers every 5000ms to purge and clean up outdated data from the aircraft DB               |
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

## 4. Design Rationale
### Rationale
Originally, the connection logic was executed on the main UI thread, causing the UI to freeze for several seconds while connecting. This led to poor responsiveness and a negative user experience. The goal was to improve perceived performance and usability.

### Alternative Considered
**Shorter timeout (Tactic: Bounded Execution Time) :**
Reduces delay but increases failure rate in unstable networks.

**Progress popup (Tactic: User Feedback) :**
Informs the user but does not resolve the underlying blocking issue.

**Introduce concurrency (Selected) :**
Using a background thread separates the blocking task from the UI.

### Decision
We introduced TConnectionThread to handle network connections off the UI thread, improving system responsiveness.

### Result
The "Connect" button now responds within 1 second, and the UI remains interactive during connection attempts. This change improves response time and user satisfaction without affecting success rate.

---

## 5. Related Views
- Deployment View - [Intelligent Flight Tracking Assistant System Deployment View](./IFTA_Deployment_View.md)

---


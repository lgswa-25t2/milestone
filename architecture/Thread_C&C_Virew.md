# Asynchronous Network Connection through Separation of TConnectionThread Component & Connector View

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
- Rationale: To resolve UI blocking issues and improve user experience.
- Alternative Considered: Timer-based polling was evaluated but found inefficient in terms of resource usage.
- Decision: Separated network connection from the main UI thread by introducing TConnectionThread.
- Result: Ensured 100% UI responsiveness and reduced connection time.

---

## 5. Related Views
- Deployment View - [Intelligent Flight Tracking Assistant System Deployment View](./IFTA_Deployment_View.md)

---


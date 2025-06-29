# Intelligent Flight Tracking Assistant System - Deployment View
## 1. Primary Presentation
The diagram illustrates Deployment Diagram for Intelligent Flight Tracking Assistant System.

### Key Diagrams
![image](https://github.com/user-attachments/assets/4dc56cfe-f4a7-4f8d-8180-e826222dfd2b)

![image](https://github.com/user-attachments/assets/b84a61bb-f680-4b8c-93d0-63219dc86481)


---

## 2. Element Catalog


| Element                        | Type           | Responsibility                                                                 |
|-------------------------------|----------------|--------------------------------------------------------------------------------|
| `Raspberry Pi ADS-B Station`  | Hardware Node  | Collects raw 1090MHz ADS-B signals using RTL-SDR and streams over TCP         |
| `dump1090`                    | Software       | Decodes raw signals into aircraft data formats (raw & SBS)                    |
| `TCP Server (:30002/:5002)`   | Component      | Serves decoded aircraft data to clients over TCP                              |
| `Windows Client PC`           | Hardware Node  | Visualizes real-time aircraft data with clustering and rendering              |
| `C++ GUI App`                 | Software       | Displays map, aircraft tracks, performs clustering and integration            |
| `Python Module`               | Component      | Provides scripting or analytics integration in GUI app                        |
| `Map Services (Google/SkyVector)` | External Service | Provides map tile data via HTTPS                                           |
| `ADS-B Hub / Metadata APIs`   | External Service | Supplies additional aircraft metadata                                         |
| `Google BigQuery`             | Cloud Storage  | Stores and analyzes historical flight data                                    |

---

## 3. Behavior
- N/A

---

## 4. Design Rationale

- N/A
---

## 5. Related Views
- N/A

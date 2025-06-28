# Intelligent Flight Tracking Assistant System Deployment View

## Deployment Diagram
![image](https://github.com/user-attachments/assets/4dc56cfe-f4a7-4f8d-8180-e826222dfd2b)



![image](https://github.com/user-attachments/assets/932df633-aca1-40cb-813b-5542d78750c8)

---

### Physical Architecture

#### Raspberry Pi ADS-B Station (Data Collection Node)

* **Hardware**: ARM-based microcomputer with RTL-SDR USB dongle
* **Software**: dump1090 ADS-B decoder, TCP server
* **Role**: Receives 1090MHz aircraft signals and streams data to the network

#### Windows Client PC (Data Visualization Node)

* **Hardware**: x64 workstation with dedicated graphics card
* **Software**: C++ based GUI application with Python integration
* **Role**: Displays real-time map, performs clustering, and integrates with cloud services

#### Internet Services (External Service Node)

* **Map Services**: Google Maps, SkyVector aviation charts
* **Data Services**: ADS-B Hub, aircraft metadata APIs
* **Cloud Storage**: Google BigQuery data warehouse

---

### Network Communication

* **TCP :30002**: Raw ADS-B data stream
* **TCP :5002**: SBS (BaseStation) format standard data
* **HTTP/HTTPS**: Map tiles, API requests, cloud uploads

---

### Key Characteristics

* **Distributed Processing**: Separation of data collection and visualization
* **Real-time Streaming**: Minimal latency
* **Cloud Integration**: Data analytics with BigQuery
* **Scalability**: Supports multiple map sources and clustering capabilities

---

### Deployment Units

Each node is packaged as an **independently deployable unit**, enabling easier system maintenance and upgrades.


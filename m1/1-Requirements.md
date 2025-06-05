# Requirements

This document contains Functional requirements and Quality attribute requirements.

## Functional Requirements

Derived from features in Project Description documents.

| ID       | Group                | Description                                                  | Feature type |
| -------- | -------------------- | ------------------------------------------------------------ | ------------ |
| IFTA_001 | Metadata             | Look up aircraft information (e.g., Airline)                 | Mandatory    |
| IFTA_002 | Metadata             | Look up route information                                    | Mandatory    |
| IFTA_003 | Metadata             | Determine aircraft point of origin and destination           | Mandatory    |
| IFTA_004 | Metadata             | Use APIs and pull information (e.g., https://vrs-standing-data.adsb.lol/ ) | Mandatory    |
| IFTA_005 | Time series Analysis | Track history - Flight tracking of time and location         | Mandatory    |
| IFTA_006 | Time series Analysis | Know age of track (drop after 30 seconds)                    | Mandatory    |
| IFTA_007 | UI                   | Improve the look and user experience with the user interface | Mandatory    |
| IFTA_008 | UI                   | Update map tiles                                             | Mandatory    |
| IFTA_009 | UI                   | Plot airports                                                | Mandatory    |
| IFTA_010 | UI                   | Modify aircraft icons and leaders                            | Mandatory    |
| IFTA_500 | Safety Analysis      | Collision avoidance - Assess aircraft within proximity to each other | Desired      |
| IFTA_501 | Safety Analysis      | Compare contrast a flight’s SBS or ADS-B data with planned route | Desired      |
| IFTA_502 | Safety Analysis      | Analyze aircraft flight profile for anomalies (e.g., flying to the wrong airport) Is the flight deviating from the flight plan? | Desired      |
| IFTA_503 | Time series Analysis | While receiving and recording data, play back tracks (Playback at 2x at 3x speed) by moving a mouse cursor | Desired      |
| IFTA_504 | Simulation           | Dead reckoning - plot tracks now or where they should be based upon constant velocity and altitude (parametric fit) | Desired      |

\* Desired features are given an ID after 500.




## Quality Attribute Requirements 

Derived from Section. *System and Software Quality Attributes* (**SSQA**) & Section. *Demo Scoring* (**DS**) in project description.

- Performance
  - [SSQA] The system provides **quick responses** to user interface actions. It includes system response time when changing aircraft focus - retrieving and rendering metadata on screen. This is both measurable (in milliseconds) and observable (perceived delay). Additionally, performance depends on the number of items being monitored, as increased load may impact responsiveness.
  - [DS] *Response time* - Response time for the remote user interface application, Raspberry Pi, and external database when actions are initiated by the user in the remote user interface. Examples include: Timely respond when the data load scales, Timely respond when executing added analytical features
- Resiliency
  - [SSQA] The system is able to handle and **recover from faults** or disruptions gracefully. It includes how the GUI reacts when the Raspberry Pi connection is lost (e.g., Wi-Fi turned off)—ideally, the application should detect the disconnection, alert the user, and attempt reconnection without crashing.
  - [DS] *Fault detection and error handling* - Examples include: How does the GUI application react when it loses connection with the Raspberry Pi? (Test turning off wifi), How does the system react when the Raspberry Pi loses connection with the ADS receiver? (Test pulling the USB cable)
- Extensibility
  - [SSQA] The system can **easily be enhanced with new features** or modified to accommodate evolving requirements. For a user interface, this includes the ability to integrate new functionalities such as identifying unregistered aircraft or detecting deviations from registered flight paths. A highly extensible system allows these capabilities to be added with minimal impact on existing code, supporting modular development and future scalability.
  - [DS] *Architecture supports new requirements or enhancements* - Examples include: Are key functionalities abstracted behind interfaces?, Can new behavior be injected without modifying existing code?, Are dependencies explicitly managed?
- Modifiability
  - [SSQA] A developer can **easily switch** the user interface application **to use a different map provider**. Switching the map component should be done with minimal code updates, low risk of introducing bugs, and without impacting unrelated parts of the system.
  - [DS] *Map Support* - The GUI application should support multiple map data types and different levels of scale. Examples include: Support map data from different map providers, Support zoom in and zoom out features
- Maintainability
  - [SSQA] The software system can be **easily understood, corrected, improved, and adapted** over time. For a user interface, the goal is not to exhibit defects or errors. An essential element to achieve this goal includes a codebase that is clean, well-documented, has good test coverage, and is structured in a way that simplifies debugging and enhancements.
- Usability
  - [DS] *Remote User Interface* - Real time display of maps and aircraft tracks, Real time display of “hooked” aircraft, Display aircraft data and other display data, Implement click buttons (or similar feature) to remotely connect to the Raspberry Pi Flight Tracker, ADS-B Hub, recorded files, or other data files, Implement slide bars or similar features to promote interaction of flight track data on the map visually, Display polygons and show only aircraft that are within the defined waypoints on the map (e.g., square or irregular shape following an highway)
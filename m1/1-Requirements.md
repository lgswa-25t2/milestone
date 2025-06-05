# Requirements

This document contains Functional requirements and Quality attribute requirements.

## Functional Requirements

Derived from features in Project Description documents.

| ID          | Group                | Description                                                  | Feature type |
| ----------- | -------------------- | ------------------------------------------------------------ | ------------ |
| IFTA_FR_001 | Metadata             | Look up aircraft information (e.g., Airline)                 | Mandatory    |
| IFTA_FR_002 | Metadata             | Look up route information                                    | Mandatory    |
| IFTA_FR_003 | Metadata             | Determine aircraft point of origin and destination           | Mandatory    |
| IFTA_FR_004 | Metadata             | Use APIs and pull information (e.g., https://vrs-standing-data.adsb.lol/ ) | Mandatory    |
| IFTA_FR_005 | Time series Analysis | Track history - Flight tracking of time and location         | Mandatory    |
| IFTA_FR_006 | Time series Analysis | Know age of track (drop after 30 seconds)                    | Mandatory    |
| IFTA_FR_007 | UI                   | Improve the look and user experience with the user interface | Mandatory    |
| IFTA_FR_008 | UI                   | Update map tiles                                             | Mandatory    |
| IFTA_FR_009 | UI                   | Plot airports                                                | Mandatory    |
| IFTA_FR_010 | UI                   | Modify aircraft icons and leaders                            | Mandatory    |
| IFTA_FR_101 | Safety Analysis      | Collision avoidance - Assess aircraft within proximity to each other | Desired      |
| IFTA_FR_102 | Safety Analysis      | Compare contrast a flight’s SBS or ADS-B data with planned route | Desired      |
| IFTA_FR_103 | Safety Analysis      | Analyze aircraft flight profile for anomalies (e.g., flying to the wrong airport) Is the flight deviating from the flight plan? | Desired      |
| IFTA_FR_104 | Time series Analysis | While receiving and recording data, play back tracks (Playback at 2x at 3x speed) by moving a mouse cursor | Desired      |
| IFTA_FR_105 | Simulation           | Dead reckoning - plot tracks now or where they should be based upon constant velocity and altitude (parametric fit) | Desired      |

\* Desired features are given an ID after 101.




## Quality Attribute Requirements 

Derived from Section. *System and Software Quality Attributes* (**SSQA**) & Section. *Demo Scoring* (**DS**) in project description.

Each item can be added or changed and can be specified through discussion with sponsor.

| ID           | Description                                                  | Source       |
| ------------ | ------------------------------------------------------------ | ------------ |
| IFTA_QAR_001 | The system provides quick responses to user interface actions. | SSQA 1, DS 1 |
| IFTA_QAR_002 | The system is able to handle and recover from faults or disruptions gracefully. | SSQA 2, DS 2 |
| IFTA_QAR_003 | The system can easily be added or modified with new features | SSQA 3, DS 3 |
| IFTA_QAR_004 | The GUI application should support multiple map data types.  | SSQA 4, DS 4 |
| IFTA_QAR_005 | The system can be easily understood, corrected, improved, and adapted. | SSQA 5       |
| IFTA_QAR_006 | Improve the look and user experience with the user interface. | DS 5         |

- [SSQA 1] The system provides **quick responses** to user interface actions. It includes system response time when changing aircraft focus - retrieving and rendering metadata on screen. This is both measurable (in milliseconds) and observable (perceived delay). Additionally, performance depends on the number of items being monitored, as increased load may impact responsiveness.
- [SSQA 2] The system is able to handle and **recover from faults** or disruptions gracefully. It includes how the GUI reacts when the Raspberry Pi connection is lost (e.g., Wi-Fi turned off)—ideally, the application should detect the disconnection, alert the user, and attempt reconnection without crashing.
- [SSQA 3] The system can **easily be enhanced with new features** or modified to accommodate evolving requirements. For a user interface, this includes the ability to integrate new functionalities such as identifying unregistered aircraft or detecting deviations from registered flight paths. A highly extensible system allows these capabilities to be added with minimal impact on existing code, supporting modular development and future scalability.
- [SSQA 4] A developer can **easily switch** the user interface application **to use a different map provider**. Switching the map component should be done with minimal code updates, low risk of introducing bugs, and without impacting unrelated parts of the system.
- [SSQA 5] The software system can be **easily understood, corrected, improved, and adapted** over time. For a user interface, the goal is not to exhibit defects or errors. An essential element to achieve this goal includes a codebase that is clean, well-documented, has good test coverage, and is structured in a way that simplifies debugging and enhancements.
- [DS 1] *Response time* - Response time for the remote user interface application, Raspberry Pi, and external database when actions are initiated by the user in the remote user interface. Examples include: Timely respond when the data load scales, Timely respond when executing added analytical features

- [DS 2] *Fault detection and error handling* - Examples include: How does the GUI application react when it loses connection with the Raspberry Pi? (Test turning off wifi), How does the system react when the Raspberry Pi loses connection with the ADS receiver? (Test pulling the USB cable)

- [DS 3] *Architecture supports new requirements or enhancements* - Examples include: Are key functionalities abstracted behind interfaces?, Can new behavior be injected without modifying existing code?, Are dependencies explicitly managed?

- [DS 4] *Map Support* - The GUI application should support multiple map data types and different levels of scale. Examples include: Support map data from different map providers, Support zoom in and zoom out features

- [DS 5] *Remote User Interface* - Real time display of maps and aircraft tracks, Real time display of “hooked” aircraft, Display aircraft data and other display data, Implement click buttons (or similar feature) to remotely connect to the Raspberry Pi Flight Tracker, ADS-B Hub, recorded files, or other data files, Implement slide bars or similar features to promote interaction of flight track data on the map visually, Display polygons and show only aircraft that are within the defined waypoints on the map (e.g., square or irregular shape following an highway)
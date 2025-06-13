# Requirements

This document contains Functional requirements and Quality attribute requirements.

## Functional Requirements

Derived from features in Project Description documents.

| ID       | Group                | Brief                                 | Description                                                  |
| -------- | -------------------- | ------------------------------------- | ------------------------------------------------------------ |
| FR_01_01 | Metadata             | Aircraft information lookup           | The system shall be able to retrieve aircraft information (e.g., airline, aircraft type etc.) in real time based on ICAO address |
| FR_01_02 | Metadata             | Route information lookup              | The system shall be able to query and display flight route data (e.g., airways, waypoints etc) |
| FR_01_03 | Metadata             | Origin and Destination identification | The system shall be able to identify and provide to the user the origin and destination information (e.g. Departure/Destination Airport Codes) of each aircraft |
| FR_02_01 | Time series Analysis | Flight history tracking               | Saves the location and time information of the airplane in order and displays the data on the screen in an appropriate way |
| FR_02_02 | Time series Analysis | Know age of track                     | After receiving the flight information, we check the validity of the data and delete it if it is determined to be invalid |
| FR_02_03 | Time series Analysis | Track playback                        | The system shall be capable of recording received aircraft track data and replaying it at 1x, 2x or 3x speed for selected flights or time ranges |
| FR_02_04 | Time series Analysis | Track simulation                      | The system shall be able to perform flight simulation with arrival destination information |
| FR_02_05 | Time series Analysis | Dead reckoning                        | If real-time data is temporarily interrupted or delayed, estimate the aircraft's current position based on the last position, speed and altitude and display it on a map |
| FR_03_01 | UI                   | Improved UI/UX                        | The systam shll better ux: Re-organize information and buttons & modify font, alignment, checkbox, button in right panel |
| FR_03_02 | UI                   | Improved UI/UX                        | Icon categorization by aircraft typel                        |
| FR_03_03 | UI                   | Improved UI/UX                        | Configure icon colors for each map to improve visual clarity |
| FR_03_04 | UI                   | Updated Map tiles                     | The system shall(may) adjust resolution by zoom-in / zoom-out. |
| FR_03_05 | UI                   | Airport plotting                      | The system shall display major airports (according to IATA/ICAO standards) on the map as icons or symbols |
| FR_03_06 | UI                   | Aircraft icons and leaders            | Icons and leaders indicating the direction of movement of the aircraft must be visually displayed on the map |
| FR_03_07 | UI                   | Area polygons                         | The system shall display polygons and show only aircraft that are within the defined waypoints on the map |
| FR_04_01 | Safety Analysis      | Collision avoidance                   | The system must detect two aircraft within 1 nm (nautical mile) or within 5 nm from the airport |
| FR_04_02 | Safety Analysis      | Route comparison                      | The system must display the current ADS-B / SBS position and predefined flight plan path of the selected plane |
| FR_04_03 | Safety Analysis      | Flight profile normaly detection      | The system should be able to detect any deviation from the normal flight trajectory (wrong airport approach, reverse flight, unregistered flight) by analyzing the aircraft's path, direction, speed and destination |
| FR_04_04 | Safety Analysis      | Flight plan deviation analysis        | The system must compare the flight plan route with the real-time route to detect whether the flight is more than 5 nm off the route |
| FR_05_01 | Record & Playback    | Record                                | The system can write aircraft's data to local or external file. (BigQuery) |
| FR_05_02 | Record & Playback    | Playback                              | The system can read SBS records from local, and the recorded aircraft position data is displayed in UI. |




## Quality Attribute Requirements 

Derived from Section. *System and Software Quality Attributes* (**SSQA**) & Section. *Demo Scoring* (**DS**) in project description.

Each item can be added or changed and can be specified through discussion with sponsor.

| ID      | Description                                                  | Source       |
| ------- | ------------------------------------------------------------ | ------------ |
| QAR_001 | The system provides quick responses to user interface actions. | SSQA 1, DS 1 |
| QAR_002 | The system is able to handle and recover from faults or disruptions gracefully. | SSQA 2, DS 2 |
| QAR_003 | The system can easily be added or modified with new features | SSQA 3, DS 3 |
| QAR_004 | The GUI application should support multiple map data types.  | SSQA 4, DS 4 |
| QAR_005 | The system can be easily understood, corrected, improved, and adapted. | SSQA 5       |
| QAR_006 | Improve the look and user experience with the user interface. | DS 5         |

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

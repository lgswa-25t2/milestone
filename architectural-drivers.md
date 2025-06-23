# Architectural Drivers

This document outlines all the factors that affect system architecture, defining key QA elements and providing a basis for design decisions.



## Stakeholders

| Role          | Name                    | Concerns                     |
| ------------- | ----------------------- | ---------------------------- |
| Product Owner | Solvit Inc.             | Features, Quality attributes |
| Mentor        | Paulo Merson, Matt Bass | Quality attributes           |
| Dev team      | Team #2 Challenger      | Rapid development, Features  |



## Constraints

- Business Constraints
  - 7 people in the development
  - 5 weeks development period
  - In addition to development, demo and presentation preparation are required.

- Technical Constraints
  - Use C++ for development
  - Since this is a Windows application using VCL (Visual Component Library), the IDE is set to RAD Studio.
  - DB must use Google BigQuery.
  - An antenna is Raspberry Pi 5.



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
| FR_03_01 | UI                   | Improved UI/UX                        | The systam shall support UX : Re-organize information and buttons & modify font, alignment, checkbox, button in right panel |
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




## Quality Attributes Requirements

Derived from Section. *System and Software Quality Attributes* & Section. *Demo Scoring* in project description. Each item can be added or changed and can be specified through discussion with sponsor.

In order to prioritize, ***I*** and ***R*** scores were given according to the following criteria.

- ***I*** (Business importance) - The score assigned in the demo scoring was H if it was 30 points, M if it was 20 points, and L if it was 10 points or less.
- ***R*** (Technical Risk) - Since all members are developers, we wrote subjectively based on our own development experience.

| ID          | Summary of Scenario                                          | QA Type         | I        | R        |
| ----------- | ------------------------------------------------------------ | --------------- | --------------- | --------------- |
| [QAR_001_01](#qa_001_01) | UI responds immediately to user interaction when click air-craft and the UI is operating with raw connect mode or SBS connect mode | Performance     | H    | H    |
| [QAR_001_02](#qa_001_02) | When the UI is operating with raw connect mode or SBS connect mode, it immediately responds to user interaction by manipulating the menu or control panel. | Performance     | H    | H    |
| [QAR_002_01](#qa_002_01) | The system detects network failure when the UI is operating with SBS connect mode | Resiliency      | H     | M     |
| [QAR_002_02](#qa_002_02) | The system detects disconnection of USB antenna in raspberry pi when the UI is operating with SBS connect mode | Resiliency | H | M |
| [QAR_003](#qa_003) | The system shall allow developers to add a deviation detection feature | Extensibility   | H  | L  |
| [QAR_004](#qa_004) | The system shall allow developers to add new aircraft identification modules | Extensibility   | H  | L  |
| [QAR_005](#qa_005) | The system shall allow developers to integrate a new map provider into the user interface with minimal code changes, low risk of introducing bugs, and without affecting unrelated parts of the system | Modifiability   | M  | M  |

### Six parts of each scenarios

#### QA_001_01

- Source - User
- Stimulus - right click air-craft in user interface
- Artifact - Remote User Interface (RUI)
- Environment - Normal raw connect or SBS connect mode, The system is tracking 5000 aircrafts simultaneously
- Response - Analytical feature are displayed promptly
- Response Measure - Analytical feature display latency up to 1 second after user action

#### QA_001_02

- Source - User
- Stimulus - Toggle Display Map checkbox in user interface
- Artifact - Remote User Interface (RUI)
- Environment - Normal raw connect or SBS connect mode, The system is tracking 5000 aircrafts simultaneously
- Response - UI responds to user interaction
- Response Measure - Map toggle interaction response ≤ 150 milliseconds

#### QA_002_01

- Source - User
- Stimulus - turn off system wifi
- Artifact - System
- Environment - Normal SBS connect mode, the system is tracking ADS-B datasets
- Response - System detects network failure and notifies the user
- Response Measure - System detects disconnection within 1 second and notifies the user within 1 second

#### QA_002_02

- Source - User
- Stimulus - disconnect USB cable during runtime
- Artifact - System
- Environment - Normal SBS connect mode, the system is tracking ADS-B datasets
- Response - System detects failure conditions (e.g., disconnection) and notifies the user
- Response Measure - System detects disconnection within 1 second and notifies the user within 1 second

#### QA_003

- Source - Solvit or Project leader
- Stimulus - A requirement is raised to add a feature that detects deviations from registered flight paths
- Artifact - Flight data analysis module and user interface
- Environment - During normal development
- Response - The new functionality is integrated
- Response Measure - Feature is deployed within 3 person days without regressions in existing functionality

#### QA_004

- Source - Solvit or Project leader
- Stimulus - A requirement is raised to add a feature for identifying unregistered aircraft
- Artifact - Aircraft identification database, real-time traffic analysis module, UI display components
- Environment - During normal development
- Response - Unregistered aircraft are visually flagged in the UI and recorded in system logs
- Response Measure - Implemented and tested within 3 person days

#### QA_005

- Source - Developer
- Stimulus - Add a new map provider to the system
- Artifact - Map rendering module in the Remote User Interface (RUI)
- Environment - During iterative development or feature expansion
- Response - The new map provider integrates seamlessly without affecting existing components
- Response Measure - Integration completed in under 4 person-hours, no unintended side effects observed



## Risk assessment

- Likelihood (L): Probability that the risk will occur
- Impact (I): Level of damage if the risk occurs

### Technical Risk Assessment

| ID   | Description                                                  | L    | I    | Mitigation Strategy                                          | Link                                                         |
| ---- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| TR_1 | System may not be updated normally due to large volume of aircraft data is received by the ADS-B server in a short period of time. | H    | H    | consider Manage sampling rate to adjust the volume of aircraft data. | [Exp 1](./experiments/exp01-aircraft-number.md) , [Exp 2](./experiments/exp02-ingestion-rate.md) |
| TR_2 | We need to apply multi-thread in program, but the VCL framework does not support multi thread. If background threads directly access or modify UI components, it may result in application instability, race conditions, or unexpected crashes. | M    | L    | Separate business logic from UI logic, and run the UI thread and the data processing thread independently. | [Exp 7](./experiments/exp07-multi-thread.md)                 |
| TR_3 | The Raspberry Pi can fail for various reasons (e.g. crash, out of memory), and it is unclear whether it provides the cause of failure depending on the situation. | H    | L    | Modify the Raspberry Pi to report its status information.    | [Exp 6](./experiments/exp06-pi-operation.md)                 |
| TR_4 | UI, network, and data processing are tightly coupled, making it unclear where to insert the deviation detection logic. | H    | H    | Separation of UI, network, and data processing components.   | Planned draw diagrams                                        |

### Non-technical Risk Assessment

Because there is no part that is linked to other parts of the documents, items didn't have an unnecessary ID.

| Description                                                  | Cause                                                        | L    | I    | Mitigation Strategy                                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| Some requirement documents lack clarity, making analysis difficult. Clarification is only possible through assumptions or direct contact with the project sponsor. unclear requirements can lead to rework, misalignment, and missed goals. | Ambiguous documents and vague requirements                   | H    | H    | Clarify ambiguous requirements by maintaining continuous, question-and-answer-based communication with Solvelt throughout the project lifecycle.Seek solutions via regular meetings with mentors and expedite requirement confirmation by suggesting common assumptions. |
| Communication within the team is limited to English due to diverse nationalities. | Different native languages                                   | H    | H    | Leverage visual collaboration tools such as Miro, along with AI-powered translation tools, to facilitate effective communication across language barriers. |
| Communication is limited to Solvelt and email, resulting in long delays in receiving responses. | Lack of proper decision-making channels                      | M    | H    | Proactively reach out to mentors and maintain regular contact with Solvelt |
| LG company PC security tools hinder development and test environment setup. | Network blocks and data transfer restrictions by security software | M    | M    | Use alternative devices (e.g., mobile), request exception handling from IT security team |
| The project duration is limited to approximately 4 weeks, with additional assignments affecting overall work efforts. | Short project timeline and parallel other tasks(Assignment, Quiz). | H    | H    | Focus on essential features, utilize planning tools and AI assistance for efficiency. |


<!--
## Potential Quality Attribute Trade-offs

Based on the defined Quality Attributes (QAs), the following trade-offs may arise due to conflicting architectural goals:

#### 1. Performance vs. Modifiability / Extensibility

*QAs Involved*

- `QA_001`: *UI responds immediately to user interaction* (Performance)
- `QA_003 / 004 / 005`: *Ease of adding new features such as deviation detection, unregistered aircraft identification, and new map providers* (Extensibility / Modifiability)

*Potential Conflict*

- Designing for modularity and flexibility often introduces layers of abstraction or interface boundaries, which can lead to increased data processing overhead and reduced performance.
- To improve performance, techniques such as caching, multithreading, and data prefetching can be applied. However, these techniques often introduce **state** into the system or cause **race conditions**, making the system harder to understand and modify.

*Decision*

- In case of conflict between performance and extensibility, we prioritized performance for core real-time features while isolating extension modules to minimize impact.

#### 2. Performance vs. Resiliency

*QAs Involved*

- `QA_001` (Performance)
- `QA_002`: *Detects and recovers from failure conditions* (Resiliency)

*Potential Conflict*

- Adding frequent monitoring (e.g., heartbeat checks, retry loops) can introduce extra system load, potentially impacting real-time responsiveness.
- Balancing proactive failure detection with minimal overhead is essential.

*Decision*

- We prioritized performance for time-critical UI interactions, while applying lightweight monitoring mechanisms to minimize overhead.

#### Summary Table

| QA 1        | QA 2          | Reason for Trade-off                                         |
| ----------- | ------------- | ------------------------------------------------------------ |
| Performance | Modifiability | Modular structure increases overhead; tight coupling boosts speed |
| Performance | Resiliency    | Monitoring and recovery add load and complexity              |
-->

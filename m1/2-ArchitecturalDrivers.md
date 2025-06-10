# Architectural Drivers

This document outlines all the factors that affect system architecture, defining key QA elements and providing a basis for design decisions.

## Stakeholders

| Role          | Name                    | Concerns                     |
| ------------- | ----------------------- | ---------------------------- |
| Product Owner | Solvit Inc.             | Features, Quality attributes |
| Mentor        | Paulo Merson, Matt Bass | Quality attributes           |
| Dev team      | Team #2 Challenger      | Rapid development, Features  |



## Requirements

Please refer to [Requirements](./1-Requirements.md).



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




## Define Quality Attributes

The Quality Attributes selected based on the [Quality attribute requirements](./1-Requirements.md#quality-attribute-requirements) are as follows.

| ID          | Summary of Scenario                                          | QA Type         | Req. ID      |
| ----------- | ------------------------------------------------------------ | --------------- | ------------ |
| IFTA_QA_001_01 | UI responds immediately to user interaction when click air-craft  | Performance     | IFTA_QAR_001 |
| IFTA_QA_001_02 | UI responds immediately to user interaction during operating menu or control panel  | Performance     | IFTA_QAR_001 |
| IFTA_QA_002 | The system detects/restores failure conditions               | Resiliency      | IFTA_QAR_002 |
| IFTA_QA_003 | The system shall allow developers to add a deviation detection feature | Extensibility   | IFTA_QAR_003 |
| IFTA_QA_004 | The system shall allow developers to add new aircraft identification modules | Extensibility   | IFTA_QAR_004 |
| IFTA_QA_005 | The system shall allow developers to integrate a new map provider into the user interface with minimal code changes, low risk of introducing bugs, and without affecting unrelated parts of the system | Modifiability   | IFTA_QAR_005 |
| IFTA_QA_006 | When system errors occur, the system shall display clear error notifications         | Usability       | IFTA_QAR_006 |



## Quality Attribute scenarios

Quality attribute scenarios were written for each requirement of the defined QA list.

### IFTA_QA_001_01

- Source - User actions in the remote user interface
- Stimulus - right click air-craft
- Artifact - User interface application
- Environment - Runtime, the system is tracking 5000+ aircrafts simultaneously
- Response - UI responds immediately to user interaction, analytical feature are displayed promptly
- Response Measure
  - Aircraft click response time ≤ 100 (TBD) milliseconds
  - Analytical feature display latency ≤ 1 second after user action

**Related approach** : refer to [Approach 01](./approachs/approach01.md)

### IFTA_QA_001_02

- Source - User actions in the remote user interface
- Stimulus - operating menu or control panel
- Artifact - User interface application
- Environment - Runtime, the system is tracking 5000+ aircrafts simultaneously
- Response - UI responds immediately to user interaction
- Response Measure
  - Menu/control panel interaction response ≤ 150 (TBD) milliseconds

**Related approach** : refer to [Approach 01](./approachs/approach01.md)


### IFTA_QA_002

- Source - User
- Stimulus - turn off Wifi or disconnect USB cable during runtime
- Artifact - User interface application
- Environment - Runtime, the system is tracking ADS-B datasets
- Response
  - System detects failure conditions (e.g., disconnection)
  - User is notified with a clear UI message (e.g., “Lost connection to Raspberry Pi”)
- Response Measure
  - System detects disconnection within ≤ 1 second
  - User notified of fault within ≤ 1 second.

**Related approach** : refer to [Approach 02](./approachs/approach02.md)

### IFTA_QA_003

- Source - Solvit or Project leader
- Stimulus - A requirement is raised to add a feature that detects deviations from registered flight paths
- Artifact - Flight data analysis module and user interface
- Environment - During normal development
- Response
  - The new functionality is integrated
- Response Measure
  - Feature is deployed within 3 person days without regressions in existing functionality

**Related approach** : refer to [Approach 03](./approachs/approach03.md)



### IFTA_QA_004

- Source - Solvit or Project leader
- Stimulus - A requirement is raised to add a feature for identifying unregistered aircraft
- Artifact - Aircraft identification database, real-time traffic analysis module, UI display components
- Environment - During normal development
- Response
  - Unregistered aircraft are visually flagged in the UI and recorded in system logs
  - The feature is implemented without altering existing aircraft tracking or display logic
- Response Measure
  - Feature added as separate module preserving existing modules
  - Implemented and tested within 3 person days

**Related approach** : refer to [Approach 04](./approachs/approach04.md)



### IFTA_QA_005

- Source - Developer
- Stimulus - Add a new map provider to the system
- Artifact - Map rendering module in the Remote User Interface (RUI)
- Environment - During iterative development or feature expansion
- Response - The new map provider integrates seamlessly without affecting existing components
- Response Measure - Integration completed in under 4 person-hours, no unintended side effects observed

**Related approach** : refer to [Approach 05](./approachs/approach05.md)


### IFTA_QA_006

- Source - Internal system components or external dependencies
- Stimulus - An unexpected error occurs due to a system failure or external service disruption
- Artifact - Remote User Interface (RUI)
- Environment - Error occuring during operation
- Response - The system immediately notifies the user of the issue in a clear and non-technical manner
- Response Measure - Error is informed to user within 1 second of the failure

**Related approach** : refer to [Approach 09](./approachs/approach09.md)



## QA priority

### Utility tree

- **Business importance** - The score assigned in the demo scoring was H if it was 30 points, M if it was 20 points, and L if it was 10 points or less.
- **Technical Risk** - Since all members are developers, we wrote subjectively based on our own development experience.

| ID   | Scenario                                                     | Type            | Business Importance | Technical Risk |
| ---- | ------------------------------------------------------------ | --------------- | ------------------- | -------------- |
| 1_1  | UI responds immediately to user interaction when click air-craft               | Performance     | H                   | H              |
| 1_2  | UI responds immediately to user interaction during operating menu or control panel | Performance     | H                   | H              |
| 2    | The system detects/restores failure conditions               | Resiliency      | H                   | M              |
| 3    | The system shall allow developers to add a deviation detection feature | Extensibility   | H                   | H              |
| 4    | The system shall allow developers to add new aircraft identification modules | Extensibility   | H                   | M              |
| 5    | The system should allow developers to integrate a new map provider into the user interface with minimal code changes, low risk of introducing bugs, and without affecting unrelated parts of the system | Modifiability   | M                   | H              |
| 6    | When system errors occur, the system shall display clear error notifications  | Usability       | L                   | L              |

### Potential Quality Attribute Trade-offs

Based on the defined Quality Attributes (QAs), the following trade-offs may arise due to conflicting architectural goals:

#### 1. Performance vs. Modifiability / Extensibility

**QAs Involved**  

- `IFTA_QA_001`: *UI responds immediately to user interaction* (Performance)  
- `IFTA_QA_003 / 004 / 005`: *Ease of adding new features such as deviation detection, unregistered aircraft identification, and new map providers* (Extensibility / Modifiability)

**Potential Conflict**  

- Designing for modularity and flexibility often introduces layers of abstraction or interface boundaries, which can lead to increased data processing overhead and reduced performance.  
- To improve performance, techniques such as caching, multithreading, and data prefetching can be applied. However, these techniques often introduce **state** into the system or cause **race conditions**, making the system harder to understand and modify.

#### 2. Performance vs. Resiliency

**QAs Involved**  

- `IFTA_QA_001` (Performance)  
- `IFTA_QA_002`: *Detects and recovers from failure conditions* (Resiliency)

**Potential Conflict**  
- Adding frequent monitoring (e.g., heartbeat checks, retry loops) can introduce extra system load, potentially impacting real-time responsiveness.  
- Balancing proactive failure detection with minimal overhead is essential.

#### 3. Extensibility vs. Usability

**QAs Involved**  

- `IFTA_QA_003 / 004` (Extensibility)  
- `IFTA_QA_006`: *Notifying Users of System Errors in Real Time* (Usability)

**Potential Conflict**  
- Continuously adding features and configuration options may lead to a more complex and crowded UI, making it harder for users to interact with the system intuitively.

### Summary Table

| QA 1          | QA 2            | Reason for Trade-off                                         |
| ------------- | --------------- | ------------------------------------------------------------ |
| Performance   | Modifiability   | Modular structure increases overhead; tight coupling boosts speed |
| Performance   | Resiliency      | Monitoring and recovery add load and complexity              |
| Extensibility | Usability       | More features may increase UI complexity and reduce clarity  |


## Risk assessment

Please refer to [Risk Assessment](./3-RiskAssessment.md)

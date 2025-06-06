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

| ID          | Scenario                                                     | QA Type         | Req. ID      |
| ----------- | ------------------------------------------------------------ | --------------- | ------------ |
| IFTA_QA_001 | UI responds immediately to user interaction                  | Performance     | IFTA_QAR_001 |
| IFTA_QA_002 | The system detects/restores failure conditions               | Resiliency      | IFTA_QAR_002 |
| IFTA_QA_003 | The system can be added a deviation detection feature        | Extensibility   | IFTA_QAR_003 |
| IFTA_QA_004 | The system can be added an identifying unregisterd aircraft feature | Extensibility   | IFTA_QAR_003 |
| IFTA_QA_005 | The system should allow developers to integrate a new map provider into the user interface with minimal code changes, low risk of introducing bugs, and without affecting unrelated parts of the system | Modifiability   | IFTA_QAR_004 |
| IFTA_QA_006 |                                                              | Maintainability | IFTA_QAR_005 |
| IFTA_QA_007 |                                                              | Maintainability | IFTA_QAR_005 |
| IFTA_QA_008 |                                                              | Usability       | IFTA_QAR_006 |
| IFTA_QA_009 |                                                              | Usability       | IFTA_QAR_006 |



## Quality Attribute scenarios

Quality attribute scenarios were written for each requirement of the defined QA list.

### IFTA_TA_001

- Source - User actions in the remote user interface
- Stimulus - Interaction with mouse, including clicking craft, zoom in/out map, panning map, operating menu or control panel
- Artifact - User interface application
- Environment - Runtime, the system is tracking 5000+ aircrafts simultaneously
- Response - UI responds immediately to user interaction, including aircraft data displayed on the map, map is zoomed and panned smoothly without delay, analytical feature are displayed promptly
- Response Measure
  - Aircraft click response time ≤ 100 milliseconds
  - Map zoom/pan completes within ≤ 200 milliseconds
  - Map panning maintains 60 FPS (frames per second) without frame drops
  - Rendering latency after receiving aircraft data ≤ 500 milliseconds for 5,000 aircraft
  - Menu/control panel interaction response ≤ 150 milliseconds
  - Analytical feature display latency ≤ 1 second after user action

**Related design decision** : refer to [ADR 02](./ADRs/adr02.md)

### IFTA_QA_002

- Source - Hardware or network failure, User
- Stimulus - Wifi is turned off or USB cable is disconnected during runtime
- Artifact - User interface application
- Environment - Runtime, the system is tracking ADS-B datasets
- Response
  - System detects failure conditions (e.g., disconnection)
  - User is notified with a clear UI message (e.g., “Lost connection to Raspberry Pi”)
  - System automatically retries reconnection at regular intervals (e.g., every 5 seconds)
  - Application remains responsive and operational (no freeze or crash)
  - Once connectivity is restored, system resumes normal operation without requiring restart

- Response Measure
  - System detects disconnection within ≤ 1 second
  - User notified of fault within ≤ 1 second
  - Reconnection attempts initiated within ≤ 5 seconds and retried every 5 seconds
  - Upon connection recovery, system resumes normal operation within ≤ 1 second
  - System remains stable and responsive throughout the failure period (UI response time degradation < 10%)

**Related design decision** : refer to [ADR 03](./ADRs/adr03.md)

### IFTA_TA_003

- Source - System developer or data analysis engineer

- Stimulus - A requirement is raised to add a feature that detects deviations from registered flight paths

- Artifact - Flight data analysis module and user interface

- Environment - The system is operating under normal conditions and receiving real-time flight data

- Response

  - A new module for detecting path deviations is implemented independently
  - The user interface is updated to display alerts or map-based warnings
  - The new functionality is integrated with minimal changes to existing data processing and UI code

- Response Measure

  - The feature is added as a plugin or separate module without modifying existing components

  - Feature is deployed within 3 days
  - No regressions in existing functionality

**Related design decision** : refer to [ADR 04](./ADRs/adr04.md)



### IFTA_QA_004

- Source - Maintenance engineer or operations manager

- Stimulus - A requirement is raised to add a feature for identifying unregistered aircraft

- Artifact - Aircraft identification database, real-time traffic analysis module, UI display components

- Environment - The system is actively processing real-time flight information

- Response

  - Unregistered aircraft are visually flagged in the UI and recorded in system logs

  - The feature is implemented without altering existing aircraft tracking or display logic

- Response Measure
  - Feature added as separate module preserving existing modules
  - Implemented and tested within 3 days

**Related design decision** : refer to [ADR 05](./ADRs/adr05.md)



### IFTA_QA_005

- Source - Developer
- Stimulus - Add a new map provider to the system
- Artifact - Map rendering module in the Remote User Interface (RUI)
- Environment - During iterative development or feature expansion
- Response - The new map provider integrates seamlessly without affecting existing components
- Response Measure - Integration completed in under 4 person-hours, no unintended side effects observed

**Related design decision** : refer to [ADR 01](./ADRs/adr01.md)



### IFTA_TA_005

- Source
- Stimulus
- Artifact
- Environment
- Response
- Response Measure

### IFTA_QA_006

- Source
- Stimulus
- Artifact
- Environment
- Response
- Response Measure





## TODO - QA priority



## TODO - risk of QA elements

Ex ) 퍼포먼스 항목 -> 제한 시간안에 성공하지 못할경우 -> Probability / Impact 를 H/M/L 로 평가

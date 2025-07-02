# IFTA SW architecture documents

The documents in this folder are constantly updated and periodically backed up to the archive folder.

And our final presentation is in [Google Slide Link](https://docs.google.com/presentation/d/1uCBuazzTcBPUN7PpB5gjWluY5R7if3t0NAmvF9Qv5iM/edit?usp=sharing).

### [Project Plan](./project-plan.md)

The plan explains the outline of the project, members and roles, the task planned, and the milestones.

### [Architectural Drivers](./architectural-drivers.md)

This document describes all the factors that affect the system architecture, and provides risk assessment and experimental planning for the derived requirements.

### [Architecture](./architecture.md)

The document of the software architecture that we envision to address requirements of system.

### ADRs

The ADRs record the important architectural decisions including rationale.

| ID                                                 | Description                                                 | Status   |
| -------------------------------------------------- | ----------------------------------------------------------- | -------- |
| [ADR_01](./ADRs/ADR01-viewport-and-aggregation.md) | Viewport-Based Aircraft Rendering with Aggregation Strategy | Accepted |

### Experiments

| ID                                                 | Description                                                  | Status    |
| -------------------------------------------------- | ------------------------------------------------------------ | --------- |
| [EXP_01](./experiments/exp01-aircraft-number.md)   | Performance Test based on the number of aircraft             | Concluded |
| [EXP_02](./experiments/exp02-ingestion-rate.md)    | Real-Time Aircraft Data Ingestion Rate and Volume via ADS-B Hub | Concluded |
| [~~EXP_03~~](./experiments/exp03-stress-input.md)  | ~~UI Input Stress Test (System Behavior Under Rapid Button Clicks)~~ | Canceled  |
| [~~EXP_04~~](./experiments/exp04-map-api.md)       | ~~API Key Requirement and Limitation Test for Map Providers~~ | Canceled  |
| [~~EXP_05~~](./experiments/exp05-playback-size.md) | ~~System Behavior Test According to Playback Data Size~~     | Canceled  |
| [EXP_06](./experiments/exp06-pi-operation.md)      | Verification of Error Cause Reporting and Connectivity Monitoring for Raspberry Pi | Concluded |
| [EXP_07](./experiments/exp07-multi-thread.md)      | Measuring performance improvement by introducing multi-threading | Suspended |
| ~~[EXP_08](./experiments/exp08-big-query.md)~~     | ~~Usage of BigQuery~~                                        | Canceled  |
| [EXP_09](./experiments/exp09-new-map.md)           | Add new map provider                                         | Concluded |

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

| ID          | Scenario                                                     | Quality Attribute | Req. ID      |
| ----------- | ------------------------------------------------------------ | ----------------- | ------------ |
| IFTA_QA_001 |                                                              | Performance       | IFTA_QAR_001 |
| IFTA_QA_002 |                                                              | Resiliency        | IFTA_QAR_002 |
| IFTA_QA_003 |                                                              | Extensibility     | IFTA_QAR_003 |
| IFTA_QA_004 | The system should allow developers to integrate a new map provider into the user interface with minimal code changes, low risk of introducing bugs, and without affecting unrelated parts of the system. | Modifiability     | IFTA_QAR_004 |
| IFTA_QA_005 |                                                              | Maintainability   | IFTA_QAR_005 |
| IFTA_QA_006 |                                                              | Usability         | IFTA_QAR_006 |



## Quality Attribute scenarios

Quality attribute scenarios were written for each requirement of the defined QA list.

### IFTA_TA_001 - Performance

- Source
- Stimulus
- Artifact
- Environment
- Response
- Response Measure

### IFTA_QA_002 - Resiliency

- Source
- Stimulus
- Artifact
- Environment
- Response
- Response Measure

### IFTA_TA_003 - Extensibility

- Source
- Stimulus
- Artifact
- Environment
- Response
- Response Measure

### IFTA_QA_004 - Modifiability

- Source - Developer
- Stimulus - Add a new map provider to the system
- Artifact - Map rendering module in the Remote User Interface (RUI)
- Environment - During iterative development or feature expansion
- Response - The new map provider integrates seamlessly without affecting existing components
- Response Measure - Integration completed in under 4 person-hours, no unintended side effects observed

Related design decision : refer to ADRx



### IFTA_TA_005 - Maintainability

- Source
- Stimulus
- Artifact
- Environment
- Response
- Response Measure

### IFTA_QA_006 - Usability

- Source
- Stimulus
- Artifact
- Environment
- Response
- Response Measure

















- 

### Performance

#### Scenario

(briet summary of scenario)

- Stimulus : asdf
- Stimulus source : asdf
- Artifact : asdf
- Environment : asdf
- Response : asdf
- Response measure : asdf

#### Tactics & Patterns

blahblah

#### Related Design Decisions

link to design decisions documents


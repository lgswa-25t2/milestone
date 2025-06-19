# Project Plan

This document presents the project's name, purpose, schedule, members, list of tasks, tools used, and goals.  
It may be updated as the project progresses.

## Project Overview

- **Project Name** : Intelligent Flight Tracking Assistance - IFTA
- **Objective** : Improve a system that meets the objectives and requirements of the Federal Aviation Administration (FAA) issued request for proposal (RFP).
- **Scope** : Windows based GUI application

## Goals

- Develop 100% of mandatory features within the schedule
- Develop as many desired features as possible
- SW architecture satisfying the derived Quality Attributes

## Tools & Technologies

- **Language** : C++
- **IDE** : C++ Builder
- **CI/CD**: GitHub
- **Monitoring** : Not Applicable
- **Project Management** : GitHub (optional : *Miro* board)
- **Communication** : MS Teams

## Project Shedule

The picture below was expressed as a progress of 6/14.

<!-- ![image](https://github.com/user-attachments/assets/46d38c02-8838-4a2c-a2a4-19b1c3ce8316) -->

If the assignee is not specifically mentioned in the plan below, it is a collaboration of the whole team.

- [*Planning & Analyze Requirements*](#planning--analyze-requirements) (6/2 - 6/9)
- [*System Design & Experiments*](#system-design--experiments) (6/10 – 6/22)
- [*Development – Mandatory Features*](#development--mandatory-features) (6/9~6/28)
- [*Improve Quality Attribute*](#improve-quality-attribute)
- [*Development – Desirable Features*](#development--desirable-features) (6/9~6/30)
- [*Reassessment of QA*](#reassessment-of-qa) (6/20–6/22)
- [*Integration & Test*](#integration--test) (6/28–7/1)
- [*Final Demo*](#final-demo) (7/2)



### Planning & Analyze Requirements

#### Understand requirements
- 6/2: Understand requirements
- 6/3: identify stakeholders & constraints
- 6/4: define quality attributes

#### Derive functional and quality attribute requirements
- 6/5: Derive functional and quality attribute requirements
- 6/6: describe approach for each quality attributes

#### Make architectural drivers
- 6/7: describe risk assessment
- 6/8~6/9: planning experiment for quality attributes

#### *Milestone 1* (6/10)
- Submit architectural drivers and requirement analysis

[Go to schedule](#project-shedule)



### System Design & Experiments

#### Run experiments

- 6/10–6/11: Run QA Experiment ① – Evaluate original code with aircraft scale (Assigned: Seungsoon, Jaeyoung)
- 6/12–6/13: Run QA Experiment ② – Real-time data ingestion via ADS-B  (Assigned: Seungsoon, Jaeyoung)
- 6/18–6/20: Run QA Experiment ③ – UI input stress test  (Assigned: Seungsoon, Jaeyoung)

#### Create architecture models, design components

-	6/18–6/22: key design decisions reflected in the architecture views and how they address the high priority requirements.
-	6/18~6/19: A deployment view that shows the supporting infrastructure and high-level component allocation.
-	6/20~6/21 : Draw Diagram for Module View, C&C View

[Go to schedule](#project-shedule)



### Development – Mandatory Features

#### Aircraft & Route Metadata – (Assigned: Yongshik)
- 6/9–6/11: Analyze current code
- 6/12–6/14: Analyze API usage
- 6/15–6/18: Lookup aircraft info
- 6/19–6/20: Lookup route info
- 6/23–6/28: Determine origin/destination

#### Time Series Analysis – (Assigned:Sangyeob)
- 6/9–6/11: Analyze current code
- 6/11: Define UX scenarios and GUI
- 6/12: Design tracking architecture and data interface
- 6/13–6/18: Implement tracking
- 6/19–6/24: Implement drop logic after 30 seconds
- 6/25–6/27: Integration test and bug fix

#### UI Enhancements –  (Assigned:Sujin)
- 6/9–6/11: Analyze UI code and define requirements
- 6/11–6/12: Configure aircraft icons
- 6/12–6/13: Update map tiles
- 6/14–6/16: Plot airports
- 6/17–6/18: Improve UI layout
- 6/19–6/21: Display polygons and filter aircraft
- 6/22–6/24: Show directional icons
- 6/25–6/26: Zoom-based tile rendering
- 6/27–6/28: Integration test and bug fix

#### Big Query -  (Assigned:Yongshik)
- 6/17: Analyze current BigQuery code (python script and DisplayGUI module)
- 6/18: Make Google API json file
- 6/19: Data storage verification using BigQuery

[Go to schedule](#project-shedule)



### Improve Quality Attribute

#### Performance & Resiliency –  (Assigned: Jaeyoung, Seungsoon)
- 6/9–6/11: Basic test  
- 6/11–6/13: 1st verification test  
- 6/14–6/17: Strategy and design 2nd test  
- 6/18–6/20: 2nd test  
- 6/18–6/28: Code improvement  
- 6/20–6/30: Final validation test  

#### Modifiability –  (Assigned:Navnit)
- 6/10–6/13: Analyze current design  
- 6/14–6/17: Add map provider - Link to [Experiment 9](./experiments/exp09-new-map.md)
- 6/18–6/20: Apply architectural improvement

#### Extensibility –  (Assigned:Youngtae)
- 6/18–6/22: Add feature to detect deviation  
- 6/23–6/27: Add featrue to detect unregistred aircraft
- 6/28–6/30: Apply architectural improvement
- TODO: update plan

#### *Milestone 2* (6/23)

Submit updated architecture

[Go to schedule](#project-shedule)



### Development – Desirable Features

#### Time series analysis (Desirable) -  (Assigned:Sangyeob)
 - 6/20~6/22 While receiving and recording data, play back tracks (playback at 2x at 3x speed) by moving a mouse cursor
 - 6/23~6/25 Track simulation
 - 6/26~6/30 Dead reckoning - plot tracks now or where they should be based upon constant velocity and altitude (parametric fit)
 - TODO: update plan


#### Safety & Deviation –  (Assigned:Youngtae)
- 6/9–6/13: Analyze code  
- 6/14–6/16: Development - Detecting the aircraft within 5 nm from the airport  
- 6/17–6/18: Development - Detecting two aircraft within 1nm  
- 6/19: Check feasibility - Get predefined flight plan  
- 6/20–6/23: Development - Detecting abnormal flight and deviation  
- 6/24–6/26: Discuss how to display the detected flight 

[Go to schedule](#project-shedule)



### Reassessment of QA

All team members participate, but the assignee of each attribue is the leader of the meeting.

 - Performance (Jaeyoung)
 - Resiliency (Seungsoon)
 - Modifiability (Navnit)
 - Extensibility (Youngtae)

[Go to schedule](#project-shedule)




### Integration & Test

#### Integrate modules, run QA & functional requirements test

TBD

[Go to schedule](#project-shedule)



### Final Demo

#### Presentation and Demonstration

TBD

[Go to schedule](#project-shedule)

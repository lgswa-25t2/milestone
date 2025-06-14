# Project Plan

This document presents the project's name, purpose, schedule, members, list of tasks, tools used, and goals.

It may be updated as the project progresses.

---

## Project Overview

- **Project Name** : Intelligent Flight Tracking Assistance - IFTA

- **Objective** : Improve a system that meets the objectives and requirements of the Federal Aviation Administration (FAA) issued request for proposal (RFP).

- **Scope** : Windows based GUI application

---
## Project Shedule

### 🔹 Phase: Planning & Analyze Requirements (6/2–6/9)
#### Understand requirements (Assigned: All) (6/2~6/4)

- Understand requirements
- identify stakeholders & constraints
- define quality attributes   

#### Derive functional and quality attribute requirements (Assigned: All) (6/5~6/6)
- Derive functional and quality attribute requirements
- describe approach for each quality attributes

#### Make architectural drivers (Assigned: All) (6/7~6/9)
- describe risk assessment
- planning experiment for quality attributes

### 🟢 Milestone 1 (6/10)

- Submit architectural drivers and requirement analysis


### 🔹 Phase: System Design & Experiments (6/10–6/22)
#### Run QA experiments (Assigned: Seungsoon, Jaeyoung)

- 6/10–6/11: Run QA Experiment ① – Evaluate original code with aircraft scale  
- 6/12–6/13: Run QA Experiment ② – Real-time data ingestion via ADS-B  
- 6/18–6/20: Run QA Experiment ③ – UI input stress test  
- 6/18–6/20: Design Architecture (deployment view, key decisions, views)

#### Create architecture models, design components (Assigned: All)
-	6/18~6/19: A deployment view that shows the supporting infrastructure and high-level component allocation.
-	6/20~6/21 : Draw Diagram for Module View, C&C View
-	6/20~6/22: key design decisions reflected in the architecture views and how they address the high priority requirements.


### 🔹 Development – Mandatory Features (6/9~6/28)

#### Aircraft & Route Metadata – (Assigned: Yongshik)
- 6/9–6/11: Analyze current code  
- 6/12–6/14: Analyze API usage  
- 6/15–6/18: Lookup aircraft info  
- 6/19–6/20: Lookup route info  
- 6/23–6/28: Determine origin/destination  

#### Time Series Analysis –  (Assigned:Sangyeob)
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

#### Big query -  (Assigned:Navnit)
- TODO: update plan (Planning by Seungsoon)



### 🔹 Improve Quality Attribute

#### Performance & Resiliency –  (Assigned: Jaeyoung, Seungsoon)
- 6/9–6/11: Basic test  
- 6/11–6/13: 1st verification test  
- 6/14–6/17: Strategy and design 2nd test  
- 6/18–6/20: 2nd test  
- 6/18–6/28: Code improvement  
- 6/20–6/30: Final validation test  

#### Modifiability –  (Assigned:Navnit)
- 6/10–6/13: Analyze current design  
- 6/14–6/17: Add map provider  
- 6/18–6/20: Apply architectural improvement
- TODO: update plan

#### Extensibility –  (Assigned:Youngtae)
- 6/18–6/22: Add feature to detect deviation  
- 6/23–6/27: Add featrue to detect unregistred aircraft
- 6/28–6/30: Apply architectural improvement
- TODO: update plan


### 🟡 Milestone 2 (6/23)

Submit updated architecture



### 🔹 Development – Desirable Features (6/9~6/30)

#### Time series analysis (Desirable) -  (Assigned:Sangyoub)
 - 6/20~6/22 While receiving and recording data, play back tracks (playback at 2x at 3x speed) by moving a mouse cursor
 - 6/23~6/25 Track simulation
 - 6/26~6/30 Dead reckoning - plot tracks now or where they should be based upon constant velocity and altitude (parametric fit)
   TODO: update plan


#### Safety & Deviation –  (Assigned:Youngtae)
- 6/9–6/13: Analyze code  
- 6/14–6/16: Development - Detecting the aircraft within 5 nm from the airport  
- 6/17–6/18: Development - Detecting two aircraft within 1nm  
- 6/19: Check feasibility - Get predefined flight plan  
- 6/20–6/23: Development - Detecting abnormal flight and deviation  
- 6/24–6/26: Discuss how to display the detected flight 



### 🔹 Reassessment of QA (6/20–6/22)
 - Performance (Jaeyoung)
 - Resiliency (Seungsoon)
 - Modifiability (Navnit)
 - Extensibility (Youngtae)




### 🔹 Integration & Test (6/28–7/1)

#### Integrate modules, run QA and functional tests



### 🎯 Final Demo (7/2)

#### presentation and demonstration

---

## Tools & Technologies

- **Language** : C++
- **IDE** : C++ Builder

- **CI/CD**: GitHub

- **Monitoring** : Not Applicable  

- **Project Management** : Miro board

- **Communication** : MS Teams 



## Goals

- Develop 100% of mandatory features within the schedule
- Develop as many desired features as possible
- SW architecture satisfying the derived Quality Attributes

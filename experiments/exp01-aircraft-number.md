# Experiment 1: Performance Test According to Number of Aircraft 


## Results and recommendations 

![Rendering Time vs. Number of Aircraft](../images/RenderingTime.png)

Origin : Map rendering time on original source code  
DrawOnlyViewable : Render aircrafts only in the viewport  
DrawZoomIn0.00002 : Render when zoom-in (Number of aircraft is 200 to 300)  
DrawZoomIn0.00005 : Render when zoom-in (Number of aricraft is 1700 to 1800)  
  
- UI performance starts to degrade noticeably when the number of aircraft exceeds 2,000.  
- Displaying too many aircraft on the map also negatively affects usability.  




## Objective 
It is natural to be concerned that system performance may degrade as the number of tracked aircraft increases.
The objective of this experiment is to determine how many aircraft the current system can handle while maintaining an acceptable screen update rate and user interaction responsiveness.
The results will help identify system performance thresholds, bottlenecks, and areas that require optimization.

## Status
[***Planned*** | In progress | Suspended | Canceled | Concluded]

## Expected outcomes
 - Performance test logs and statistical data
 - Graphs showing performance changes according to the number of aircraft
 - CPU and memory usage analysis by aircraft count

## Resources required
 - Software: Flight Tracker client

 - Hardware: One test laptop (Intel Core i7-1165G7 @ 2.80GHz / 16.0GB RAM)

 - Test data: Pre-recorded simulation files for different aircraft counts
   (50 / 100 / 200 / 300 / 500 / 1000 / 3000 / 5000 / 10000)
   
 - UI automation macro scripts

 - Personnel: 3 people × 4 hours
   
   (1 for test execution, 2 for preparation and support)

## Experiment description
- Test Environment Setup

  Generate pre-recorded test data (using AI tools if needed)

  Prepare and configure a UI macro automation tool and scripts

  Implement logging functionality for screen update and user response time

- Step-by-Step Execution

  Gradually increase the number of aircraft:
  50 → 100 → 200 → 300 → … → 10,000

  \* At each step, measure:

  Time from data load to aircraft appearing on map

  Response time when selecting an aircraft

  UI latency when switching menus

  Time to reflect map interactions (zoom, pan, switch)

  CPU and memory usage

- Log Analysis and Visualization

  Organize collected logs and measured data

  Visualize results as graphs

  Identify performance thresholds and bottlenecks

  Detect any abnormal behavior under load

- Conclusion and Review

  Summarize the findings in a final report
  
  Propose improvements based on analysis
  
  Plan follow-up experiments if necessary

## Duration
Start Date: June 10, 2025

End Date: June 12, 2025



## Assignee

Jaeyong Jeong, Seungsoon Lee



## Links and references

Technical risk [TR2](../architectural-drivers.md#technical-risk-assessment)

Software Architecture in Practice – Chapter 11: Performance Tactics

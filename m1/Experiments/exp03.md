# Experiment 3: UI Input Stress Test (System Behavior Under Rapid Button Clicks) 


## Results and recommendations 
To be completed after the experiment.

## Objective 
The purpose of this experiment is to evaluate the responsiveness and stability of the system when exposed to rapid or excessive UI input events, such as continuous button clicks.

This test aims to answer the following key questions:

- Is the system responsive and stable when a UI button is clicked repeatedly at short intervals?
- Do duplicate or missed event processing issues occur?
- To what extent do CPU and memory usage increase due to repeated interactions?
- Can the system recover from freezes or crashes triggered by rapid input?

The goal is to identify potential bottlenecks or vulnerabilities in the UI event handling mechanism and define optimization points for future improvements.

## Status
[***Planned*** | In progress | Suspended | Canceled | Concluded]

## Expected outcomes
 - Event logs generated during rapid click input
 - Response time and processing speed measurements
 - CPU and memory usage patterns during the test
 - Error/crash detection and recovery behavior
 - Visualized graphs and a summary test report

## Resources required
 - Software: Flight Tracker client
 - Hardware: One test laptop (Intel Core i7-1165G7 @ 2.80GHz / 16.0GB RAM)
 - Personnel: 3 people × 4 hours
   - Script creation and test execution: 1 person × 2 hours
   - Log analysis and report writing: 1 person × 2 hours
   

## Experiment description
- Test Environment Setup

  Add logging code for button click events

  Set up and launch the client application with the automation tool

  Configure logging path and CPU/memory monitoring tools

- Execute Stress Test

  Perform automated button clicks with different intervals (10ms, 100ms, 500ms) and repetition counts (50, 100, 500)

  Example: 100 consecutive clicks on a specific UI button and observe visual feedback and UI stability

- Data Collection

  Measure UI response time and screen update delay
  
  Check for dropped or unprocessed events
  
  Record CPU and memory usage during each test
  
- Analysis and Visualization

  Analyze delays, dropped events, and behavior under load
  
  Create graphs of response time and resource usage for each scenario
  
  Evaluate stability and recovery capacity
  
- Summary and Review

  Write a summary report of findings
  
  Identify problems and propose mitigation strategies
  
  Determine the need for further experiments

## Duration
Start Date: June 13, 2025

End Date: June 14, 2025

## Links and references
Software Architecture in Practice – Chapter 11: Performance Tactics

Selenium Official Documentation

AutoHotKey Scripting Examples
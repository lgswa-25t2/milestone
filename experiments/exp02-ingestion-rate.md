# Experiment 2: Real-Time Aircraft Data Ingestion Rate and Volume via ADS-B Hub 


## Results and recommendations 

![image](https://github.com/user-attachments/assets/d80f5a90-71a4-4ba3-8c8d-73a85ca57504)
![image](https://github.com/user-attachments/assets/d548447e-fe80-4adc-8d58-edf3f19ac02f)


1. Average and Peak Message Ingestion Rate (msg/sec)
Observation Period: June 14, 01:00 – 10:00

Average Rate: 4,100.58 messages per second

Peak Rate: 9,367 messages per second

2. Number of Aircraft Observed per Minute/Hour
Observation Period: June 14, 01:00 – 10:00

[Total Aircraft Observed]

Average: 5,157.92 aircraft

Maximum: 7,808 aircraft

[Visible Aircraft Only]

Average: 4,633.20 aircraft

Maximum: 7,015 aircraft

3. Update Frequency per Aircraft
Observation Period: From June 13, 01:04 (based on 100,000 data points)

Average Update Frequency: 15.815 messages per aircraft

## Objective 
The objective of this experiment is to quantitatively measure the rate and volume of real-time aircraft data streaming via ADS-B.
This will help objectively define the minimum performance requirements for the data ingestion module and buffering mechanisms in the system architecture.

The experiment seeks to answer the following key questions:

- How frequently is an aircraft’s position data updated?
- How many aircraft can be recognized simultaneously at a given time?
- What is the maximum number of messages received per second?

 The results will be used to update the performance test benchmarks and serve as reference material for architectural design decisions.

## Status
[***Planned*** | In progress | Suspended | Canceled | Concluded]

## Expected outcomes
 - Timestamped aircraft message logs
 - Number of aircraft observed per minute/hour
 - Average and peak message ingestion rate (msg/sec)
 - Update frequency per aircraft
 - Visualization graphs for each data metric

## Resources required
 - Software: Flight Tracker client

 - Hardware: One test laptop (Intel Core i7-1165G7 @ 2.80GHz / 16.0GB RAM)

 - Personnel: 3 people × 4 hours
   
   - Data collection and preprocessing: 1 person × 6 hours
   
   - Data analysis and visualization: 2 people × 3 hours

## Experiment description
- Test Environment Setup

  Modify client code to log raw data from the ADS-B live feed
  
  Install and configure the client on the test PC and ensure proper connection to the ADS-B Hub
  
- Data Collection

  Verify that data is being collected correctly

  Check data quality, including missing position information and overall integrity

- Data Analysis

  Analyze number of unique aircraft per minute/hour

  Calculate average and peak message ingestion rate (msg/sec)

  Determine update frequency per aircraft

  Create visualizations and graphs for all metrics

- Summary and Review

  Write a summary report of results
  
  Define data ingestion performance baselines to be reflected in system design
  
  Evaluate the need for follow-up experiments

## Duration
Start Date: June 11, 2025

End Date: June 12, 2025

## Assignee

Jaeyong Jeong, Seungsoon Lee

## Links and references
Technical risk [TR2](../architectural-drivers.md#technical-risk-assessment)

Software Architecture in Practice – Chapter 11: Performance Tactics

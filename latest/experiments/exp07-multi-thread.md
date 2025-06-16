# Experiment 7: Measuring performance improvement by introducing multi-threading

## Results and recommendations

To be written upon completion of the experiment.

## Objective

The purpose of this experiment is to check whether the Raspberry Pi reports connectivity-related failures (e.g., Wi-Fi disconnect, antenna removal, system lock-up) to our system.
Additionally, the experiment will confirm whether the Raspberry Pi has a working **heartbeat mechanism**, and whether our system performs **ping-based health checks** to detect failures passively.

The purpose of this experiment is to measure how much performance is improved when the UI thread and business logic thread are separated as mitigation strategy in [TR2](../architectural-drivers.md#technical-risk-assessment). To compare the results, the results of [Exp1](./exp01-aircraft-number.md) and [Exp2](./exp02-ingestion-rate.md), which are performance measurement results that have not been improved, and repeat the same experiment after the implementation is completed to check whether there is a difference.

## Status

\[***Planned*** | In progress | Suspended | Canceled | Concluded]

## Expected outcomes

* Confirmation of whether error causes (Wi-Fi failure, antenna removal, lock-up) are reported to our system
* Determination of whether a heartbeat mechanism is implemented and functioning
* Verification of whether our system actively monitors Raspberry Pi health via ping or timeout detection

## Resources required

 - Software: Flight Tracker client

 - Hardware: One test laptop (Intel Core i7-1165G7 @ 2.80GHz / 16.0GB RAM)

 - Personnel: 2 people × 4 hours

   - Test execution, data collection: 1 person × 4 hours

   - Data processing, analysis and visualization: 1 people × 4 hours

## Experiment description

### 1. Pre-experiment

* Need to implement the function first.

### 2. Test Scenarios

 Performance tests have already been carried out for two types, so the scenario is carried out in the same way.

- Scenario of Exp1 - [Link](./exp01-aircraft-number.md#experiment-description)
- Scenario of Exp2 - [Link](./exp02-ingestion-rate.md#experiment-description)

### 3. Data Analysis

* Visualization
* Comparison between Before and After

### 4. Conclusion and Review

* Check the performance improvement level
* Write how the implementation affects other quality attributes and proceed with a team review.

## Duration

Start Date: June 22, 2025

End Date: June 22, 2025

## Assignee

Youngtae Kim, Jaeyong Jeong

## Links and references

Technical risk [TR2](../architectural-drivers.md#technical-risk-assessment)

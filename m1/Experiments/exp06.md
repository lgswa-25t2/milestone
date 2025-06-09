
# Experiment 5: System Behavior Test According to Playback Data Size

## Results and recommendations

To be written upon completion of the experiment.

## Objective

The goal of this experiment is to investigate how the system behaves as the size of playback data increases.
We aim to determine the maximum data size the system can handle while maintaining acceptable load times, UI responsiveness, and memory usage.
This will help identify performance bottlenecks and data handling limits.

## Status

[***Planned*** | In progress | Suspended | Canceled | Concluded]

## Expected outcomes

* Playback performance logs and detailed metrics
* Graphs showing how system behavior changes with data size
* Thresholds for maximum playable data size without degradation
* CPU and memory usage trends per playback size

## Resources required

* **Software**: Playback module integrated with logging
* **Hardware**: One test laptop (Intel Core i7-1165G7 @ 2.80GHz / 16.0GB RAM)
* **Test data**: Playback files of varying sizes
  (5MB / 20MB / 50MB / 100MB / 200MB / 500MB / 1GB)
* **Automation**: UI automation macros for playback start/stop
* **Personnel**: 3 people × 4 hours

  * (1 for test execution, 2 for setup, logging, and analysis)

## Experiment description

### 1. Test Environment Setup

* Prepare playback files with realistic and representative aircraft movement data
* Implement logging to measure load times, playback lag, memory usage, and responsiveness
* Set up UI automation for consistent test execution

### 2. Execution Plan

* Run playback tests with increasing file sizes
* For each data size, measure:

  * Time to load playback file
  * Time to start playback
  * Average playback frame rate and lag
  * Response time to playback controls (pause, seek, speed change)
  * CPU and memory usage during playback

### 3. Data Analysis

* Collect and organize logs and metrics
* Visualize results using line graphs or heatmaps
* Identify thresholds where performance drops or failures occur

### 4. Conclusion and Review

* Summarize key findings and thresholds
* Propose architectural or design improvements
* Recommend limits or data chunking strategies if needed
* Suggest follow-up testing for real-world scenarios

## Duration

Start Date: June 13, 2025
End Date: June 15, 2025


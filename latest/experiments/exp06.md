# Experiment 6: Verification of Error Cause Reporting and Connectivity Monitoring for Raspberry Pi

## Results and recommendations

To be written upon completion of the experiment.

## Objective

The purpose of this experiment is to check whether the Raspberry Pi reports connectivity-related failures (e.g., Wi-Fi disconnect, antenna removal, system lock-up) to our system.
Additionally, the experiment will confirm whether the Raspberry Pi has a working **heartbeat mechanism**, and whether our system performs **ping-based health checks** to detect failures passively.

## Status

\[***Planned*** | In progress | Suspended | Canceled | Concluded]

## Expected outcomes

* Confirmation of whether error causes (Wi-Fi failure, antenna removal, lock-up) are reported to our system
* Determination of whether a heartbeat mechanism is implemented and functioning
* Verification of whether our system actively monitors Raspberry Pi health via ping or timeout detection

## Resources required

* **Hardware**:

  * Raspberry Pi 5
  * Wi-Fi-enabled test environment
  * Removable external antenna (if used)
  * Power supply with switch (for simulating lock-up or forced reset)

* **Software**:

  * Device-side agent expected to report error status or send heartbeat
  * Network tools for ping/connection monitoring (e.g., `ping`, `fping`, custom watchdog)

* **Personnel**: 2 people × 5 hours

  * (1 for physical and network testing, 1 for log capture and analysis)

## Experiment description

### 1. Setup

* Ensure Raspberry Pi is registered in our system and actively communicating
* Enable log capture on both device and RUI (Windows) sides
* Identify expected heartbeat mechanism (interval, format, channel)
* Confirm if the central system sends periodic pings or has timeout logic

### 2. Test Scenarios

Perform the following fault injections and observe the system's response:

#### a) **Wi-Fi Disconnection**

* Disconnect the Raspberry Pi from Wi-Fi (e.g., shutdown interface or pull router connection)
* Observe:

  * Whether an error cause is sent before disconnection
  * If heartbeat stops, how long until the system notices
  * Whether ping failure triggers a system alert

#### b) **Antenna Removal (if applicable)**

* Physically remove the external antenna to simulate degraded signal
* Observe:

  * Whether the Raspberry Pi detects and reports low signal or connectivity degradation
  * Whether connection loss occurs and if it’s detected by our system

#### c) **System Lock-up**

* Simulate lock-up via CPU overload, infinite loop, or OS hang (e.g., `while(true)` on main thread)
* Observe:

  * Whether heartbeat stops
  * If our system detects this via timeout or ping failure
  * Whether any residual logs are sent on reboot

### 3. Data Analysis

* Analyze logs to check:

  * Whether meaningful error messages were sent from the Pi before or after each failure
  * Time delay between failure and detection on our system
  * Whether our system uses a polling/ping mechanism or relies solely on heartbeats
* Categorize cases into:

  * Actively reported error cause
  * Detected via ping/timeout
  * Not detected

### 4. Conclusion and Review

* Identify gaps in failure reporting or monitoring
* Recommend:

  * Adding/reinforcing heartbeat or watchdog mechanism on the Pi
  * Implementing or tightening ping-based monitoring on our system
  * Standardizing error reporting for connectivity issues
* Propose next steps for automated recovery or redundancy

## Duration

Start Date: June 14, 2025

End Date: June 16, 2025

## Assignee

Jaeyong Jeong, Youngtae Kim

## Links and references

Technical risk [TR2](../2-ArchitecturalDrivers.md#technical-risk-assessment)

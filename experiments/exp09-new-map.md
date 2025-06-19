# Experiment 9: Add new map provider

## Results and recommendations

After analysis, ***OpenStreetMap (OSM)*** was selected as the most suitable provider due to open license, modular integration capability, offline tile accessibility.

## Objective

Evaluate the effort and system impact required to support an additional map provider in the existing architecture. This tests the system's modifiability by assessing how easily a new component can be plugged in and made functional without major architectural changes. This will guide the decision on selecting the most suitable map provider for production integration.



## Status

\[Planned | In progress | Suspended | Canceled | ***Concluded***]



## Expected outcomes

- Successful integration of new map tiles and basic interaction (zoom)
- Minimal changes to existing system architecture or UI logic
- Justified decision to select one map provider based on modifiability, licensing, ecosystem, and technical fit

## Resources required

* **Hardware**:
  * Hardware: One test laptop (Intel Core i7-1165G7 @ 2.80GHz / 16.0GB RAM)
* **Software**:
  * RUI application (code base)
  * Abstraction or adapter layer for map provider switching
  * Log monitoring and system debug tools
* **Personnel**: 1 people × 4 days x 4 hours/day

## Experiment description

### 1. Setup

- Identify and isolate all dependencies on the current map provider (Google Maps)
- Build a modular integration layer in the application for map provider by extending MasterLayer (already existing code)
- Find non commercial (open / free) map providers

### 2. Test Scenarios

- Licensing and ecosystem: Review provider licenses for compatibility with project policies, and open and free usage
- Integration complexity : Measure number of files affected, and architectural adjustments required to add new provider
- Provider switching : Validate ability to switch providers via interface changes without modifying existing provider's code
- Performance impact : Measure startup time, tile load times, and responsiveness in the RUI
- Error handling and resilience : Check how gracefully failures (e.g. network outages) are handled



### 3. Conclusion and Review

- Summarize findings with emphasis on modifiability metrics and development effort
- Select ***OpenStreetMap*** as the best candidate due to:
  - Minimal integration effort
  - Clear modular separation
  - Open and permissive license promoting future adaptations
- Proceed with OSM, and leveraging the modular approach tested



## Duration

Start Date: June 14, 2025

End Date: June 17, 2025

## Assignee

Navnit Kumar

## Links and references

![image](https://github.com/user-attachments/assets/83ce49fc-598f-41d3-aada-144c99b5ed5b)



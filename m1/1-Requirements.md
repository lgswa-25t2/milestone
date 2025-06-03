# Requirements

This document contains Functional requirements and Quality attribute requirements.

## Functional Requirements

Derived from Project Description documents.

### Mandatory

- Aircraft and Route Metadata
  - Look up aircraft information (e.g., Airline)
  - Look up route information
  - Determine aircraft point of origin and destination
  - Use APIs and pull information (e.g., https://vrs-standing-data.adsb.lol/ )

- Time Series Analysis
  - Track history - Flight tracking of time and location
  - Know age of track (drop after 30 seconds)

- Enhancements to User Interface
  - Improve the look and user experience with the user interface
  - Update map tiles
  - Plot airports
  - Modify aircraft icons and leaders

### Desired

- Safety and Deviation Analysis

  - Collision avoidance - Assess aircraft within proximity to each other

  - Compare contrast a flight’s SBS or ADS-B data with planned route

  - Analyze aircraft flight profile for anomalies (e.g., flying to the wrong airport) Is the flight deviating from the flight plan?


- Time Series Analysis
  - While receiving and recording data, play back tracks (Playback at 2x at 3x speed) by moving a mouse cursor
- Track simulation
  - Dead reckoning - plot tracks now or where they should be based upon constant velocity and altitude (parametric fit)


## Quality Attribute Requirements 

Derived from QA scenarios in [architectural drivers](./2-ArchitecturalDrivers.md) documents.

- asdf
- qwer
- zxcv
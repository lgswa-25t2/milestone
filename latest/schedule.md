# Task Schedule



## Aircraft and Route Metadata

Assigned to Yongshik.

#### Description

- Look up aircraft information (e.g. Airline)
- Look up route information
- Determine aircraft point of origin and destination
- Use APIs and pull information (e.g. https://vrs-stainding-data.adsb.lol)

#### Detailed Schedule

- 6/9 ~ 6/11 : Analysis current code
- 6/12 ~ 6/14 : Analysus of API usage
- 6/15 ~ 6/18 : Look up aircraft information
- 6/19 ~ 6/22 : Look up route information
- 6/23 ~ 6/28 : Determine aircraft point of origin and destination

## Time series analysis

Assigned to Sangyeob.

#### Description

- Track history - Flight tracking of time and location
- Know age of track (drop after 30 seconds)

#### Detailed Schedule

- 6/9 ~ 6/11 : Analysis current code
- 6/11 : Describe detailed scenarios
  - Defined UX scenarios
  - Defined GUI design
- 6/12 : Track history architecture design
  - Selected flight tracking history UI design
  - Data storage design
  - Data save/load interface design
- 6/13 ~ 6/18 : Flight tracking implementation
  - Implementation tracking UI
  - Implementation tracking Data storage
- 6/19 ~ 6/24 : Drop history after 30 seconds implementation
  - Tracking UI remove and clear logic implementation
- 6/25 ~ 6/27 : Integration test and bug fix

## Enhancements to User Interface

Assigned to Sujin.

#### Description

- Improve the look and user experience with the user interface
- Update map tile
- Plot airports
- Modify aircraft icons and leaders

#### Detailed Schedule

- 6/9 ~ 6/10 : Analysis current code
- 6/11 : Describe detailed requirements
- 6/12 ~ 6/15 : Update map tiles
  - optimized TileManager
  - improve tile caching mechanism
- 6/16 ~ 6/18 : Plot airports data
- 6/19 ~ 6/23 : Improvement UI layout
  - refactoring `DisplayGUI.cpp`
  - applying better UI components design
  - Color / Icon update
- 6/23 ~ 6/27 : Improve Aircraft Icon
  - Dynamic icon resizing (based on zoom level)
  - Icon categorization by aircraft type
  - Improved leader line styling

## Safety and Deviation Analysis

TBD

#### Description

- Compare contrast a flight's SBS or ADS-B data with planned route
- Analyze aircraft flight profile for anomalies (e.g. flying to the wrong airport)
- Is the flight deviating from the flight plan?

## Time series analysis 2

TBD

#### Description

- While receiving and recording data, play back tracks (playback at 2x at 3x speed) by moving a mouse cursor
- Track simulation
- Dead reckoning - plot tracks now or where they should be based upon constant velocity and altitude (parametric fit)



## Performance & Resiliency

Assigned to Jaeyong & seungsoon

#### Description

- Measure current UI response time
- Real-time Aircraft data ingestion rate and volume via ADS-B hub
- Action when wifi is turned off or USB cable is disconnected during runtime

#### Detailed Schedule

- 6/9 ~ 6/11 : Current system basic test
- 6/11 ~ 6/13 : Current system performance attributes verification 1st test
- 6/14 ~ 6/17 : Establish improvement strategies and 2nd test design
- 6/18 ~ 6/20 : 2nd test in progress
- 6/18 ~ 6/28 : SW code modification
- 6/20 ~ 6/30 : Test to confirm improvement results in progress

## Modifiability

Assigned to Navnit

#### Description

add map provider



## Extensibility

Assigned to Youngtae

#### Description

- detect deviation
- detect unregistered aircraft
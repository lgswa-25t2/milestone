# Demo Scoring

Teams are ranked by total points scored. The maximum possible score is 200 points with an additional 10 bonus points.

Possible Grading Criteria Architecture Class:

### Functional capability [40 points]

Additional features or capabilities added. Each feature graded as works completely/works partially/doesn’t work or not implemented. Examples include:

- Detect airplanes on collision course

- Detect unregistered airplanes

- Detect deviations from registered flight path

- Lookup aircraft information

- Record history to file (need to determine what specific information should be recorded)

### Response time [30 points]

Response time for the remote user interface application, Raspberry Pi, and external database when actions are initiated by the user in the remote user interface. Examples include:

- Timely respond when the data load scales

- Timely respond when executing added analytical features

### Fault detection and error handling [30 points]

Examples include:

- How does the GUI application react when it loses connection with the Raspberry Pi? (Test turning off wifi)

- How does the system react when the Raspberry Pi loses connection with the ADS receiver? (Test pulling the USB cable)

### Architecture supports new requirements or enhancements [30 points]

Examples include:

- Are key functionalities abstracted behind interfaces?

- Can new behavior be injected without modifying existing code?

- Are dependencies explicitly managed?

### Map Support [20 points]

The GUI application should support multiple map data types and different levels of scale. Examples include:

- Support map data from different map providers
- Support zoom in and zoom out features

### System and software quality [- 3 points per error observed for up to -24 points]

- Point deductions for any errors

### Remote User Interface (Max 50 points + 10 possible bonus points)

- Real time display of maps and aircraft tracks
- Real time display of “hooked” aircraft
- Display aircraft data and other display data
- Implement click buttons (or similar feature) to remotely connect to the Raspberry Pi Flight Tracker, ADS-B Hub, recorded files, or other data files
- Implement slide bars or similar features to promote interaction of flight track data on the map visually
- Display polygons and show only aircraft that are within the defined waypoints on the map (e.g., square or irregular shape following an highway)

- Best user interface (UI): 10 points; 2nd Best UI: 8 points, 3rd Best UI: 6 points, 4th Best UI: 4 points, 5th Best UI: 4 points (points awarded based on client/sponsor judgment)



## Assumptions and Hints

- Each team will be given a complete Raspberry Pi Flight Tracker Kit (e.g., with Raspberry Pi, SDR, etc.)
- Each team’s Raspberry Pi will come pre-loaded with a base image with dump1090 installed.
- Each team will be given a router to support local network testing between Raspberry Pi and remote user interface.
- Each team will be given sample source code for the remote user interface.
- Each team will be given Google Cloud Platform credit to use Google BigQuery (SW Architect - $100 per team)
- The team may use any third-party software but the choice of technology must be justified.
- Assume that anything can fail… your design should account for failure and recovery to the greatest extent possible.
- Teams will use their own laptops for software development and to execute the Flight Agent user interface.
- The provided software will function as shown in the Kick Off demonstration; however, there may be better ways to design or implement functionality and quality attributes.
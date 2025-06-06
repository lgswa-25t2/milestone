1. What is the desired round-trip time to fetch aircraft and route metadata information?

: Assuming this question refers to active aircraft tracks, the time round trip time must be less than

1 second. However, Solvit, Inc will be looking at which team can attain the fastest time.



2. What metadata must be displayed for a “hooked” aircraft in order to meet completeness

requirements?

: The as-is remote user interface provided to the teams shows the minimum metadata that must

be displayed. Solvit, Inc is looking at team creativity and ideas for other metadata to display.



3. What range should be considered acceptable for proximity detection? Proximity

detection to what?

: Proximity detection should identify aircraft within 1nm. If an aircraft is about to enter controlled

airspace, like around an airport, then 5nm.



4. What level of deviation (in miles) from the planned route should be classified as a

deviation?

: 5 nautical miles



5. What should the system behavior be when an aircraft’s flight profile is detected as

anomalous?

: This is a team’s design decision. Think like you are in charge of flight safety and need to know

the information on a cluttered screen with hundreds of aircraft flying around. How would you

want the system to alert you if you were in charge and responsible?



6. What specific data must be recorded in the flight history file (e.g., timestamp, aircraft ID,

location)?

: This is a team’s design decision. What data would you need for training purposes or if an

accident happened? What data would you need to simulate a previous flight?



7. What is the recommended file size for a record history file used in playback?

: Good question. This is part of the design and architecture tradeoff that teams must analyze,

work through, and justify decisions.



8. Which map providers must be supported to receive full credit during evaluation?

: Teams are welcome to use any map data. Think of the user experience, however. Which map

data, including its scale and imagery, provides the best experience for the remote user interface.



9. If map data fails to load or lags, what is the expected system response? Will resiliency

and user error messaging be part of the evaluation?

: Good question. Yes. Review the quality attributes section of the project plan. This is part of the

design and architecture tradeoff that teams must analyze, work through, and justify decisions.



10. Will the presence of partial updates or stale metadata (e.g., outdated altitude or speed)

negatively affect the evaluation score?

: Good question. Stale data is not great for air safety. While this is a desired feature and not a

mandatory feature, other teams will receive bonus points for implementing this feature.



11. How do you expect the number of flights can be displayed at the same time? (maximum

flights count on the map)

: The display should be able to manage all active tracks. The question that seems to be asked is

whether some tracks should be filtered.



Another way to think about the question is where the team can make the decision based on

regional control areas. Selecting those regional control areas as though those are the areas

under one’s control may offer a filter option for aircraft entering, within, and exiting and thus limit

the number to what has to be displayed for a specific controller for that airspace. Be sure to

think about handoff times between airspace with aircraft coming in and out of the airspace

selected.



12. What does analytical feature mentioned in response time ?

: Please clarify the question.



13. Is there any predefined test cases to demonstrate implemented features ?

: No. The teams will need to show their test cases used during the final demo.



14. What duration (in milliseconds) should be considered acceptable as the connection

timeout threshold?

: Good question. This is part of the design and architecture tradeoff that teams must analyze,

work through, and justify decisions.



15. What is the acceptable threshold (in milliseconds or seconds) for system recovery time

after a lost connection?

: Good question. This is part of the design and architecture tradeoff that teams must analyze,

work through, and justify decisions.



16. By what means will the system architecture be evaluated—through design

documentation, architectural diagrams, actual code review, or a combination of these?

: Please refer to the project plan. There are three milestone events. Contact Paulo and Matt for

milestone 1 and 2 grading criteria. Solvit will be posting the milestone 3 grading criteria by mid

June.



17. How many and which types of maps are required to satisfy the evaluation criteria?

: Refer to question 8 and answer.



18. What qualifies as an error for evaluation purposes? Does this include only crashes and

exceptions, or also issues like broken user flows and missing error messages?

: Yes to all examples provided.

Air Safety would dictate that if there is an error - there is an error. Some things coming from the

ADSB community or the server QoS are probably out of your control.



19. Is there a defined quantitative performance standard or a stress test scenario that will be

used during evaluation to assess system behavior under load?

: Great question. The details of the final demo are being finalized. The published final demo

criteria will answer this question. Anticipate mid June for the grading criteria and final demo

guidance to be published.
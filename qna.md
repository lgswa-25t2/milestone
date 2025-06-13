## Part 1

- What is the desired round-trip time to fetch aircraft and route metadata information?

  - Assuming this question refers to active aircraft tracks, the time round trip time must be less than 1 second. However, Solvit, Inc will be looking at which team can attain the fastest time.

- 항공기 및 경로 메타데이터 정보를 가져오는 데 원하는 왕복 시간은 얼마입니까?

  이 질문이 활성 항공기 트랙을 언급한다고 가정하면 왕복 시간은 1초 미만이어야 합니다. 그러나 Solvit, Inc는 어느 팀이 가장 빠른 시간을 달성할 수 있는지 살펴볼 것입니다.



- What metadata must be displayed for a “hooked” aircraft in order to meet completeness requirements?

  - The as-is remote user interface provided to the teams shows the minimum metadata that must be displayed. Solvit, Inc is looking at team creativity and ideas for other metadata to display.

- 완전성 요건을 충족하기 위해 "후크된" 항공기에 대해 어떤 메타데이터를 표시해야 합니까?

  팀에 제공되는 as-is 원격 사용자 인터페이스는 표시되어야 하는 최소 메타데이터를 보여줍니다. Solvit, Inc는 보여줄 다른 메타데이터에 대한 팀 창의성과 아이디어를 찾고 있습니다.



- What range should be considered acceptable for proximity detection? Proximity detection to what?

  - Proximity detection should identify aircraft within 1nm. If an aircraft is about to enter controlled airspace, like around an airport, then 5nm.

- 근접 감지에 허용되는 범위는 무엇입니까? 무엇에 대한 근접 감지?

  근접 감지는 1nm 이내의 항공기를 식별해야 합니다. 항공기가 공항 주변과 같이 통제된 영공에 진입하려고 한다면, 5nm.



- What level of deviation (in miles) from the planned route should be classified as a deviation?

  - 5 nautical miles

- 계획된 경로에서 어느 정도의 편차(마일)가 편차로 분류되어야 합니까?

  5해리



- What should the system behavior be when an aircraft’s flight profile is detected as anomalous?

  - This is a team’s design decision. Think like you are in charge of flight safety and need to know the information on a cluttered screen with hundreds of aircraft flying around. How would you want the system to alert you if you were in charge and responsible?

- 항공기의 비행 프로필이 이상으로 감지될 때 시스템 동작은 어떻게 되어야 합니까?

  이것은 팀의 디자인 결정이다. 비행 안전을 책임지고 수백 대의 항공기가 날아다니는 어수선한 화면의 정보를 알아야 한다고 생각하세요. 당신이 책임지고 책임이 있다면 시스템이 당신에게 어떻게 경고하기를 원하십니까?



- What specific data must be recorded in the flight history file (e.g., timestamp, aircraft ID, location)?

  - This is a team’s design decision. What data would you need for training purposes or if an accident happened? What data would you need to simulate a previous flight?

- 비행 이력 파일에 기록해야 하는 특정 데이터(예: 타임스탬프, 항공기 ID, 위치)는 무엇입니까?

  이것은 팀의 디자인 결정이다. 교육 목적으로 또는 사고가 발생한 경우 필요한 데이터는 무엇입니까? 이전 비행을 시뮬레이션하려면 어떤 데이터가 필요합니까?



- What is the recommended file size for a record history file used in playback?

  - Good question. This is part of the design and architecture tradeoff that teams must analyze, work through, and justify decisions.

- 재생에 사용되는 기록 기록 파일의 권장 파일 크기는 얼마입니까?

  좋은 질문입니다. 이는 팀이 분석하고, 작업하고, 결정을 정당화해야 하는 설계 및 아키텍처 절충안의 일부입니다.



- Which map providers must be supported to receive full credit during evaluation?
  - Teams are welcome to use any map data. Think of the user experience, however. Which map data, including its scale and imagery, provides the best experience for the remote user interface.

- 평가 중에 전체 크레딧을 받으려면 어떤 지도 제공자가 지원되어야 합니까?

  팀은 모든 지도 데이터를 사용할 수 있습니다. 하지만 사용자 경험을 생각해 보세요. 스케일과 이미지를 포함한 지도 데이터는 원격 사용자 인터페이스에 가장 적합한 경험을 제공합니다.

  

- If map data fails to load or lags, what is the expected system response? Will resiliency and user error messaging be part of the evaluation?

  - Good question. Yes. Review the quality attributes section of the project plan. This is part of the design and architecture tradeoff that teams must analyze, work through, and justify decisions.

- 맵 데이터가 로드되지 않거나 지연되는 경우 예상되는 시스템 응답은 무엇입니까? 복원력 및 사용자 오류 메시지가 평가의 일부입니까?

  좋은 질문입니다. 네. 프로젝트 계획의 품질 평가 항목 섹션을 검토합니다. 이는 팀이 분석하고, 작업하고, 결정을 정당화해야 하는 설계 및 아키텍처 절충안의 일부입니다.



- Will the presence of partial updates or stale metadata (e.g., outdated altitude or speed) negatively affect the evaluation score?

  - Good question. Stale data is not great for air safety. While this is a desired feature and not a mandatory feature, other teams will receive bonus points for implementing this feature.

- 부분적인 업데이트 또는 오래된 메타데이터(예: 오래된 고도 또는 속도)의 존재가 평가 점수에 부정적인 영향을 미칠까요?

  좋은 질문입니다. 고정 데이터는 항공 안전에 좋지 않습니다. 이것은 필수 기능이 아닌 바람직한 기능이지만, 다른 팀은 이 기능을 구현하면 보너스 포인트를 받게 됩니다.



- How do you expect the number of flights can be displayed at the same time? (maximum flights count on the map)

  - The display should be able to manage all active tracks. The question that seems to be asked is whether some tracks should be filtered.
  - Another way to think about the question is where the team can make the decision based on regional control areas. Selecting those regional control areas as though those are the areas under one’s control may offer a filter option for aircraft entering, within, and exiting and thus limit the number to what has to be displayed for a specific controller for that airspace. Be sure to think about handoff times between airspace with aircraft coming in and out of the airspace selected.

- 항공편 수를 어떻게 동시에 표시할 수 있을까요? (지도상의 최대 비행 횟수)

  디스플레이는 모든 활성 트랙을 관리할 수 있어야 합니다. 질문이 제기되는 것 같은 것은 일부 트랙을 필터링해야 하는지 여부입니다.

  질문에 대해 생각하는 또 다른 방법은 팀이 지역 통제 영역을 기반으로 결정을 내릴 수 있는 곳입니다. 해당 지역 통제 구역을 마치 자신의 통제 하에 있는 구역인 것처럼 선택하면 항공기 진입, 내부 및 출구에 대한 필터 옵션을 제공할 수 있으며 따라서 해당 영공의 특정 컨트롤러에 대해 표시되어야 하는 것으로 수를 제한할 수 있습니다. 선택한 영공을 드나드는 항공기와 함께 영공 간 핸드오프 시간을 반드시 생각하세요.



- What does analytical feature mentioned in response time ?

  - Please clarify the question.

- 응답 시간에 언급된 분석 기능은 무엇입니까?

  질문을 명확히 해 주세요.

  

- Is there any predefined test cases to demonstrate implemented features ?

  - No. The teams will need to show their test cases used during the final demo.

- 구현된 기능을 시연하기 위해 미리 정의된 테스트 사례가 있습니까?

  아니. 팀은 최종 데모 중에 사용된 테스트 케이스를 보여줘야 합니다.



- What duration (in milliseconds) should be considered acceptable as the connection timeout threshold?

  - Good question. This is part of the design and architecture tradeoff that teams must analyze, work through, and justify decisions.

- 연결 시간 초과 임계값으로 허용되는 것으로 간주되어야 하는 기간(밀리초 단위)은 무엇입니까?

  좋은 질문입니다. 이는 팀이 분석하고, 작업하고, 결정을 정당화해야 하는 설계 및 아키텍처 절충안의 일부입니다.

  

- What is the acceptable threshold (in milliseconds or seconds) for system recovery time after a lost connection?

  - Good question. This is part of the design and architecture tradeoff that teams must analyze, work through, and justify decisions.

- 연결 손실 후 시스템 복구 시간에 대한 허용 가능한 임계값(밀리초 또는 초)은 얼마입니까?

  좋은 질문입니다. 이는 팀이 분석하고, 작업하고, 결정을 정당화해야 하는 설계 및 아키텍처 절충안의 일부입니다.



- By what means will the system architecture be evaluated—through design documentation, architectural diagrams, actual code review, or a combination of these?

  - Please refer to the project plan. There are three milestone events. Contact Paulo and Matt for milestone 1 and 2 grading criteria. Solvit will be posting the milestone 3 grading criteria by mid June.

- 설계 문서, 아키텍처 다이어그램, 실제 코드 검토 또는 이들의 조합을 통해 시스템 아키텍처는 어떤 수단으로 평가됩니까?

  프로젝트 계획을 참조하십시오. 세 가지 이정표 이벤트가 있습니다. 마일스톤 1 및 2 등급 기준에 대해서는 Paulo 및 Matt에게 문의하십시오. Solvit은 6월 중순까지 이정표 3 등급 기준을 게시할 예정입니다.



- How many and which types of maps are required to satisfy the evaluation criteria?

  - Refer to question 8 and answer.

- 평가 기준을 충족시키기 위해 몇 개와 어떤 유형의 지도가 필요합니까?

  질문 8을 참조하여 답변합니다. (평가 중에 전체 크레딧을 받으려면 어떤 지도 제공자가 지원되어야 합니까?

  팀은 모든 지도 데이터를 사용할 수 있습니다. 하지만 사용자 경험을 생각해 보세요. 스케일과 이미지를 포함한 지도 데이터는 원격 사용자 인터페이스에 가장 적합한 경험을 제공합니다.)

  

- What qualifies as an error for evaluation purposes? Does this include only crashes and exceptions, or also issues like broken user flows and missing error messages?

  - Yes to all examples provided. Air Safety would dictate that if there is an error - there is an error. Some things coming from the ADSB community or the server QoS are probably out of your control.

- 평가 목적으로 오류로 간주되는 것은 무엇입니까? 여기에는 충돌 및 예외만 포함됩니까, 아니면 깨진 사용자 흐름 및 누락된 오류 메시지와 같은 문제도 포함됩니까?

  제공된 모든 예에 예. 항공 안전은 오류가 있으면 오류가 있다고 지시할 것입니다. ADSB 커뮤니티나 서버 QoS에서 오는 일부 것들은 아마도 당신이 통제할 수 없을 것입니다.



- Is there a defined quantitative performance standard or a stress test scenario that will be used during evaluation to assess system behavior under load?

  - Great question. The details of the final demo are being finalized. The published final demo criteria will answer this question. Anticipate mid June for the grading criteria and final demo guidance to be published.

- 부하 하에서 시스템 동작을 평가하기 위해 평가 중에 사용될 정의된 정량적 성능 표준 또는 스트레스 테스트 시나리오가 있습니까?

  좋은 질문입니다. 최종 데모의 세부 사항이 마무리되고 있습니다. 게시된 최종 데모 기준이 이 질문에 답할 것입니다. 6월 중순에 채점 기준과 최종 데모 지침이 게시될 것으로 예상합니다.





## Part 2

- Page 18 of project description mentions "Lookup aircraft information", may we know does it mean the feature that displays the information such as ICAO on the side bar when we choose an aircraft?
  - When you run the application, two windows open up. One is the main user interface, and one looks like a terminal or command prompt window. When you hook a track, the terminal / command prompt window shows a lot of information about the aircraft, such as aircraft model, aircraft owner, and more. Use this information as the “aircraft information”.

- Among the mandatory features on page 9, there is a track history which should be dropped after 30 seconds. It seems that one is different from the recording feature (dumps to file). Please let us know if our understanding is not correct.
  - The feature is asking the teams to track the duration of time between ADS-B / SBS messages for each track. For example, which tracks have not received a recent message greater than 5 sec, 10 sec, etc. Any track that has not been updated longer than 30 seconds should be removed from the user interface display.

- May I ask is there any specific reason that SolveIt decides the duration of track history as 30 seconds? (page 9 Prj description)
  - 30 seconds was based upon an assumption that there are no longer ADS-B receivers to provide information (e.g., over the ocean) or the aircraft has landed. Maintaining the track on the map display no longer provides useful information. Teams are welcome to conduct analysis and modify the 30 second requirement if the evidence supports their change.

- To limit the amount of work & increase the success rate of this project, we assume that the maximum number of aircrafts is 10,000, what do you think of that decision?
  - Concur. Solvit generally observes between 6000-8000 tracks, so this provides a good margin for any anomalies in high track observations.

- We're not sure what kind of modifications are expected for the "leaders" mentioned in the "Enhancements to User Interface." (page 10)
  - Leaders are the velocity vectors. These are the lines that extend beyond the nose of the aircraft track.

- How many man-days do you expect it would take to add a new map provider?
  - The answer is it depends on several factors, such as experience and library / tool use. Recommend looking at provided code to see how Solvit implemented the existing map data. Recommend the teams plan 1-3 days to complete this requirement. If after a genuine 3 days of effort and your team is still challenged with adding map data, please contact Solvit Inc.
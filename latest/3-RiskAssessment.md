# Risk Assessment

This document identifies technical and non-technical risks assessment. By assessing these risks early, appropriate mitigation strategies can be developed and applied to minimize project delays, quality degradation, and communication issues.

## Risk Evaluation Criteria

Likelihood (L): Probability that the risk will occur

Impact (I): Level of damage if the risk occurs



## Technical Risk Assessment

| ID   | Description | L    | I    | Mitigation Strategy | Link |
| ---- | ----------- | ---- | ---- | ---------- | ---------- |
| TR_1 | System may not be updated normally due to large volume of aircraft data is received by the ADS-B server in a short period of time. |   H   |  H  |   consider Manage sampling rate to adjust the volume of aircraft data.   |   [Exp 1](./experiments/exp01.md) , [Exp 2](./experiments/exp02.md)   |
| TR_2 | We need to apply multi-thread in program, but the VCL framework does not support multi thread. If background threads directly access or modify UI components, it may result in application instability, race conditions, or unexpected crashes. |  M   |  L  |    Separate business logic from UI logic, and run the UI thread and the data processing thread independently.    |    [Exp 7](./experiments/exp07.md)    |
| TR_3 | The Raspberry Pi can fail for various reasons (e.g. crash, out of memory), and it is unclear whether it provides the cause of failure depending on the situation. |  H  |  L   |     Modify the Raspberry Pi to report its status information.     |     [Exp 6](./experiments/exp06.md)     |
| TR_4 | UI, network, and data processing are tightly coupled, making it unclear where to insert the deviation detection logic.            |  H   |  H   |    Separation of UI, network, and data processing components.    |    Planned draw diagrams    |



## Non-technical Risk Assessment

| ID    | Description                                                  | Cause                                                        | L    | I    | Mitigation Strategy                                          |
| ----- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| NTR_1 | Some requirement documents lack clarity, making analysis difficult. Clarification is only possible through assumptions or direct contact with the project sponsor. unclear requirements can lead to rework, misalignment, and missed goals. | Ambiguous documents and vague requirements                   | H    | H    | Clarify ambiguous requirements by maintaining continuous, question-and-answer-based communication with Solvelt throughout the project lifecycle.Seek solutions via regular meetings with mentors and expedite requirement confirmation by suggesting common assumptions. |
| NTR_2 | Communication within the team is limited to English due to diverse nationalities. | Different native languages                                   | H    | H    | Leverage visual collaboration tools such as Miro, along with AI-powered translation tools, to facilitate effective communication across language barriers. |
| NTR_3 | Communication is limited to Solvelt and email, resulting in long delays in receiving responses. | Lack of proper decision-making channels                      | M    | H    | Proactively reach out to mentors and maintain regular contact with Solvelt |
| NTR_4 | LG company PC security tools hinder development and test environment setup. | Network blocks and data transfer restrictions by security software | M    | M    | Use alternative devices (e.g., mobile), request exception handling from IT security team |
| NTR_5 | The project duration is limited to approximately 4 weeks, with additional assignments affecting overall work efforts. | Short project timeline and parallel other tasks(Assignment, Quiz). | H    | H    | Focus on essential features, utilize planning tools and AI assistance for efficiency. |

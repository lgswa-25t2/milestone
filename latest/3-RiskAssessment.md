# Risk Assessment

This document identifies technical and non-technical risks assessment. By assessing these risks early, appropriate mitigation strategies can be developed and applied to minimize project delays, quality degradation, and communication issues.

## Risk Evaluation Criteria

Likelihood (L): Probability that the risk will occur (1 = Very Low, 5 = Very High)

Impact (I): Level of damage if the risk occurs (1 = Negligible, 5 = Critical)

Risk Level = L × I

- High: 20–25
- Medium: 12–19
- Low: 1–11



## Technical Risk Assessment

### Identification

| ID   | Refrence    | Description | L    | I    | Risk Level |
| ---- | ----------- | ----------- | ---- | ---- | ---------- |
| TR_1 | IFTA_QA_001_01 | System may not be updated normally due to large volume of aircraft data is received by the ADS-B server in a short period of time. |   4   |  5   |   20     |
| TR_2 | IFTA_QA_002 | We need to apply multi-thread in program, but the VCL framework is not thread-safe. If background threads directly access or modify UI components, it may result in application instability, race conditions, or unexpected crashes. |  3   |  1  |    3    |
| TR_3 | IFTA_QA_002 | The Raspberry Pi can fail for various reasons (e.g. crash, out of memory), and it is unclear whether it provides the cause of failure depending on the situation. |  4   |  2   |     8       |
| TR_4 | IFTA_QA_003 | UI, network, and data processing are tightly coupled, making it unclear where to insert the deviation detection logic.            |  4   |  4   |    16     |

### Prioritization, Mitigation, Experiments

| ID   | Description | Risk Level | Mitigation Strategy | Linked Experiments |
| ---- | ----------- | ---------- | ------------------- | ------------------ |
| TR_1 | System may not be updated normally due to large volume of aircraft data is received by the ADS-B server in a short period of time. |   High    | consider Manage sampling rate to adjust the volume of aircraft data.                    | [Exp 1](./experiments/exp01.md) , [Exp 2](./experiments/exp02.md) |
| TR_2 | We need to apply multi-thread in program, but the VCL framework is not thread-safe. If background threads directly access or modify UI components, it may result in application instability, race conditions, or unexpected crashes. <!--We need to apply multi-thread in program, but VCL does not support multi-thread.                 Although the use of multithreading is considered to enhance performance, the VCL is not thread-safe. --> |   Low     | Separate business logic from UI logic, and run the UI thread and the data processing thread independently.                    | [Exp 7](./experiments/exp07.md) |
| TR_3 | Raspberry Pi can fail for various reasons, and it is unclear whether it provides the cause of failure depending on the situation.  |   Low     | Modify the Raspberry Pi to report its status information.| [Exp 6](./experiments/exp06.md) |
| TR_4 | UI, network, and data processing are tightly coupled, making it unclear where to insert the deviation detection logic.            |    Mid     | Separation of UI, network, and data processing components.                     | Planned draw diagrams |


## Non-technical Risk Assessment

### Identification

| ID     | Name                                              | Description                                                  | Cause                                                        |
| ------ | ------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| NTR_01 | Unclear Requirements                              | Some requirement documents lack clarity, making analysis difficult. Clarification is only possible through assumptions or direct contact with the project sponsor. unclear requirements can lead to rework, misalignment, and missed goals. | Ambiguous documents and vague requirements                   |
| NTR_02 | Language Barrier                                  | Communication within the team is limited to English due to diverse nationalities. | Different native languages                                   |
| NTR_03 | Delayed Decision-Making                           | Communication is limited to Solvelt and email, resulting in long delays in receiving responses. | Lack of proper decision-making channels                      |
| NTR_04 | Development Restrictions due to PC Security Tools | LG company PC security tools hinder development and test environment setup. | Network blocks and data transfer restrictions by security software |
| NTR_05 | Tight Schedule                                    | The project duration is limited to approximately 4 weeks, with additional assignments affecting overall work efforts. | Short project timeline and parallel other tasks(Assignment, Quiz). |

### Prioritization and Mitigation

| ID    | Name                    | L    | I    | Risk Level  | Mitigation Strategy                                          |
| ----- | ----------------------- | ---- | ---- | ----------- | ------------------------------------------------------------ |
| NTR_1 | Unclear Requirements    | 4    | 5    | High (20)   | Clarify ambiguous requirements by maintaining continuous, question-and-answer-based communication with Solvelt throughout the project lifecycle.Seek solutions via regular meetings with mentors and expedite requirement confirmation by suggesting common assumptions. |
| NTR_2 | Language Barrier        | 4    | 5    | High (20)   | Leverage visual collaboration tools such as Miro, along with AI-powered translation tools, to facilitate effective communication across language barriers. |
| NTR_3 | Delayed Decision-Making | 3    | 5    | Medium (15) | Proactively reach out to mentors and maintain regular contact with Solvelt |
| NTR_4 | Security Restrictions   | 3    | 3    | Low (9)     | Use alternative devices (e.g., mobile), request exception handling from IT security team |
| NTR_5 | Tight Schedule          | 4    | 4    | Medium (16) | Focus on essential features, utilize planning tools and AI assistance for efficiency. |

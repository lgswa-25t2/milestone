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

TODO - QA scenario 에 대한 risk 를 작성해야함

Ex ) 퍼포먼스 항목 -> 제한 시간안에 성공하지 못할경우 -> Probability / Impact 를 H/M/L 로 평가

그 후 해당 위험을 위한 experiment 를 계획하고 plan 업데이트

### Identification

| ID   | Name                                       | Description                                                  | Cause                                           |
| ---- | ------------------------------------------ | ------------------------------------------------------------ | ----------------------------------------------- |
| TR_1 | Lack of Development Environment Experience | Team members have no prior experience with Borland C++, which is expected to cause significant difficulty in development, debugging, and build processes. | Use of uncommon IDE and non-standard syntax.    |
| TR_2 | Difficulty in Code Analysis                | The legacy code is outdated, poorly documented, and lacks comments, making it difficult to analyze. | Legacy coding style, no documentation.          |
| TR_3 | Tool DependencyTool Dependency             | Development is constrained to MS Windows due to specific tool dependencies. | Development tool is tightly coupled with the OS |

### Prioritization and Mitigation

| ID   | Name                                       | L    | I    | Risk Level  | Mitigation Strategy                                          |
| ---- | ------------------------------------------ | ---- | ---- | ----------- | ------------------------------------------------------------ |
| TR_1 | Lack of Development Environment Experience | 5    | 5    | High (25)   | Careful review of installation guide documentation,  Conduct initial collaborative build practice sessions, Engage in structured tutorial-based learning. |
| TR_2 | Difficulty in Code Analysis                | 4    | 5    | High (20)   | Conduct focused code analysis workshops to review legacy code, identify key modules. |
| TR_3 | Tool Dependency                            | 3    | 5    | Medium (15) | Use VMware to install a Windows VM or configure dual-boot to run Borland tools in a compatible OS. |



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

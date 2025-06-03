# Architectural Drivers

This document outlines all the factors that affect system architecture, defining key QA elements and providing a basis for design decisions.

## Stakeholders

| Role          | Name               | Concerns          |
| ------------- | ------------------ | ----------------- |
| Product Owner | Solvit Inc.        | Features          |
| Dev team      | Team #2 Challenger | Rapid development |

## Requirements

Please refer to [Requirements](./1-Requirements.md).

## Constraints

- The original code is written in C++.
- Since this is a Windows application using VCL (Visual Component Library), the IDE is set to RAD Studio.
- DB must use Google BigQuery.

## Quality Attributes

In addition to the key QA elements in description, additional items were derived through the QA scoreboard.

#### Score board

Business importance : Indicates how important quality attributes are to a successful system and to meeting requirements.

Risk : This shows how dangerous it can be when quality attributes are not met.

| Quality Attribute   | Business Importance | Risk | Score | Comments                                                     |
| ------------------- | :-----------------: | :--: | :---: | ------------------------------------------------------------ |
| ***Performance***   |         10          |  9   |  90   | - Quality req. #1 in description<br />- quick response       |
| ***Resiliency***    |         10          |  10  |  100  | - Quality req. #2 in description<br />- connection lost      |
| Reliability         |          8          |  3   |  24   | It is difficult for non-artificial failures to occur.        |
| ***Extensibility*** |         10          |  9   |  90   | - Quality req. #3 in description<br />- add new features     |
| <u>Usability</u>    |          9          |  7   |  63   | Make popup box when error is occuring.                       |
| Scalability         |          7          |  5   |  35   | There is no requirement that performance remain constant as the number of aircraft increases. |
| **Maintainability** |          8          |  7   |  56   | - Quality req. #5 in description                             |
| Testability         |          3          |  2   |   6   | Out of scope                                                 |
| **Modifiability**   |          8          |  8   |  64   | - Quality req. #4 in description<br />- Change map provider  |
| Security            |          8          |  2   |  16   | Out of scope                                                 |

- ***Performance***, ***Resiliency***, ***Extensibility*** - Top quality attributes determined by project sponsor
- **Modifiability**, **Maintainability** - Derived from short brief of quality requirements in project description
- <u>Usability</u> : additional derived from QA score board



### Performance

#### Scenario

(briet summary of scenario)

- Stimulus : asdf
- Stimulus source : asdf
- Artifact : asdf
- Environment : asdf
- Response : asdf
- Response measure : asdf

#### Tactics

blahblah

#### Patterns

blahblah

#### Related Design Decisions

link to design decisions documents


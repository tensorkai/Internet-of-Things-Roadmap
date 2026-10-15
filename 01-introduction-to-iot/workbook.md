# Design workbook

[← Module home](README.md) · [Worked example](examples/room-monitor-design.md) · [Assessment](assessment.md)

Copy this file into your own project notes. Replace each blank with a decision, an assumption, or an explicitly unresolved question. Never paste real credentials.

**Project:** …  
**Author / date / revision:** …  
**Evidence status:** design only / simulated / measured (identify which applies to each result)

## A · User and component map

**Use case:** For …, measure … so they can decide …  
**Outside scope:** …  
**Expected physical quantity and unit:** …

| Role | Proposed component or service | Required / optional / combined | Why |
| --- | --- | --- | --- |
| Sensor | … | … | … |
| Signal conditioning / conversion | … | … | … |
| Controller and firmware | … | … | … |
| Network equipment | … | … | … |
| Gateway | … | … | … |
| Backend and storage | … | … | … |
| Application | … | … | … |
| Actuator or local indicator | … | … | … |

## B · Message contract

**Example telemetry message:** …

| Field | Type / unit | Meaning | Invalid or missing behavior |
| --- | --- | --- | --- |
| … | … | … | … |

- Reading identity and duplicate policy: …
- Measurement time versus reception time: …
- Behavior when the device clock is uncertain: …
- Freshness threshold and display refresh interval: …
- Sensor-fault behavior: …
- Event versus configuration example: …
- Optional command ID, expiry, permission, and repeat behavior: …
- What reported state proves—and what it does not: …

## C · Architectures and failures

Insert two diagrams or link to your drawings. Label direction, content, frequency, trust boundaries, and failed-link behavior.

**Local responsibilities:** …  
**Remote responsibilities:** …  
**Queue capacity / overflow / replay rate:** …  
**What survives restart:** …

| Failure | Device behavior | Service / application behavior | Recovery |
| --- | --- | --- | --- |
| Sensor fault | … | … | … |
| Network outage | … | … | … |
| Gateway failure, if present | … | … | … |
| Backend unavailable | … | … | … |
| Device power cycle | … | … | … |

## D · Requirements, budgets, and decision

| ID | Behavior and numerical limit | Conditions / assumptions | Verification method | Status |
| --- | --- | --- | --- | --- |
| R1 | … | … | … | Proposed |
| R2 | … | … | … | Proposed |
| R3 | … | … | … | Proposed |
| R4 | … | … | … | Proposed |
| R5 | … | … | … | Proposed |

**Accuracy target and reference method:** …  
**Availability target and observation period:** …  
**Power source and battery-life assumptions:** …  
**Installation-cost ceiling:** …  
**Retention and cleanup schedule:** …  
**Support lifetime and owner:** …

**Payload calculation:** interval … s; bytes/reading …; readings/day …; payload/day …; retained payload …  
**Excluded overhead:** …

| Requirement or preference | Architecture A | Architecture B |
| --- | --- | --- |
| … | … | … |

**Choice and reason:** …  
**Tradeoff accepted:** …  
**What would change the choice:** …

## E · Trust, privacy, and lifecycle

| Role / identity | Allowed actions | Denied actions |
| --- | --- | --- |
| Device | … | … |
| Viewer | … | … |
| Administrator | … | … |

| Risk / exposed interface | Consequence | Proposed control | Future evidence | Residual uncertainty |
| --- | --- | --- | --- | --- |
| … | … | … | … | … |
| … | … | … | … | … |
| … | … | … | … | … |

| Data collected | Purpose | Access | Retention / deletion |
| --- | --- | --- | --- |
| … | … | … | … |

**Provisioning:** …  
**Updates and recovery:** …  
**Ownership transfer / retirement:** …

## F · Initial bill of materials and operating costs

| Item / service | Quantity | Function | Selection constraints | Cost estimate and source/date |
| --- | --- | --- | --- | --- |
| Controller board | … | … | … | Unknown until selected |
| Sensor | … | … | … | Unknown until selected |
| Power and cables | … | … | … | Unknown until selected |
| Indicator / passive components | … | … | … | Unknown until selected |
| Enclosure / mounting | … | … | … | Unknown until selected |
| Gateway, if needed | … | … | … | Unknown until selected |
| Backend / network service | … | … | … | Unknown until selected |

**One-time costs:** …  
**Recurring connectivity/hosting costs:** …  
**Replacement and maintenance work:** …

## G · Tabletop results and review

| Scenario | Expected outcome from the design | Reasoning / calculation | Missing decision or revision |
| --- | --- | --- | --- |
| 15-minute outage | … | … | … |
| Delayed / duplicate reading | … | … | … |
| Sensor failure | … | … | … |
| Repeated command | … | … | … |
| Device restart | … | … | … |
| Unauthorized change | … | … | … |

These are tabletop predictions. Log physical experiments separately with equipment, method, expected result, actual result, and pass/fail status.

**Assessment score:** …  
**Reviewer questions:** …  
**Corrections made:** …  
**Next experiment:** …

[Return to the design studio →](lessons/06-design-studio.md)

# Assessment · Explain your design

[← Module home](README.md) · [Workbook](workbook.md) · [Worked example](examples/room-monitor-design.md)

Answer in your own words before expanding the answer guide. This assessment checks introductory reasoning, not production readiness.

## Part 1 · Ten questions

1. In the room monitor, distinguish sensor, controller, backend, and application.
2. Can an IoT monitoring design omit an actuator? Explain.
3. A device reaches a backend through a Wi-Fi access point and router. Must it also have an application gateway?
4. Classify “temperature 27 °C,” “sensor disconnected,” “set LED on,” and “sample every 60 s.”
5. The broker acknowledges a command. What has not yet been proved?
6. A sample was measured at 12:00 and received at 12:10. Which time describes its freshness?
7. With exactly 90 samples during an outage and a 60-record drop-oldest queue initially empty, how many are retained and dropped?
8. At one 120-byte reading every 60 seconds, how much application payload is generated per day?
9. What is missing from “the dashboard should update quickly”?
10. Why might separate device credentials help when one device is compromised?

<details>
<summary><strong>Answer guide</strong> — check after attempting all ten questions</summary>

1. The sensor measures the physical quantity; the controller runs local logic; the backend receives/processes/stores data; the application presents it to the user.
2. Yes. A monitoring-only design can help a person decide without producing an automated physical action.
3. No. Network forwarding and application gateway responsibilities differ. A gateway is a design choice based on the device/service interfaces and local needs.
4. Telemetry, event, command, and configuration.
5. The device's authorization, execution, output state, and the physical effect have not necessarily been established by a broker acknowledgement.
6. Measurement time, if trustworthy. Reception time says when the service received it. If the device clock is uncertain, freshness is uncertain too.
7. Retain 60; drop the oldest 30, under the stated simplified assumptions.
8. 86,400 / 60 = 1,440 readings; 1,440 × 120 = **172,800 bytes/day**, excluding overhead.
9. The behavior being timed, a numerical limit, test conditions, and a verification method.
10. The compromised identity can be revoked without necessarily replacing every other device's credential. Authorization and secure provisioning are still required.

</details>

**Self-check target:** at least 8 of 10 correct, then revise every incorrect answer. This is a teaching threshold chosen for this module, not an external certification.

## Part 2 · Design review

Score each row from 0 to 2: **0 = missing; 1 = present but ambiguous; 2 = explicit and consistent.**

| Criterion | A score of 2 requires |
| --- | --- |
| User and component map | A clear decision, relevant physical quantity, and justified optional/combined roles |
| Architecture | Two alternatives with labeled flows, trust boundaries, and a reasoned choice |
| Message contract | Units, identities, timing, validity, duplicates, and command/state distinctions |
| Requirements and budgets | Five measurable requirements with verification methods, plus explicit resource assumptions |
| Failure behavior | Sensor, network, service, queue-overflow, and restart outcomes |
| Trust and lifecycle | Risks, permissions, data inventory, materials/cost considerations, support, and retirement |

**Completion target:** at least 10 of 12, with no missing criterion. Rework the design until another reader can explain it without inventing behavior.

A high score does not establish electrical safety, measured accuracy, secure implementation, or long-term reliability. Keep proposed, simulated, and measured evidence separate.

## Part 3 · Explain one change

Your user now wants five rooms instead of one. Write a short paragraph explaining what you would revisit in identities, message volume, device records, architecture, and maintenance. A gateway is a possibility, not an automatic requirement.

<details>
<summary>Example reasoning</summary>

Give each device a distinct identity and enforce per-device permissions. Under unchanged sampling assumptions, payload volume is five times the one-device estimate. Show separate last-seen and data-quality states for each room. Reassess network coverage, service capacity, installation effort, and support ownership. Compare a gateway only if local interfaces, coordination, or buffering needs justify it.

</details>

## Continue the roadmap

Keep the workbook and corrections as the first entry in your project evidence. Next, learn how the physical circuit supports the design in [Electronics Fundamentals →](../02-electronics-fundamentals/README.md). Study [Mathematical Foundations](../03-mathematical-foundations/README.md) alongside the calculations.

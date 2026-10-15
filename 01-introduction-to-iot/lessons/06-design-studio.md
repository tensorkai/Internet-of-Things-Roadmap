# 06 · Design studio

[← Trust and lifecycle](05-security-privacy-and-lifecycle.md) · **Lesson 6 of 6** · [Final assessment →](../assessment.md)

> **Learning goal:** assemble a design that another learner can inspect, question, and eventually implement.

## Your brief

Design a room-temperature monitor for one room. It must show recent measurements and data age on a dashboard, and retain useful local behavior during a network outage.

Include a local status indicator. Add a remotely controlled LED only if you want a command path; it is optional. Use a direct-to-backend or gateway architecture and explain your choice. You are designing the system, not purchasing parts or proving a physical implementation.

Start by copying the [workbook](../workbook.md) into your project notes. Read the [worked example](../examples/room-monitor-design.md) after writing your first attempt.

## Step 1 · Define the user and the decision

Write a one-sentence use case. Name what the user can reasonably infer from the measurements.

For example, “see temperature trends and investigate persistent warmth” is supportable as a goal. “Determine whether a room is healthy” is too broad for one temperature sensor.

Identify one thing the system will not claim to measure. This prevents the dashboard from implying knowledge the sensor does not provide.

## Step 2 · Draw the complete path

Include sensor, conditioning/conversion, controller, network equipment, backend, storage, and application. Mark combined or omitted roles. Add an optional gateway and actuator only when justified.

For every arrow, write:

- data or command carried;
- direction and expected frequency;
- identity/permission check at a trust boundary;
- behavior if the connection fails.

Place a boundary around device-local work. Then disconnect the upstream path on paper: identify what still works, what becomes unavailable, and what the user sees.

## Step 3 · Make the contracts inspectable

Create one telemetry example, one invalid-reading example, and—if applicable—one command example. Define units, time semantics, reading identity, and how duplicate readings are handled.

For a command, distinguish acceptance, reported output, and physical observation. Specify expiry and repeated-command behavior. Do not label “message sent” as “action completed.”

## Step 4 · Choose measurable targets

Write at least five requirements. Include sampling, display latency, freshness, an outage behavior, and retention. Each requirement needs a method that could later decide pass or fail.

Then record design constraints for accuracy, power/battery, availability, installation cost, and support lifetime. Mark unmeasured properties explicitly. Estimate payload volume with units and list excluded overhead.

Requirements and later verification should remain traceable: each test should name the requirement it addresses ([National Aeronautics and Space Administration, 2016](../references.md#ref-systems), Chapter 5).

## Step 5 · Conduct a tabletop failure exercise

This is a reasoning exercise, not a hardware test. Use a sample interval of 10 s, a stale threshold greater than 30 s, a queue of 60 records, and drop-oldest overflow for this walkthrough.

Assume an empty queue at the start of each independent scenario.

| Scenario | Your task |
| --- | --- |
| Network is unavailable for 15 minutes | Calculate retained and dropped readings under the simplified schedule |
| An old reading arrives after a recent reading | Explain storage and current-display behavior |
| The sensor reports a fault | Explain why the previous good value must not appear as a fresh sample |
| A command is submitted twice | State what happens for set-state versus toggle behavior |
| The device restarts | Explain boot ID, sequence reset, clock uncertainty, and queue persistence |
| The viewer requests a configuration change | Name the permission decision and expected response |

Write down your answer before opening the worked design. If an outcome is unspecified, improve the contract rather than guessing what firmware will do.

## Step 6 · Review costs, risks, and ownership

Create an initial bill of materials by **role**, even if you have not selected a specific product. Include power, cables, enclosure, mounting, and any gateway. Separate one-time costs from connectivity, hosting, replacement, and maintenance effort.

List three risks with proposed controls and future evidence. Assign an owner to updates, recovery, and retirement. These planning activities connect security decisions to the product's lifecycle ([Fagan et al., 2026](../references.md#ref-lifecycle)).

## What to submit

| Artifact | It should answer |
| --- | --- |
| Use-case statement and diagram | What is the system for, and how do its parts interact? |
| Message contract | What do its messages mean, including invalid or repeated ones? |
| Requirements and verification plan | What counts as meeting the design goals? |
| Architecture comparison | Why is the chosen design suitable here? |
| Failure exercise | What changes when sensing, networking, or services fail? |
| Risks, data inventory, and bill of materials | What must be protected, supported, and paid for? |

## Before moving on

You are ready when another learner can follow your diagram, identify assumptions, and explain how a requirement will be checked. A polished drawing alone is not enough.

Use the [assessment and rubric](../assessment.md). Keep unfinished implementation questions for [Electronics Fundamentals](../../02-electronics-fundamentals/README.md) and later modules.

[Compare with the worked design →](../examples/room-monitor-design.md) · [Take the assessment →](../assessment.md)

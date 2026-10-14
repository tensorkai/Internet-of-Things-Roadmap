# Testing and Troubleshooting

[Back to roadmap](../README.md)

## Prerequisites

Start with 04–06; extend coverage as each system layer is added.

## Topics to learn

- [ ] Translate requirements into a test matrix with setup, expected result, acceptance threshold, measured result, and retained evidence.
- [ ] Test pure firmware logic on a host: conversion, parsing, state transitions, timing rollover, bounds, queues, and persistent configuration handling.
- [ ] Use static analysis, compiler warnings, sanitizers where supported, fuzzing of parsers, and reproducible automated builds.
- [ ] Create hardware-in-loop tests for GPIO, bus timing, sensor behavior, boot/recovery, and real actuator feedback.
- [ ] Test protocol contracts and full device-to-dashboard flows, including commands and authorization boundaries.
- [ ] Inject missing sensors, invalid values, network outages, DNS failures, broker restarts, slow consumers, expired credentials, power interruptions, and full storage.
- [ ] Measure timing jitter, worst observed latency, RAM/stack high-water marks, CPU use, bandwidth, packet loss, and current draw. Observed maxima are not proofs of worst-case bounds.
- [ ] Run soak/endurance tests to reveal leaks, thermal issues, reconnect loops, flash wear patterns, and clock drift. Record duration and operating conditions.
- [ ] Use debugger breakpoints, serial logs, logic analyzers, oscilloscopes, packet captures, and correlation IDs to isolate the layer at fault.
- [ ] Automate regression tests and retain firmware version, hardware revision, dependency versions, and raw results. Separate simulated, bench, and field evidence.

## Hands-on work

1. Write and execute a failure matrix against your integrated prototype.
2. Capture one hardware trace and one network trace and use them to explain a failure.
3. Run an initial 24-hour soak test, then choose a longer test duration based on requirements and failure risks; record memory, resets, and delivery statistics.
4. Introduce a regression in a safe test branch and confirm the relevant automated test catches it.

## Completion evidence

- [ ] Provide reproducible test commands and a report showing pass, fail, and untested cases.
- [ ] Link each important requirement to evidence; document deviations instead of silently weakening thresholds.
- [ ] Demonstrate recovery paths as well as normal operation.

## Primary reference

[Zephyr Twister](https://docs.zephyrproject.org/latest/develop/twister/index.html) is one example of an embedded test runner; choose tooling appropriate to your stack.


# Projects and Assessment

[Back to roadmap](../README.md)

These projects turn the topic checklists into evidence. Progress by demonstrated competence rather than a fixed weekly schedule. The values below are starting targets for a small learning prototype; choose and justify different targets before testing if your use case requires them.

## Working setup

Use one documented microcontroller board, one compatible sensor, an LED/button, a breadboard, appropriate low-voltage power, and access to a multimeter. Add a logic analyzer, gateway computer, or other equipment when the project needs it. Reuse compatible equipment you already own. Verify board voltage, pinout, SDK support, and sensor interface before wiring or purchasing.

A simulator can support language, protocol, backend, and failure exercises. Label simulated evidence clearly. Real electrical behavior, current draw, radio coverage, and physical sensor accuracy require hardware measurements.

Keep a project record containing source, dependency versions, setup instructions, wiring/schematics, a bill of materials, requirements, test results, and limitations. Never commit actual credentials.

## Milestone 1: Local sensing

**Preparation:** categories 01–06 and sensing foundations from 16.

Build a room monitor, calibrated plant monitor, or door event logger. Begin with a nonblocking LED and button exercise, then add the sensor. Convert readings into units and report quality/status separately from the value.

- [ ] Sample on a documented schedule without blocking button handling or diagnostics.
- [ ] Explain calibration, expected error, and selected filtering delay.
- [ ] Remove the sensor and demonstrate an explicit fault instead of a plausible-looking stale value.
- [ ] Restart the board and confirm valid configuration and a known initial state.
- [ ] Record a peripheral transaction and explain it from the datasheet.

**Deliver:** firmware, wiring diagram, sensor conversion tests, recorded measurements, and a fault demonstration.

## Milestone 2: Connected device

**Preparation:** categories 07–08 plus identity and transport controls from 11.

Publish versioned telemetry to a local test broker or API. Add a low-voltage LED controller with explicit set-state commands and reported state. Keep command acceptance separate from execution.

- [ ] Use a unique test-device credential with permissions limited to that device.
- [ ] Validate the server identity and reject invalid credentials/certificates in the chosen secure transport setup.
- [ ] Disconnect the network for 10 minutes; keep local sensing/control responsive.
- [ ] Bound the backlog and replay rate, and document what happens when buffering fills.
- [ ] Repeat a command ID, send an expired command, and restart during command processing; show the specified result.
- [ ] Verify last-seen/offline reporting and recovery after a broker restart.

**Deliver:** packet/log evidence, topic or API contract, identity setup, queue limits, and reconnection results.

## Milestone 3: End-to-end application

**Preparation:** categories 09–12, as appropriate to the architecture.

Persist measurements and build a dashboard showing current state, history, units, time range, data quality, and offline status. Add a threshold alert with hysteresis and a recovery event.

- [ ] Replaying the same event does not create an unintended duplicate record.
- [ ] Late and missing samples remain distinguishable from live normal measurements.
- [ ] A user cannot access devices belonging to another test user/group.
- [ ] Alerts open and clear correctly without repeating on every sample.
- [ ] Restore a backup into a clean instance and compare its contents.
- [ ] Measure acquisition-to-storage and acquisition-to-display latency against declared limits.

**Deliver:** service/application source, data model, screenshots, access-control tests, restore evidence, and latency results.

## Milestone 4: Reliable fleet capstone

**Preparation:** core categories 01–13 plus 15–17. Complete optional specialization work when the chosen capstone needs it.

Choose a multi-room sensor network, greenhouse monitoring/control simulator, equipment condition monitor, or fleet-management prototype. Use at least three distinct device identities to exercise fleet behavior. Record which devices are physical and which are simulated; hardware conclusions must come from physical measurements.

Define acceptance limits before implementation. A useful initial test profile is a 10-minute network outage, a 24-hour soak run, a broker restart, a device power cycle, malformed telemetry, and an invalid update attempt. Extend duration and scenarios based on risk; passing this profile is not proof of production readiness.

- [ ] Explain the problem, users, architecture, trust boundaries, and measurable requirements.
- [ ] Integrate authenticated telemetry, useful history, alerts, and bounded commands where applicable.
- [ ] Preserve specified local behavior during upstream outages.
- [ ] Provision, rotate, revoke, and retire one identity without disrupting the other devices.
- [ ] Demonstrate a valid firmware update, rejection of an invalid image, and supported rollback/recovery.
- [ ] Measure memory, latency, power, message volume, and data-loss/duplication behavior.
- [ ] Execute the failure matrix below and retain raw results.
- [ ] Produce an operations runbook, cost estimate, release manifest, support plan, and known-limitations list.

## Failure-test matrix

| Injected condition | Required observation |
| --- | --- |
| Sensor removed or invalid | Data is marked invalid; actuator behavior follows the defined policy |
| Network unavailable | Local work continues; queue capacity and retry rate remain bounded |
| Broker/API restart | Device reconnects without manual reset or uncontrolled replay |
| Duplicate/reordered message | Stored and physical outcomes follow the documented event/command contract |
| Stale command | Device rejects or expires it according to policy |
| Power loss during state write | Device recovers a valid configuration |
| Power loss during update | Supported recovery path preserves a bootable system |
| Unauthorized/revoked identity | Access is denied and diagnosis is possible without exposing secrets |
| Incorrect certificate | Connection is rejected; recovery does not disable validation |
| Full queue or disk | Declared retention/drop/rejection policy is enforced and visible |
| Slow subscriber/backend | Backpressure does not exhaust device or gateway memory |
| Reset or incorrect wall clock | Timestamps and command validity follow an explicit recovery policy |
| Long-running operation | Resets, resource growth, delivery gaps, and power behavior are recorded |

Test on your own isolated equipment, simulator, or authorized test deployment. For hardware-specific failures, write down the exact injection method and recovery steps before performing the test.

## Evidence template

For each test record:

1. Requirement and test identifier.
2. Source revision, firmware, hardware revision, dependency versions, and configuration.
3. Equipment and setup, including whether the result is simulated or measured.
4. Steps and input/failure conditions.
5. Expected result and numerical acceptance limits where relevant.
6. Actual result, raw logs/traces/measurements, and pass/fail status.
7. Defects, fixes, retest results, and remaining limitations.

## Completion standard

A milestone is complete when the evidence demonstrates its requirements and someone else can reproduce the setup. A dashboard screenshot alone does not prove reliability or security. Mark unsupported or untested features explicitly, resolve failures against the agreed requirements, and retain the results as portfolio material. The core learning path ends with an assessed fleet capstone; specialization adds deeper expertise afterward.

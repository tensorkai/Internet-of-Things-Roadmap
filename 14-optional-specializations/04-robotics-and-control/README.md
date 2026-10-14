# Robotics and Control

[Back to specializations](../README.md) · [Main roadmap](../../README.md)

## Prerequisites

Category 16, firmware timing, electronics, and power engineering; add calculus and linear algebra as needed.

## Topics to learn

- [ ] Learn coordinate frames, kinematics, encoder feedback, sensor fusion, and actuator dynamics.
- [ ] Drive small motors through suitable drivers and account for stall current, supply transients, mechanical limits, and feedback.
- [ ] Study discrete-time feedback, PID, delay, jitter, filtering, saturation, anti-windup, and stability.
- [ ] Separate local control loops from network commands; define command limits, deadlines, and loss-of-command behavior.
- [ ] Implement explicit operating states, interlocks, manual override, startup checks, and a physical stop mechanism appropriate to the training platform.
- [ ] Evaluate repeatability, positioning error, overshoot, settling time, and response to disturbances.

## Project

Use a simulated plant first, then an appropriately guarded low-energy motor or servo setup. Test bounded commands, feedback loss, and communication timeout.

## Completion evidence

Deliver control diagrams, timing traces, measured response plots, limits, and fault behavior. Document what remains unverified before any larger mechanical system.


# Sensing, Signal Processing, and Control

[Back to roadmap](../README.md)

## Prerequisites

Categories 02, 03, 04, and 06.

## Topics to learn

- [ ] Select sensors by range, accuracy, precision, resolution, response time, drift, cross-sensitivity, interface, placement, and environment.
- [ ] Study analog conditioning, input protection, reference stability, amplification, filtering, ADC quantization, and calibration.
- [ ] Choose sampling from signal bandwidth; understand aliasing and the role of analog filtering before sampling. A digital filter cannot recover information already aliased.
- [ ] Preserve raw data while evaluating moving averages, median filters, exponential smoothing, and filter delay. Use frequency analysis when the application requires it.
- [ ] Represent missing, stale, saturated, out-of-range, and implausible readings explicitly. Track units, calibration version, and quality metadata.
- [ ] Calibrate against an appropriate reference, estimate uncertainty, document conditions, and plan recalibration as sensors age or environments change.
- [ ] Implement threshold rules with hysteresis and debounce. Distinguish monitoring from control and open-loop from closed-loop behavior.
- [ ] Study feedback, sample period, delay, stability, saturation, and introductory PID control. Add anti-windup and rate/output limits where appropriate.
- [ ] Define startup, shutdown, manual override, interlocks, communication-loss behavior, and sensor-failure behavior for actuators. Use a simulator or benign low-voltage plant during learning.

## Hands-on work

1. Calibrate a sensor at several points and report residual error and repeatability.
2. Compare raw and filtered recordings containing a step, noise, and a missing-data interval.
3. Build a hysteresis controller and simulate sensor failure, delayed readings, and a command timeout.
4. For control specialization, tune a simulated feedback loop and measure overshoot, settling time, and saturation behavior.

## Completion evidence

- [ ] Provide calibration data, sample-rate justification, filter comparison plots, and a quality-state definition.
- [ ] Demonstrate predictable control behavior during restart, invalid measurements, and loss of connectivity.


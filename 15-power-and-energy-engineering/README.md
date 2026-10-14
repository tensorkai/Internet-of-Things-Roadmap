# Power and Energy Engineering

[Back to roadmap](../README.md)

## Prerequisites

Categories 02, 03, and 06; repeat measurements after networking in 07–08.

## Topics to learn

- [ ] Distinguish power from energy and peak from average current. Inventory MCU, radio, sensors, regulators, indicators, and leakage paths.
- [ ] Build a mode-based budget using current, voltage, duration, and frequency for sleep, sensing, processing, connection, and transmission.
- [ ] Understand usable battery capacity, discharge conditions, temperature, aging, self-discharge, protection, and cutoff voltage. Use manufacturer-approved charging and protection appropriate to the chemistry.
- [ ] Compare linear and switching regulators using efficiency, quiescent current, noise, transient response, and dropout/headroom.
- [ ] Study radio startup/association cost, batching, sample/transmit intervals, retries, sensor warm-up time, and duty cycling.
- [ ] Use MCU sleep modes, wake sources, peripheral gating, and retained state. Account for development-board LEDs, USB interfaces, and regulators that may dominate sleep current.
- [ ] Measure current waveforms with suitable instruments; consider meter burden voltage and whether the instrument captures short peaks.
- [ ] Test brownout during transmission, startup surge, recovery after power loss, and data integrity. Compare estimates to measurements before choosing a battery size.
- [ ] For advanced work, assess energy harvesting, seasonal energy availability, storage losses, and operation under energy shortage.

## Hands-on work

1. Make a state-by-state current table and calculate average current: sum(current × time) divided by total time.
2. Estimate runtime using usable capacity divided by average current only when the voltage/conversion assumptions fit; otherwise calculate on an energy basis.
3. Measure sleep and transmission behavior, change one duty-cycle setting, and report the impact on energy and data freshness.
4. Demonstrate stable operation at the expected low-supply condition using appropriate bench equipment.

## Completion evidence

- [ ] Submit a measured energy budget with uncertainty, runtime assumptions, and peak-current margin.
- [ ] Explain the gap between estimated and observed consumption and identify the dominant loads.

